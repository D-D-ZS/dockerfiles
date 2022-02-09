# 介绍
用于创建增加ssh 服务的 centos 镜像
# 使用方法
## 1. 复制需要登录的公钥信息到authorized_keys
公钥信息一般在本地用户目录下，~/.ssh/id_rsa.pub，如果没有可以通过 `ssh-keygen -t rsa` 命令生成

## 2. 创建镜像
```
cd sshd_centos
docker build -t centos_sshd:7.5 .
```

## 3. 启动镜像
```
docker run -d -p 10022:22 centos_sshd:7.5
```

## 4. 测试连接
```
ssh root@localhost -p 10022
```
