# WSL2初始操作

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

