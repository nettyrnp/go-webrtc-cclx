# WebRtc-Cclx
WebRtc-Cclx is a minimal deploy with multi-conferencing functionality. It has a working signaler, TURN server and web app.

### Prerequisits
* Create an AWS (or GCP, Azure, Heroku...) 'instanse' for hosting and running the application (WebRtc-Cclx). 
- Create an account at https://console.aws.amazon.com

- Copy intance ID and IP (e.g. '<intance_ID>=i-08323c3e2cb6e976f' and '<intance_IP>=34.227.15.123')

- [Optionally] Install aws console and check instanse status using aws console: 
aws ec2 get-console-output --instance-id <intance_ID>

- Generate a pem key pair and connect to your instance:
```
(see https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

- Change the permissions of your private key:
chmod 400 /path/my_key_pair.pem

- Log into your instance via ssh:
ssh -i /path/my_key_pair.pem ec2-user@<intance_IP>

- Follow the instructions described in 'Installing the environment'

- Follow the instructions described in 'Running WebRtc-Cclx'

- Open 'index.html' file:
sudo nano ~/app/mygo/src/github.com/nettyrnp/go-webrtc-cclx/www/index.html
and change this line it it: const SIGNALER_URI = 'localhost:5001' --> const SIGNALER_URI = '<intance_IP>:5001'

- Go to 'go-webrtc-cclx' folder:
cd ~/app/mygo/src/github.com/nettyrnp/go-webrtc-cclx

- Launch the app:
sudo /usr/local/bin/docker-compose up --build

- Open the page in Chrome on your PC/Mac ('doctor'): 
https://<intance_IP>:5000/

- Open the page in Chrome on some other PC/Mac ('patient'): 
https://<intance_IP>:5000/

```

### Installing the environment
* Install Docker 
```
(see https://docs.docker.com/install/linux/docker-ce/ubuntu/)
```
* Docker-Compose
```
(see https://github.com/Yelp/docker-compose/blob/master/docs/install.md)
```
* Install Golang
```
(see https://golang.org/doc/install)
```
* Install WebRtc-Cclx
```
```
go get -u github.com/nettyrnp/go-webrtc-cclx

### Running WebRtc-Cclx

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
