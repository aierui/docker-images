FROM daocloud.io/centos:7

MAINTAINER centos 7 that dev

# replace base repo
COPY ./files/CentOS-Base.repo /etc/yum.repos.d/

#
RUN mkdir -p /data1/ && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    yum install -y vim rsync gcc-c++  && \
    yum clean all

# 
ENV LC_ALL en_US.UTF-8

# 工作目录
WORKDIR /data1

# 初始化脚本
CMD ["/bin/bash"]