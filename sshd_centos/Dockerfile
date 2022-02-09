# 设置继承镜像
FROM centos:7.5.1804
# 作者信息
MAINTAINER dandan9 (dandan9@docker.com)
# 更新yum源
RUN yum update -y
# 安装ssh服务
RUN yum install -y openssh-server
RUN mkdir -p /var/run/sshd
RUN mkdir -p /root/.ssh
RUN ssh-keygen -A
# 取消pam限制
RUN sed -ri 's/session required pad_loginuid.so/#session required pad_loginuid.so/g' /etc/pam.d/sshd
# 服务质量配置文件到响应位置，并赋予脚本执行权限
ADD authorized_keys /root/.ssh/authorized_keys
ADD run.sh /run.sh
RUN chmod 755 /run.sh
# 开放端口
EXPOSE 22
# 设置自启动命令
CMD ["/run.sh"]
