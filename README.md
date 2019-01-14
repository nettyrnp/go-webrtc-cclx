# WebRtc-Cclx
WebRtc-Cclx is a minimal deploy with multi-conferencing functionality. It has a working signaler, TURN server and web app.

### Prerequisites
A working Docker and Docker Compose setup.

### Installing
## Install Golang
```
see https://golang.org/doc/install
```
## Install WebRtc-Cclx
```
go get -u github.com/nettyrnp/go-webrtc-cclx
```

### Running

* Generate your SSL certificates, WebRTC only works over HTTPS so we have to serve `www` and `signaler` via HTTPS
```
./create-ssl-cert.sh
```
* Start a multi-conference via a single command
```
docker-compose up --build
```
* Open up https://<the_host>:5000/ After you share your webcam you have joined the conference. 
Here <the_host> is 'localhost' or some specific IP where you placed the WebRtc-Cclx and where you run 'docker-compose up'.
