FROM registry.cn-beijing.aliyuncs.com/aierui/centos7:1.0

MAINTAINER PHP 7.4.5 that dev

## env
ENV PATH  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/server/sbin/:/usr/local/server/bin

# RUN yum makecache
RUN yum install -y deltarpm libxml2 libxml2-devel openssl-devel bzip2-devel libcurl-devel \
        db4-devel gdbm-devel libwebp-devel libjpeg-turbo-devel libpng-devel \
        libXpm-devel freetype-devel openldap-devel libmcrypt-devel \
        sqlite-devel libtidy-devel libxslt-devel ImageMagick-devel \
        libevent-devel libmemcached-devel libdb-devel \
        gmp-devel mariadb-devel libyaml-devel \
        oniguruma oniguruma-devel \
        graphviz hiredis-devel jemalloc-devel readline-devel

ADD ./files/php-7.4.5.tar.gz ./files/libzip-1.5.2.tar.gz /tmp/

RUN ls -la /tmp && cd /tmp/libzip-1.5.2 \
    && ls -la  && mkdir build && cd build && cmake3 .. && make && make install

# install php, php extensions start
RUN cd /tmp/php-7.4.5 && export MAKE_CPU_CORE="`fgrep processor /proc/cpuinfo|tail -1|awk -F ':' '{print $2}'`" \
    && ./buildconf --force \
    && ./configure \
        --prefix=/usr/local/server \
        --exec-prefix=/usr/local/server \
        --bindir=/usr/local/server/bin \
        --sbindir=/usr/local/server/sbin \
        --sysconfdir=/usr/local/server/etc \
        --datadir=/usr/local/server/share \
        --includedir=/usr/local/server/include \
        --libexecdir=/usr/local/server/libexec \
        --localstatedir=/usr/local/server/var \
        --sharedstatedir=/usr/local/server/share/com \
        --mandir=/usr/local/server/share/man \
        --infodir=/usr/local/server/share/info \
        --with-pear=/usr/local/server/lib/php \
        --with-config-file-path=/usr/local/server/lib/php \
        --with-libdir=lib64 \
        --with-sqlite3=shared \
        --with-curl=shared,/usr/local/curl/ \
        --with-ldap=shared \
        --with-xmlrpc=shared \
        --with-zlib=shared \
        --with-bz2=shared \
        --with-iconv=shared \
        --with-mhash=shared,/usr/local/server \
        --with-mcrypt=shared,/usr/local/server \
        --with-gd=shared \
        --with-png-dir=/usr \
        --with-jpeg-dir=/usr \
        --with-freetype-dir=/usr \
        --enable-gd-native-ttf \
        --disable-debug \
        --disable-rpath \
        --enable-simplexml \
        --enable-libxml \
        --enable-filter \
        --enable-ftp \
        --enable-xmlreader=shared \
        --enable-xmlwriter=shared \
        --enable-hash \
        --enable-phar=shared \
        --enable-json=shared \
        --enable-dom=shared \
        --enable-pdo=shared \
        --with-pdo-sqlite=shared,/usr \
        --enable-zip=shared \
        --with-zlib-dir=/usr \
        --enable-xml \
        --with-gmp \
        --with-xsl=shared,/usr \
        --enable-mbstring=shared,all \
        --enable-ftp=shared \
        --enable-bcmath=shared \
        --enable-shmop=shared \
        --enable-sysvsem=shared \
        --enable-sysvshm=shared \
        --enable-sysvmsg=shared \
        --enable-sockets=shared \
        --enable-exif=shared \
        --enable-soap=shared \
        --enable-wddx=shared \
        --with-tidy=shared,/usr \
        --with-pic \
        --enable-inline-optimization \
        --with-openssl \
        --with-gettext=shared \
        --with-config-file-scan-dir=/usr/local/server/lib/php.d/ \
        --enable-fpm \
        --enable-cli \
        --enable-pcntl \
        --with-readline \
    && make -j $MAKE_CPU_CORE && \
	make install && \
    cd /tmp && rm -rf *  && \
    # phplint
    curl -L -o /usr/local/bin/phpunit https://phar.phpunit.de/phpunit.phar && \
    chmod +x /usr/local/bin/phpunit && \
    # remove denpentdent libray
    yum erase -y deltarpm libxml2-devel openssl-devel bzip2-devel libcurl-devel \
        db4-devel gdbm-devel libwebp-devel libjpeg-turbo-devel libpng-devel \
        libXpm-devel freetype-devel openldap-devel libmcrypt-devel \
        sqlite-devel libtidy-devel libxslt-devel ImageMagick-devel \
        libevent-devel libmemcached-devel libdb-devel \
        gmp-devel mariadb-devel libyaml-devel \
        oniguruma oniguruma-devel \
        graphviz hiredis-devel jemalloc-devel readline-devel && \
    yum clean all


# 初始化脚本
CMD ["/usr/local/server/sbin/php-fpm", "-F"]

