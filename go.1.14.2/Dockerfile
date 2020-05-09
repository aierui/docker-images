FROM registry.cn-beijing.aliyuncs.com/aierui/centos7:1.0

MAINTAINER golang dev

RUN cd /data1 && \
    curl -o ./go.tar.gz https://dl.google.com/go/go1.14.2.linux-amd64.tar.gz && \
    tar zxf ./go.tar.gz -C /usr/local && \
    ln -s /usr/local/go/bin/* /usr/local/bin/ && \
    rm -Rf /data1/go.* && \
	yum install -y git gcc gcc-c++ make && yum clean all && \
    mkdir -p /go
ENV GOPROXY https://goproxy.cn,direct
# ENV GO111MODULE auto
ENV PATH /usr/local/go/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/go/sh:/go/bin
ENV GOPATH /go
