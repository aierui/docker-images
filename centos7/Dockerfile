FROM centos:centos7.8.2003

MAINTAINER centos 7 that dev

# replace base repo
#COPY ./files/CentOS-Base.repo /etc/yum.repos.d/

#
RUN mkdir -p /data1/ && \
    yum install -y wget && \
    curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo && \
    sed -i -e '/mirrors.cloud.aliyuncs.com/d' -e '/mirrors.aliyuncs.com/d' /etc/yum.repos.d/CentOS-Base.repo && \
    curl -o /etc/yum.repos.d/epel.repo https://mirrors.aliyun.com/repo/epel-7.repo && \
    yum clean all && yum makecache && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    yum install -y yum-fastestmirror vim rsync gcc gcc-c++ re2c iproute net-tools \
        aria2 autoconf git make cmake cmake3 bison \
        atop htop sysstat dstat perf gdb tree && \
    yum clean all

# 
ENV LC_ALL en_US.UTF-8

# 工作目录
WORKDIR /data1

# 初始化脚本
CMD ["/bin/bash"]