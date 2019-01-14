# WebRtc-Cclx
WebRtc-Cclx is a minimal deploy with multi-conferencing functionality. It has a working signaler, TURN server and web app.

### Prerequisites
A working Docker and Docker Compose setup.

### Running
For developing a docker-compose.yml is available with features like hot-reloads so you can quickly start developing.

* Trust all localhost HTTPS certificates --  open [chrome://flags](chrome://flags/#allow-insecure-localhost) in a new tab and enable `#allow-insecure-localhost`
* Generate your SSL certificates, WebRTC only works over HTTPS so we have to serve `www` and `signaler` via HTTPS
```
./create-ssl-cert.sh
```
* Start a multi-conference
```
docker-compose up --build
```
* Open up https://localhost:5000/ After you share your webcam you have joined the conference.
