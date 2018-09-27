## Spin up a new vagrant box:

```
vagrant init ubuntu/xenial64
vagrant up
vagrant ssh
```

## Install Docker
**this doesn't need to be done separately as it's added as part of provisioner in vagrantfile**

```
sudo apt-get install -y docker.io
```

### Use docker run to start a container and execute a command

```
sudo docker run centos:7 /bin/echo 'Hello Docker'
```

### To launch an interactive container, the following command can be executed

```
sudo docker run -t -i ubuntu:14.04 /bin/bash
```
-i runs the container in interactive mode

/bin/bash starts the bash shell

the container will run untill we exit bash

### We can serve web page from inside a container

```
sudo docker run -p 127.0.0.1:8080:80 -i ubuntu:14.04 nc -kl 80
```

### Run index.js using docker build

```
docker build .
sudo docker run -p 8080:3000 -t <image>

```


## Install Docker Compose on Linux systems

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
[Reference](https://docs.docker.com/compose/install/#install-compose)

### Give permission to docker  and vagrant user

```
sudo chmod +x /usr/local/bin/docker-compose
usermod -G docker vagrant

```

## Run docker compose

```
docker-compose build && docker-compose up db

```

### Login to docker container if there is multi-VM environment error

```
vagrant ssh docker

```

## Start the application after database(mysql) is up and running

```
docker-compose up -d web

```

### Check if app is running and connected to db

```
curl http://localhost:3000

```

### Check dockerprocesses running

```
docker ps

```

## Bring the app and db down

```
docker-compose down

```

## Install docker machine

```
curl -L "https://github.com/docker/machine/releases/download/v0.14.0/docker-machine-$(uname -s)-$(uname -m)" >/usr/local/bin/docker-machine && chmod +x /usr/local/bin/docker-machine


```