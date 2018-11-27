FROM ubuntu:bionic

ARG VERSION="3.6.1"

RUN apt-get update && \
    apt-get upgrade -y

RUN apt-get install -y autoconf automake libtool curl make g++ unzip wget

# Getting the sourcecode
RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.6.1/protobuf-cpp-${VERSION}.tar.gz
RUN tar xvzf protobuf-cpp-3.6.1.tar.gz
# Compiling
WORKDIR protobuf-${VERSION}
RUN ./configure --prefix=/usr
RUN make
RUN make check
RUN make install

# refresh shared library cache
RUN ldconfig

# Running protoc
ENTRYPOINT ["protoc"]
CMD ["--out=/data", "/data/default.proto"]
