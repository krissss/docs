各项 docker-stack 的集合

# 基本操作

```bash
# docker
docker -h
# composer
docker-compose -h
# swarm
docker swarm -h
# 服务
docker service -h
# stack
docker stack -h
```

# docker volume 修改

```bash
# 停止服务
service docker stop
# 移动到挂载目录
mv /opt/docker/volumes /mnt/docker-volumes
# 建立软链
ln -s /mnt/docker-volumes /opt/docker/volumes
# 启动服务
service docker start
```