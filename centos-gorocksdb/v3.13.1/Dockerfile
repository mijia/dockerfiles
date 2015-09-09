FROM sunyi00/centos-golang:1.0.0

RUN yum -y install gcc-c++ snappy \
    && yum -y clean all \
    && mkdir -p /go/vendor \
    && git clone https://github.com/facebook/rocksdb /go/vendor/rocksdb \
    && cd /go/vendor/rocksdb \
    && git checkout v3.13.1 \ 
    && make install-shared \
    && ln -s /usr/lib64/libbz2.so.1 /usr/lib64/libbz2.so \
    && ln -s /usr/lib64/libsnappy.so.1 /usr/lib64/libsnappy.so \
    && CGO_CFLAGS="-I/go/vendor/rocksdb/include" CGO_LDFLAGS="-L/usr/lib64" go get github.com/tecbot/gorocksdb 
    && rm -rf /go/vendor

WORKDIR /go

