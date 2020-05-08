FROM daocloud.io/centos:7

MAINTAINER centos 7 that dev

# replace base repo
#COPY ./files/CentOS-Base.repo /etc/yum.repos.d/

#
RUN mkdir -p /data1/ && \
    yum install -y wget && \
    mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base-Origin.repo && \
    wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo && \
    yum clean all && yum makecache && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    yum install -y vim rsync gcc-c++ re2c iproute net-tools \
        aria2 autoconf git make cmake cmake3 bison \
        atop htop sysstat dstat perf losf gdb tree && \
    yum clean all

# 
ENV LC_ALL en_US.UTF-8

# 工作目录
WORKDIR /data1

# 初始化脚本
CMD ["/bin/bash"]