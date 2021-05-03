# FAQ

> swarm 模式下默认的 ingress 网络下，各 service 之间不能通过 name 联通（同 stack 除外）

原因：未知

解决办法：新建一个 ingress(overlay) 网络，将需要通过 name 联通的 service 加入该网络

> portainer 下无直接操作 service 加入网络的功能，且 container 不能直接加入新建的 ingress 网络

原因：
[issue-1807](https://github.com/portainer/portainer/issues/1807)
[issue-3546](https://github.com/portainer/portainer/issues/3546)

解决办法：通过命令行加入网络

```bash
# service 加入网络
docker service update $SERVICE --network-add $NETWORK1 --network-rm $NETWORK2

# container 加入网络
docker network connect $NETWORK2 $CONTAINER
```