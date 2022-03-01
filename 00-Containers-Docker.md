# Container concepts - Docker

Create your account in Docker Hub: https://hub.docker.com


## Installing Docker on Ubuntu

` sudo apt-get update `

`sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

`sudo apt-key fingerprint 0EBFCD88`

`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`

`sudo apt-get update`

`sudo apt-get install docker-ce docker-ce-cli containerd.io`

### Running hello-world docket container

`sudo docker run hello-world `


### After docker installation add your user id to docker group

` sudo usermod -aG docker mahendra`
` docker run hello-world ` 

Running hello-world docket container without sudo after adding your user id to docker group. You need to Logout and login for the group addition to be effective. OR start new shell with newgrp command. ` newgrp docker`



## Running Apache webserver in docker container

` mkdir -p /var/www/html                                                          `

` echo hello from docker >> /var/www/html/index.html                              `

` sudo sh -c "echo hello from docker >> /var/www/html/index.html"                 `

` docker run -d -p 8080:80 --name="myapache" -v /var/www/html:/var/www/html httpd `

### List docker containers which are running in this host:

` docker ps `

### Test apache webserver running on port 8080

curl http://localhost:8080


### Useful docker commands

- docker ps -a --> show currently running and past containers

- docker start --> start a container from a locally stored image

- docker stop --> stops a container using Linux SIGTERM

- docker restart --> restarts a currently running container.

- docker kill --> stops a container using Linux SIGKILL.

- docker rm --> removes all container files from the host OS.

- docker inspect <ID> | less

### Using JSON Path:

` docker inspect --format='{{.NetworkSettings.IPAddress}}' containername `
` docker inspect --format='{{.State.Pid}}' containername `

## Managing Images

- docker images    --> to get list of images
- docker image ls  --> same as above - to get list of images
- docker image --help
- docker image inspect <IMAGE-ID>

ctrl+p ctrl+q - to exit container without terminating the container


### docker commit

After making changes to a container, you can save it to an image using docker commit.
 
` docker commit -m "custom web server" -a "My user name" myapache myapache

## Copying docker image from one system to another system

Use "docker save -o myapache.tar myapache" and copy the tar file to any other system to import.

From another system, use "docker load -i myapache.tar" to import it as an image

