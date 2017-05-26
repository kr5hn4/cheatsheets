# What is Redis?
#### Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker.

#### Redis is also very often reffered to as, what is called a key-value store or NoSQL database. The essence of a key-value store is the ability to store some data, called a value, inside a key. This data can later be retrieved only if we know the exact key used to store it.

#### Redis works with an in-memory dataset and it also allows you to persist the datasets by dumping them to a disk every once in a while, or by appending each command to a log.

### Redis supports the following types of data structures:
strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs and geospatial indexes with radius queries.


#### some notes about key naming conventions
- Redis keys are binary safe, this means that you can use any binary sequence as a key, from a string like "foo" to the content of a JPEG file. The empty string is also a valid key.
- The maximum allowed key size is 512 MB.
- The colons in key names as a concept for storing namespaced data <br /> eg. `SET user:1098:name John`

### Commands:
`SET` to store the value at a given key <br />
eg. `SET user:name John`

`GET` - Get the value of key. An error is returned if the value stored at key is not a string, because GET only handles string values.

`DEL` - to delete a given key and associated value

## List of commands supported by Redis:

 DECR, DECRBY, DEL, EXISTS, EXPIRE, GET, GETSET, HDEL, HEXISTS, HGET, HGETALL, HINCRBY, HKEYS, HLEN, HMGET, HMSET, HSET, HVALS, INCR, INCRBY, KEYS, LINDEX, LLEN, LPOP, LPUSH, LRANGE, LREM, LSET, LTRIM, MGET, MSET, MSETNX, MULTI, PEXPIRE, RENAME, RENAMENX, RPOP, RPOPLPUSH, RPUSH, SADD, SCARD, SDIFF, SDIFFSTORE, SET, SETEX, SETNX, SINTER, SINTERSTORE, SISMEMBER, SMEMBERS, SMOVE, SORT, SPOP, SRANDMEMBER, SREM, SUNION, SUNIONSTORE, TTL, TYPE, ZADD, ZCARD, ZCOUNT, ZINCRBY, ZRANGE, ZRANGEBYSCORE, ZRANK, ZREM, ZREMRANGEBYSCORE, ZREVRANGE, ZSCORE
