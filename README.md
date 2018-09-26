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

