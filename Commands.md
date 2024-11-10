# Redis Commands Guide

Redis is an in-memory data structure store that supports various types of data structures, each with a unique set of commands. This guide provides a detailed overview of commands for the most commonly used data types and features in Redis.

---

## 1. General Commands

- **PING**: Test connectivity to the Redis server.

  ```bash
  PING  # Response: PONG
  ```

- **SELECT**: Switch to a different database (0-15 by default).

  ```bash
  SELECT 1
  ```

- **DBSIZE**: Return the number of keys in the current database.

  ```bash
  DBSIZE
  ```

- **KEYS**: List keys matching a pattern (use carefully in production as it can be slow).

  ```bash
  KEYS *
  ```

- **DEL**: Delete one or more keys.

  ```bash
  DEL key1 key2
  ```

- **EXISTS**: Check if a key exists.

  ```bash
  EXISTS key
  ```

- **EXPIRE**: Set a time-to-live (TTL) for a key in seconds.

  ```bash
  EXPIRE key 60
  ```

- **TTL**: Check the remaining TTL for a key.

  ```bash
  TTL key
  ```

---

## 2. String Commands

Strings are the most basic data type in Redis, holding text or binary data.

- **SET**: Set the value of a key.

  ```bash
  SET key "value"
  ```

- **GET**: Retrieve the value of a key.

  ```bash
  GET key
  ```

- **INCR / DECR**: Increment or decrement the integer value of a key.

  ```bash
  INCR counter
  DECR counter
  ```

- **APPEND**: Append a value to an existing key.

  ```bash
  APPEND key "more text"
  ```

- **GETRANGE**: Get a substring of the string stored at a key.

  ```bash
  GETRANGE key 0 4
  ```

- **MSET / MGET**: Set or get multiple key-value pairs at once.

  ```bash
  MSET key1 "value1" key2 "value2"
  MGET key1 key2
  ```

---

## 3. List Commands

Lists are ordered collections of strings, implemented as linked lists.

- **LPUSH / RPUSH**: Add an element to the beginning or end of a list.

  ```bash
  LPUSH list "element1"
  RPUSH list "element2"
  ```

- **LPOP / RPOP**: Remove and return the first or last element of a list.

  ```bash
  LPOP list
  RPOP list
  ```

- **LRANGE**: Get a range of elements from a list.

  ```bash
  LRANGE list 0 -1  # Get all elements
  ```

- **LLEN**: Get the length of a list.

  ```bash
  LLEN list
  ```

- **LSET**: Set the value of an element at a specific index.

  ```bash
  LSET list 1 "new_value"
  ```

---

## 4. Set Commands

Sets are unordered collections of unique strings.

- **SADD**: Add one or more members to a set.

  ```bash
  SADD set "member1" "member2"
  ```

- **SMEMBERS**: Get all members in a set.

  ```bash
  SMEMBERS set
  ```

- **SISMEMBER**: Check if a member exists in a set.

  ```bash
  SISMEMBER set "member"
  ```

- **SREM**: Remove one or more members from a set.

  ```bash
  SREM set "member"
  ```

- **SUNION / SINTER / SDIFF**: Perform union, intersection, or difference operations on multiple sets.

  ```bash
  SUNION set1 set2
  SINTER set1 set2
  SDIFF set1 set2
  ```

---

## 5. Hash Commands

Hashes are collections of key-value pairs, useful for storing objects.

- **HSET**: Set the value of a field in a hash.

  ```bash
  HSET hash field "value"
  ```

- **HGET**: Get the value of a field in a hash.

  ```bash
  HGET hash field
  ```

- **HMSET / HMGET**: Set or get multiple fields in a hash at once.

  ```bash
  HMSET hash field1 "value1" field2 "value2"
  HMGET hash field1 field2
  ```

- **HGETALL**: Get all fields and values in a hash.

  ```bash
  HGETALL hash
  ```

- **HINCRBY**: Increment the integer value of a hash field.

  ```bash
  HINCRBY hash field 1
  ```

- **HEXISTS**: Check if a field exists in a hash.

  ```bash
  HEXISTS hash field
  ```

---

## 6. Sorted Set Commands

Sorted sets are collections of unique strings with a score assigned to each element.

- **ZADD**: Add one or more members to a sorted set, with scores.

  ```bash
  ZADD zset 1 "member1" 2 "member2"
  ```

- **ZRANGE / ZREVRANGE**: Get a range of members in a sorted set, by index.

  ```bash
  ZRANGE zset 0 -1  # Get all members
  ZREVRANGE zset 0 -1  # Get all members in reverse
  ```

- **ZSCORE**: Get the score associated with a member in a sorted set.

  ```bash
  ZSCORE zset "member1"
  ```

- **ZINCRBY**: Increment the score of a member in a sorted set.

  ```bash
  ZINCRBY zset 1 "member1"
  ```

- **ZREM**: Remove one or more members from a sorted set.

  ```bash
  ZREM zset "member"
  ```

---

## 7. Pub/Sub Commands

Redis provides a simple publish/subscribe messaging system.

- **PUBLISH**: Send a message to a channel.

  ```bash
  PUBLISH channel "message"
  ```

- **SUBSCRIBE**: Subscribe to a channel.

  ```bash
  SUBSCRIBE channel
  ```

- **UNSUBSCRIBE**: Unsubscribe from a channel.

  ```bash
  UNSUBSCRIBE channel
  ```

---

## 8. Transaction Commands

Redis supports transactions to execute multiple commands atomically.

- **MULTI**: Begin a transaction block.
- **EXEC**: Execute all commands in a transaction.
- **DISCARD**: Discard all commands in a transaction.

Example:

```bash
MULTI
SET key "value"
INCR counter
EXEC
```

---

## 9. Scripting Commands (Lua)

- **EVAL**: Execute a Lua script in Redis.

  ```bash
  EVAL "return redis.call('SET', KEYS[1], ARGV[1])" 1 key "value"
  ```

---

## 10. Administrative Commands

- **SAVE / BGSAVE**: Save the dataset to disk synchronously or asynchronously.

  ```bash
  SAVE
  BGSAVE
  ```

- **MONITOR**: Monitor all commands received by the server in real-time.

  ```bash
  MONITOR
  ```

- **INFO**: Get information and statistics about the server.

  ```bash
  INFO
  ```

- **FLUSHALL / FLUSHDB**: Delete all keys in all databases or the current database.

  ```bash
  FLUSHALL
  FLUSHDB
  ```

---

This guide covers fundamental Redis commands for various use cases, including data storage, cache management, messaging, and server administration. Redis commands are flexible and powerful, allowing you to build real-time, high-performance applications.
