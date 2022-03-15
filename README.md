```
docker network create redis

docker run -it --rm --name redis --net redis -p 6379:6379 redis:6.2.6-alpine
```

Configuration

- Github default config document for each version, redis.conf
    - Mount this to the container using a docker volume (the entire config directory) - run redis server as an entry point, pointined to the redis.conf file definied in the bind mount
```
docker run -it --rm --name redis --net redis -v ${PWD}/config:/etc/redis -p 6379:6379 redis:6.2.6-alpine redis-server /etc/redis/redis.conf
```

Redis instance do not use passwords by default - requirepassword configuration key

RDB vs AOF mode for persistence (config settings):
    - RDB: dbfilename <dump>
    - appendonly: yes

Create a docker volume (redis) and mount it into your container


```
docker volume create redis

docker run -it --rm --name redis --net redis -v ${PWD}/config:/etc/redis/ -v redis:/data/  redis:6.0-alpine redis-server /etc/redis/redis.conf
```
# redis
