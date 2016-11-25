# Redis KV Docker with Alpine Base Image

## Docker Build
```shell
docker build -t lucmichalski/redis-alpine .
```

## Docker Build (No cache)
```shell
docker build -t lucmichalski/redis-alpine --no-cache .
```

## Docker Run

```shell
docker run -d\
 --name redis-6379\
 -v /host/dir:/data\
 -p 6379:6379/tcp\
  lucmichalski/redis-alpine \
   --port 6379\
   --protected-mode no\
   --logfile redis-6379.log
```

## Docker Compose

```yaml
version: '2'

services:
 redis-6379:
  ports:
   - "6379:6379"
  volumes:
   - /host/dir/redis/modules:/modules
   - /host/dir/redis/data:/data
  image: lucmichalski/redis-alpine
  command: ['--port', '6379', '--protected-mode', 'no', 'logfile', 'redis-6379.log']
```
