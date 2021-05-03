# Usage

```bash
# 安装 docker
# @link https://docs.docker.com/engine/install/

# 初始化 swarm
docker swarm init

# 安装 kong
docker stack deploy --compose-file=docker-stack.yml kong
```

## konga 使用

Kong Admin URL: http://kong:8001

# Link

[Kong](https://github.com/Kong/docker-kong/tree/master/compose)
[KongA](https://github.com/pantsel/konga/issues/533)