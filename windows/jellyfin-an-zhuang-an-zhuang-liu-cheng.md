# jellyfin安装安装流程

## 安装

[服务端](https://jellyfin.org/downloads/server)

[客户端](https://jellyfin.org/downloads/clients/)

默认端口：8096

## 问题

### 局域网不能访问

windows 局域网访问需要开放防火墙入站端口（8096）

### TMDB 如果获取不到信息

需要配置 api.themoviedb.org 的 hosts 指向

* 方法一：http://tool.chinaz.com/speedworld/api.themoviedb.org 测速 取一个速度还可以的，不丢包的
* 方法二：https://dnschecker.org/ 搜索 api.themoviedb.org，找到Hangzhou, China

官网： https://www.themoviedb.org/

### web端需要转码时 ffmpeg cpu 占用较高

使用 [windows 播放客户端](https://github.com/jellyfin/jellyfin-media-player/releases)
