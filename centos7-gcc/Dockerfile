FROM registry.cn-beijing.aliyuncs.com/aierui/centos7:1.0

MAINTAINER centos 7 with gcc(8.2.0) that dev

RUN mkdir -p /tmp/download && \
    cd /tmp/download && \
	yum update -y && \
    echo "Download gcc" && \
    wget -q -O /tmp/download/gcc-8.2.0.tar.xz http://mirrors.ustc.edu.cn/gnu/gcc/gcc-8.2.0/gcc-8.2.0.tar.xz && \
    echo "Unpack gcc" && \
    tar xf gcc-*.xz && \
    cd /tmp/download/gcc-* && \
    echo "Download gcc dependent" && \
    ./contrib/download_prerequisites && \
    echo "gcc configure" && \
    ./configure --enable-checking=release --enable-languages=c,c++ --disable-multilib > /dev/null && \
    echo "make" && \
    make -j4  > /dev/null && \
    make install && \
    yum -y erase wget gcc gcc-c++ bzip2 && \
    yum clean all && \
    cd /data1 && \
    rm -Rf /tmp/download
    
WORKDIR /data1/