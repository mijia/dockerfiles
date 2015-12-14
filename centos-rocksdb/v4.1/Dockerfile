FROM sunyi00/centos-golang:1.0.0

RUN yum -y install gcc-c++ snappy \
    && yum -y clean all \
    && mkdir -p /tmp/vendor \
    && git clone https://github.com/facebook/rocksdb /tmp/vendor/rocksdb \
    && cd /tmp/vendor/rocksdb \
    && git checkout v4.1 \
    && make static_lib \
    && mv librocksdb.a /usr/lib \
    && mv include/rocksdb /usr/local/include \
    && ln -s /usr/lib64/libbz2.so.1 /usr/lib64/libbz2.so \
    && ln -s /usr/lib64/libsnappy.so.1 /usr/lib64/libsnappy.so \
    && rm -rf /tmp/vendor \

ENV CGO_LDFLAGS="-L/usr/lib -lrocksdb -lstdc++ -lm -lz"
WORKDIR /go
