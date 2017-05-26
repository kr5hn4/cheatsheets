# What is Redis?
 Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker.

 Redis is also very often reffered to as, what is called a key-value store or NoSQL database. The essence of a key-value store is the ability to store some data, called a value, inside a key. This data can later be retrieved only if we know the exact key used to store it.

 Redis works with an in-memory dataset and it also allows you to persist the datasets by dumping them to a disk every once in a while, or by appending each command to a log.

### Redis supports the following types of data structures:
strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs and geospatial indexes with radius queries.


### some notes about key naming conventions
- Redis keys are binary safe, this means that you can use any binary sequence as a key, from a string like "foo" to the content of a JPEG file. The empty string is also a valid key.
- The maximum allowed key size is 512 MB.
- The colons in key names as a concept for storing namespaced data <br /> eg. `SET user:1098:name John`

### General commands:

`ECHO 'Hello World!'` - Echo the given string.

`PING [message]` - Ping the server. Returns PONG if no argument is provided, otherwise return a copy of the argument as a bulk. This command is often used to test if a connection is still alive, or to measure latency.

`GET` - Get the value of the specified key. If the key does not exist the special value 'nil' is returned. If the value stored at key is not a string an error is returned because GET can only handle string values.

`SET user:name John` to store the value at a given key <br />

`DEL key1 key2 ... keyN` - Remove the specified keys. If a given key does not exist no operation is performed for this key. The commnad returns the number of keys removed.

`INCR key` & `DECR key` - Increment or decrement the number stored at key by one. If the key does not exist or contains a value of a wrong type, set the key to the value of "0" before to perform the increment or decrement operation.

`INCRBY key integer` & `DECRBY key integer` - INCRBY and DECRBY work just like INCR and DECR but instead to increment/decrement by 1 the increment/decrement is integer.

INCR commands are limited to 64 bit signed integers.

`QUIT` - Ask the server to close the connection. The connection is closed as soon as all pending replies have been written to the client.

### working with lists

A list is a series of ordered values. Some of the important commands for interacting with lists are `LPUSH`, `RPUSH`, `LLEN`, `LRANGE`, `LPOP`, and `RPOP`. You can immediately begin working with a key as a list, as long as it doesn't already exist as a different type.

`LPUSH` - puts the new value at the start of the list.
    `LPUSH planets 'mercury'`

`RPUSH` puts the new value at the end of the list.
    `RPUSH planets 'venus'`
    `RPUSH planets 'earth'`

`LRANGE` gives a subset of the list. It takes the index of the first element you want to retrieve as its first parameter and the index of the last element you want to retrieve as its second parameter. A value of -1 for the second parameter means to retrieve elements until the end of the list.

    `LRANGE planets 0 -1`
  =>
    1) 'mercury'
    2) 'venus'
    3) 'earth'

    `LRANGE planets 0 1`
  =>
    1) 'mercury'
    2) 'venus'

    `LRANGE planets 1 2`
  =>
    1) 'venus'
    2) 'earth'

## working with sets in Redis

 A set is similar to a list, except it does not have a specific order and each element may only appear once. Some of the important commands in working with sets are `SADD`, `SREM`, `SISMEMBER`, `SMEMBERS` and `SUNION`.

`SADD` - Adds the given value to the set.
    `SADD todo 'learn redis'`
    `SADD todo 'use redis in a project'`
    `SADD todo 'make a redis cheatsheet'`

`SREM` - Removes the given value from the set.
    `SREM todo 'make a redis cheatsheet'`

## List of commands supported by Redis:

 DECR, DECRBY, DEL, EXISTS, EXPIRE, GET, GETSET, HDEL, HEXISTS, HGET, HGETALL, HINCRBY, HKEYS, HLEN, HMGET, HMSET, HSET, HVALS, INCR, INCRBY, KEYS, LINDEX, LLEN, LPOP, LPUSH, LRANGE, LREM, LSET, LTRIM, MGET, MSET, MSETNX, MULTI, PEXPIRE, RENAME, RENAMENX, RPOP, RPOPLPUSH, RPUSH, SADD, SCARD, SDIFF, SDIFFSTORE, SET, SETEX, SETNX, SINTER, SINTERSTORE, SISMEMBER, SMEMBERS, SMOVE, SORT, SPOP, SRANDMEMBER, SREM, SUNION, SUNIONSTORE, TTL, TYPE, ZADD, ZCARD, ZCOUNT, ZINCRBY, ZRANGE, ZRANGEBYSCORE, ZRANK, ZREM, ZREMRANGEBYSCORE, ZREVRANGE, ZSCORE
 70
