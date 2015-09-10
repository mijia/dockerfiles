FROM sunyi00/centos-golang:1.0.0

RUN yum -y install gcc-c++ snappy \
    && yum -y clean all \
    && mkdir -p /tmp/vendor \
    && git clone https://github.com/facebook/rocksdb /tmp/vendor/rocksdb \
    && cd /tmp/vendor/rocksdb \
    && git checkout v3.13.1 \ 
    && make install-shared \
    && ln -s /usr/lib64/libbz2.so.1 /usr/lib64/libbz2.so \
    && ln -s /usr/lib64/libsnappy.so.1 /usr/lib64/libsnappy.so \
    && rm -rf /tmp/vendor \
    && yum -y erase gcc-c++

WORKDIR /go
