# A Brief comparison of MongoDB with traditional RDBMS

|  RBMS  |           MongoDB             |
|--------|-------------------------------|
|Database|Database                       |
|Table   |Collection                     |
|Row     |Document                       |
|Index   |Index                          |
|JOIN    |Embedded Document or Reference |

# DataBases in MongoDB

#### In MongoDB, databases hold collections of documents.

To select a database to use, in the mongo shell, issue the use <db> statement, as in the following example:

`use dbName`

If a database does not exist, MongoDB creates the database when you first store data for that database. As such, you can switch to a non-existent database and perform the following operation in the mongo shell:

```
use myNewDB

db.myNewCollection.insertOne( { x: 1 } )
```

The insertOne() operation creates both the database myNewDB and the collection myNewCollection1 if they do not already exist.

----------------------------------------------------------------------------------------------------------------------------------------

# Working with Collections

If a collection does not exist, MongoDB creates the collection when you first store data for that collection.

```
db.myNewCollection2.insertOne( { x: 1 } )
db.myNewCollection3.createIndex( { y: 1 } )
```

_since version 3.2 of mongoDB_

By default, a collection does not require its documents to have the same schema; i.e. the documents in a single collection do not need to have the same set of fields and the data type for a field can differ across documents within a collection.

----------------------------------------------------------------------------------------------------------------------------------------

# Working with Documents

MongoDB stores data records as BSON documents.
BSON is nothing, but just binary representation of JSON documents.

BSON supports the following data types as values in documents. Each data type has a corresponding number and string alias that can be used with the $type operator to query documents by BSON type.

|Type	              |Number	|Alias	Notes             |
|-------------------|-------|-------------------------|
|Double	            |1	    |“double”	                |
|String	            |2	    |“string”	                |
|Object	            |3	    |“object”	                |
|Array	            |4	    |“array”	                |
|Binary data	      |5	    |“binData”	              |
|Undefined	        |6	    |“undefined”	Deprecated. |
|ObjectId	          |7	    |“objectId”              	|
|Boolean	          |8	    |“bool”	                  |
|Date	              |9	    |“date”	                  |
|Null	              |10	    |“null”	                  |
|Regular Expression	|11	    |“regex”	                |
|DBPointer	        |12	    |“dbPointer”	Deprecated. |
|JavaScript	        |13	    |“javascript”           	|
|Symbol	            |14	    |“symbol”	Deprecated.     |
|JavaScript (with scope)|15	|“javascriptWithScope”	  |
|32-bit integer	    |16	    |“int”	                  |
|Timestamp	        |17	    |“timestamp”	            |
|64-bit integer	    |18	    |“long”	                  |
|Decimal128	        |19	    |“decimal”	New in version 3.4.|
|Min key	          |-1	    |“minKey”	                |
|Max key	          |127	  |“maxKey”	                |


MongoDB documents are composed of field-and-value pairs and have the following structure:

```
{
   field1: value1,
   field2: value2,
   field3: value3,
   ...
   fieldN: valueN
}
```

The value of a field can be any of the BSON data types, including other documents, arrays, and arrays of documents. For example, the following document contains values of varying types:

```
var mydoc = {
               _id: ObjectId("5099803df3f4948bd2f98391"),
               name: { first: "Alan", last: "Turing" },
               birth: new Date('Jun 23, 1912'),
               death: new Date('Jun 07, 1954'),
               contribs: [ "Turing machine", "Turing test", "Turingery" ],
               views : NumberLong(1250000)
            }
```

**Notes:**
- Field names are strings.
- The field name \_id is reserved for use as a primary key; its value must be unique in the collection, is immutable, and may be of any type other than an array.
- The field names cannot start with the dollar sign ($) character.
- The field names cannot contain the dot (.) character.
- The field names cannot contain the null character.

In MongoDB, each document stored in a collection requires a unique \_id field that acts as a primary key. If an inserted document omits the \_id field, the MongoDB driver automatically generates an ObjectId for the \_id field.

### ObjectId:
ObjectIds are small, likely unique, fast to generate, and ordered. ObjectId values consists of 12-bytes, where the first four bytes are a timestamp that reflect the ObjectId’s creation, specifically:

- a 4-byte value representing the seconds since the Unix epoch,
- a 3-byte machine identifier,
- a 2-byte process id, and
- a 3-byte counter, starting with a random value.

# CRUD operations
## Inserting

`db.collectionName.insert(
  {
    field1: value1,
    field2: value2,
    field3: value3,
    ...
    fieldN: valueN
  }
  )`

## Finding
`db.collectionName.findOne()` - Finds one arbitrary document <br />
`db.collectionName.find()` - Finds all documents <br />
`db.collectionName.find({}, {name:true, _id:false})` - Shows only the names of the ships <br />
`db.collectionName.findOne({'name':'USS Defiant'})` - Finds one document by attribute

## Updating
`db.collectionName.update({name : 'USS Prometheus'}, {name : 'USS Something'})` -Replaces the whole document <br />
`db.collectionName.update({name : 'USS Something'}, {$set : {operator : 'Starfleet', class : 'Prometheus'}})` - Sets / changes certain attributes of a given document <br />
`db.ships.update({name : 'USS Something'},{$unset : {operator : 1}})` - Removes an attribute from a given document


## Deleting
`db.collectionName.remove({name : 'USS Prometheus'})` - Removes the document <br />
`db.collectionName.remove({name:{$regex:’^USS\\sE’}})` - Removes using operator

### operators
- **$gt / $gte** (greater than / greater than equals)  <br />`db.collectionName.find({class:{$gt:'P'}`
- **$lt / $lte** (lesser than / lesser than equals ) <br/>
`db.collectionName.find({class:{$lte:'P'}`
- **$exists** (does an attribute exist or not) <br />
`db.collectionName.find({type:{$exists:true}})`
- **$regex** (Perl-style pattern matching ) <br />
`db.collectionName.find({name:{$regex:'^USS\\sE'}})`
- **$type** (search by type of an element) <br />
`db.collectionName.find({name : {$type:2}})`

