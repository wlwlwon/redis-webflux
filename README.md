# redis-webflux


Redis 명령어 정리


flushdb

hset user:1 name sma age 10 city atlanta
-3
hget name
-"sam"
hget age
-"10"

hgetall user:1
1)"name"
2)"sam"
3)"age"
4)"10"
5)"city"
6)"atlanta"


expire user:2 10 ->지정된 시간 후 key 자동 삭제
-1
ttl user:2 -> 남은 시간 확인
(integer)6

keys *
"user:1"

hkeys user:1
1)"name"
2)"age"
3)"city"

hexists user:1 status
0
hexists user:1 age
1

hdel user:1 age
1

hgetall user:1
1)"name"
2)"sam"
3)"city"
4)"atlanta"

del user:1
1
keys *
(empty array)

push ( rpush, lpush)

rpush users sam mike jake
(integer) 3

keys *
"users"

type users
list

llen users //(list length hlen:hash length)
(integer)3

lrange users 0 -1
1)"sam"
2)"mike"
3)"jake"

lrange users 0 1
1)"sam"
2)"mike"

lpop users
"sam"

lrange users 0 -1
1)"mike"
2)"jake"


sadd users 1 2 3 4 5
5
scard users (s cardinality)
(integer) 5

smembers users
1
2
3
4
5

sismember users 5
1

sismember users 100
0

srem users 199 (set remove)
0

srem users 5
1

sismember users 5
0

sadd skill:java 1 2 3 4
4
sadd skill:js 2 3 4
3
sadd skill:asw 4 5 6
3

sinter skill:java skill:js skill:aws
"4"

sunion skill:java skill:js
1
2
3
4

sadd candidate:criminal 4 5 6
3

sdiff skill:java cancidate:creiminal
1
2
3

sinterstore java-js skill:java skill:js
3
smembers java-js
2
3
4


zadd products 0 books
1
zadd products 0 iphone 0 tv
2

zincrby products 1 books
1
zincrby products 1 iphone
1
zincrby products 1 iphone
2
zincrby products 1 tv
1
zrange products 0 -1
books
tv
iphone

zrange products -1 -1
iphone

zrange products 0 0 rev
iphone

zrange products 0 1 rev withscores
iphone
3
books
2

zrank products books
1
zrank products iphone
2
zrevrank products iphone
0
zscore products iphone
3
zpopmax products
iphone
3
