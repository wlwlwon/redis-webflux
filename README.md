# redis-webflux

This repository contains the code samples With Spring WebFlux

Redis 명령어 정리

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


