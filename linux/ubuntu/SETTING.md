# 设置

## 修改 apt 源

```bash
cp /etc/apt/sources.list /etc/apt/sources.list.bak
sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
sed -i s@/security.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
```