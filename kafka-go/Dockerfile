FROM golang:latest



RUN apt-get update && \
    apt-get upgrade -y
RUN apt-get install -y \
#            python3-software-properties \
#            software-properties-common \
#            apt-transport-https \
            openssl \
            libssl1.1 \
            libsasl2-2 \
            libsasl2-modules-gssapi-mit \
        && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# RUN wget -qO - https://packages.confluent.io/deb/5.0/archive.key | apt-key add -
# RUN add-apt-repository "deb [arch=amd64] https://packages.confluent.io/deb/5.0 stable main"

# Updating repo info so the cnfulent repo is used
# RUN apt-get update 

# RUN apt-get install -y confluent-platform-oss-2.11
# RUN apt-get install -y librdkafka1 librdkafka-dev
RUN git clone https://github.com/edenhill/librdkafka.git
WORKDIR librdkafka
RUN ./configure --prefix=/usr
RUN make
RUN make install

WORKDIR /go/src/app
COPY . .

RUN go get -d -v ./...
RUN go install -v ./...

CMD ["app"]

