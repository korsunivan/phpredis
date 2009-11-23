PhpRedis
=============


Installing/Configuring
======================

Functions
=========


## get
##### *Description*

Get the value related to the specified key

##### *Parameters*

key : key

##### *Return Value*

If key didn't exist, FALSE is returned. Else, the value related to this key is returned.

##### *Examples*

$redis->get('key');

## set
##### Description

Set the string value in argument as value of the key.

##### Parameters
*Key* : key
*Value* : Value

##### Return value
*Bool* : TRUE if the SET is successful.

##### Examples

<pre>
$redis->set('key', 'value')
</pre>

## setnx
##### Description
Set the string value in argument as value of the key if the target key already exists.

##### Parameters
*key*
*value*

##### Return value
*BOOL*

##### Examples
<pre>
$this->redis->setnx('key', 'value'); /* return TRUE */
$this->redis->setnx('key', 'value'); /* return FALSE */
</pre>

## delete
##### Description
##### Parameters
##### Return value
##### Examples


## exists
##### Description
Vérify if the specified key exists.
##### Parameters
*key* : key 
##### Return value
*BOOL* : If the key exists, return TRUE, else return FALSE.
##### Examples
<pre>
$this->set('key', 'value');
$this->exists('key'); /* TRUE*/
$this->exists('NonExistingKey'); /* FALSE*/
</pre>

## incr
##### Description
Increment the number stored at key by one. If the second argument is filled, it will be used as the integer value of the increment.
##### Parameters
*key* : key
*value* : value that will be incremented to key
##### Return value
*INT* the new value of incremented value
##### Examples
<pre>
$redis->incr('key1'); /*key1 didn't exists, setted to 0 before the increment */
					  /*and now has the value 1 							 */

$redis->incr('key1'); /* 2 */
$redis->incr('key1'); /* 3 */
$redis->incr('key1'); /* 4 */
</pre>

## decr
##### Description
##### Parameters
##### Return value
##### Examples

## mget
##### Description
##### Parameters
##### Return value
##### Examples

## rpush
##### Description
##### Parameters
##### Return value
##### Examples

## lpush
##### Description
##### Parameters
##### Return value
##### Examples
## rpop
## lpop
## llen
## lindex
## lset
## lrange
## ltrim
## lrem
## sadd
## srem
## smove
## sismember
## scard
## spop
## sinter

##### *Description*

Return the members of a set resulting from the intersection of all the sets hold at the specified keys.
if just a single key is specified, then this command produces the members of this set. If one of the keys
is missing, FALSE is returned.

##### *Parameters*

key1, key2, keyN : keys identifying the different set on which we will apply the intersection.
		
##### *Return value*

Array, contain the result of the intersesction between those keys. If the Intersection beteen the different set is empty, the return value will be empty array.

##### *Examples*

<pre>
$redis = new Redis();
$redis->connect('127.0.0.1', 6379);
$redis->sadd('key1', 'val1');
$redis->sadd('key1', 'val2');
$redis->sadd('key1', 'val3');
$redis->sadd('key1', 'val4');

$redis->sadd('key2', 'val3');
$redis->sadd('key2', 'val4');

$redis->sadd('key3', 'val3');
$redis->sadd('key3', 'val4');

var_dump($redis->sinter('key1', 'key2', 'key3'));
</pre>

the output :

<pre>
array(2) {
  [0]=>
  string(4) "val4"
  [1]=>
  string(4) "val3"
}
</pre>

## sinterstore
## sunion
## sunionstore
## sdiff
## sdiffstore
## smembers
## incrby
## decrby
## getset
## randomkey
## select
## move
## rename
## renamenx
## expire
## keys
## dbsize
## auth
## save
## bgsave
## lastsave
## type
##### *Description*
Returns the type of data pointed by a given key.

##### *Parameters*
key: string.

##### *Return value*

Depending on the type of the data pointed by the key, this method will return the following value:
* string: 1
* set: 2
* list: 3
* other: 0

## flushdb

##### *Description*
Removes all entries from a given database.

##### *Parameters*
dbindex: integer, the database number to delete from. The first database has number zero.

## flushall
##### *Description*
Removes all entries from all databases.

##### *Parameters*
None.

## sort

## info
##### *Description*
Returns an associative array of strings and integers, with the following keys:

* redis_version
* arch_bits
* uptime_in_seconds
* uptime_in_days
* connected_clients
* connected_slaves
* used_memory
* changes_since_last_save
* bgsave_in_progress
* last_save_time
* total_connections_received
* total_commands_processed
* role


##### *Parameters*
None.

## ttl
##### *Description*
Returns the time to live left for a given key, in seconds. If the key doesn't exist, FALSE is returned.

##### *Parameters*
key: string

##### *Return value*
Long, the time left to live in seconds.