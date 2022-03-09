FROM golang:1.17

RUN apt-get update \
    && apt install -y protobuf-compiler

RUN go get -u google.golang.org/grpc \ 
    && go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.26 \
    && go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.1

WORKDIR /usr/local/grpc
COPY ./tls-go-client-server.proto ./
RUN mkdir ./proto

CMD protoc --go_out=./proto ./tls-go-client-server.proto