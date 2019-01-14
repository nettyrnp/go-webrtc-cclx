# WebRtc-Cclx
WebRtc-Cclx is a minimal deploy with multi-conferencing functionality. It has a working signaler, TURN server and web app.

### Installing the environment
* Install Docker 
```
(see https://docs.docker.com/install/linux/docker-ce/ubuntu/)
```
* Install Docker-Compose
```
(see https://github.com/Yelp/docker-compose/blob/master/docs/install.md)
```
* Install Golang
```
(see https://golang.org/doc/install)
```
* Install WebRtc-Cclx source code
```
go get -u github.com/nettyrnp/go-webrtc-cclx
```

### How to launch the app
* Create an AWS (or GCP, Azure, Heroku...) 'instance' for hosting and running the application (WebRtc-Cclx). 

* Create an account at https://console.aws.amazon.com

* Copy intance ID and IP (e.g. '<intance_ID>=i-08323c3e2cb6e976f' and '<intance_IP>=34.227.15.123')

* [Optionally] Install aws console and check instance status using aws console: 
```
aws ec2 get-console-output --instance-id <intance_ID>
```

* Generate a pem key pair and connect to your instance:
```
(see https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

- Change the permissions of your private key:
chmod 400 /path/my_key_pair.pem

- Log into your instance via ssh:
ssh -i /path/my_key_pair.pem ec2-user@<intance_IP>
```

* Install the environment in your instance
```
Follow the instructions described in 'Installing the environment'
```

* Change a line in 'index.html'. Open it:
```
sudo nano ~/app/mygo/src/github.com/nettyrnp/go-webrtc-cclx/www/index.html
and change the line: const SIGNALER_URI = 'localhost:5001' --> const SIGNALER_URI = '<intance_IP>:5001'
```

* Launch the app:
```
cd ~/app/mygo/src/github.com/nettyrnp/go-webrtc-cclx
sudo /usr/local/bin/docker-compose up --build
```

* Generate your SSL certificates, WebRTC only works over HTTPS so we have to serve `www` and `signaler` via HTTPS
```
./create-ssl-cert.sh
```

* Start conferencing:
```
Open the page in Chrome at your PC/Mac ('doctor'): 
https://<intance_IP>:5000/

Open the page in Chrome at some other PC/Mac ('patient'): 
https://<intance_IP>:5000/
```

### How to launch the app LOCALLY (for test purposes)

* Generate your SSL certificates, WebRTC only works over HTTPS so we have to serve `www` and `signaler` via HTTPS
```
./create-ssl-cert.sh
```
* Launch the app
```
cd ~/app/mygo/src/github.com/nettyrnp/go-webrtc-cclx
docker-compose up --build
```
* Start conferencing (with yourself)
```
Open up https://localhost:5000/. After you share your webcam you have joined the conference. 
```

