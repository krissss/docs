# WSL2

## root 登录

```bash
# 在 ubuntu 内
sudo passwd root

# 在 powershell
ubuntu config --default-user root
```

## 重启

在 powershell 下（admin）

```shell
net stop LxssManager
net start LxssManager
```

## 设置代理

```bash
vi ~/.bashrc

# 添加以下内容
# proxy
export hostip=$(cat /etc/resolv.conf |grep -oP '(?<=nameserver\ ).*')
export all_proxy="socks5://${hostip}:10808"
```

重新打开命令行窗口，然后测试：`curl google.com`

## 安装docker

[参考微软教程](https://docs.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-containers)

建议：使用迅雷下载 docker 安装包

