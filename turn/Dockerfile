FROM alpine:latest

ENV GOPATH /usr/local
ENV REALM localhost

RUN apk --no-cache add go git musl-dev && rm -rf /var/cache/apk/*
RUN go get github.com/cespare/reflex github.com/pions/turn

WORKDIR /usr/local/src/github.com/nettyrnp/go-webrtc-cclx/turn
CMD reflex -r . -s go run main.go
