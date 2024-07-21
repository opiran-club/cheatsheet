

# To search for an installed package, yum search package_name
#yum search docker

# To install a package, yum install package_name
#yum install docker
Then we need to start the service of Docker. 
#systemctl start docker
#systemctl enable docker

# To check the status of the Docker service, run systemctl status docker.
The machine on which we installed Docker is called Docker host. 

# To search for an image on hub.docker.com, run docker search image_name.
For eg: I want to search for Ubuntu. 
#docker search ubuntu (it will display all the images related to ubuntu)

# To search for a particular version of image, run docker search image_name:version number
For eg: #docker search ubuntu:17.4

# To download an image from hub.docker.com, run docker pull image_name
For eg: #docker pull ubuntu

# To display installed images, run docker images.

# To remove an image from your machine, run docker rmi image_name
For eg: #docker rmi hello-world

# To create a container, run docker run --name container_name os

For eg: docker run --name c1 –it centos bash(bash shell will be default so not necessary to mention)
	-i – it means we need an interactive container 
	-t – it means we need a shell to run commands in the container

# To check more options of creating a container, run docker container --help

# To check for active containers, run docker ps
# Show all containers, run docker ps –a

# docker ps –q (only display container id)

# docker ps –s (display container details with size used)

# To provide interactive mode with a terminal in a container, use docker run --name container_name –it (-i is Interactive mode and –t is terminal)
For eg: #docker run –-name first-cont –it centos

# To exit out of a container shell, press Ctrl+p then q

# To check live, resources used by containers, run docker stats

# To install a new package in Ubuntu, run apt update then apt upgrade then apt install pkg_name.

For eg: I want to install vim.
apt update (update list of available packages)
		apt upgrade (upgrade the system by installing/upgrading packages)
		apt install vim (install vim package)


# To go inside a container, run docker exec –it container_name or container_id shell_name(bash, etc) (-i is Interactive mode and –t is terminal)

#docker exec –it c4 or 78e64dac91d9 bash (go will go inside the container c4 with the help of command exec –it and the shell bash)

# Check IP address of a container on which ip a command is not installed, run hostname –i 


# To check installed repos in your system, run yum repolist

# Display low-level information on an image, run docker inspect image_id or image_name:version_no.

# To check SHA value of any file, run md5sum file_name 

# To remove a running container with processes, run docker rm –f container_name (-f will forcefully remove the container)

# View all/top processes running in the system, run top

# Create a container in background, run docker run –-name c1 –itd ubuntu bash (-d will create the container in detach mode and the contain will start in background)

# Connect to a container via bash shell, run docker attach container_name

# View a process of a particular container, run docker top container_name

# Create a container in bg with httpd service, run docker run --name web1 –d httpd (-d will run the container in background/detach mode)

# Access an httpd container, run docker exec –i container_name bash
Httpd container will by default open in /usr/local/apache2 directory.

Files of httpd are stored in:
/var/www/html
Files of apache2 are stored in:
/usr/local/apache2/htdocs

# curl http://ip_address (this will print the contents stored at the ip_address)

Command line browser
#elinks

#yum install elinks (This will install elinks in your system) 

#elinks https://www.google.com (this will open google.com in a browser type display on the terminal)


Copy files from local machine to container and vice-versa

#docker cp source destination

#docker cp index.html c1:/root (index.html – source file in current dir, -c1:/root container c1; dir /root)
PORT FORWARDING
-p ip:hostport:container_port image_name

Command: 
#docker run --name web2 –d –p 8080:80 httpd (this will create a new container named web2 with application httpd, -d for detach mode, -p is for port forwarding, 8080: is hostPort and :80 is containerPort)

Now we can connect to this container using the port number.

NESTED CONTAINER (docker service running in containers as well)

To create a nested container with docker running it in, use the below command:

#docker run --name c3 –itd docker (this will create a new container c3, -i for interactive, ¬-t for pseudo tty, -d for detach mode, docker to create container with docker image)


#docker rmi img_name (to delete a docker image)
	Use -f for force delete img if in-use by a container.

#docker build -t avnimahesh95/centos(user_name/img_name) path_of_dockerfile

#docker login (to login to docker hub)

#docker push avnimahesh95/centos(user_name/img_name) this will push the img from local machine to hub.docker.com

#docker pull avnimahesh95/centos(user_name/img_name) this will pull the img from hub.docker.com to local machine

#docker run --name c1 -v new_vol/vol_path_for_mapping --hostname -itd centos
(this will create a vol named “new_vol” and will map that vol to the path, and will create a container “c1” in that vol_path and will run centos in it)

#docker -H <ip_address_of_docker_remote_machine>:<port_number> -d <image_name> (run this command remotely on a docker host, -H is the IP addr of remote host on which Docker is installed, :<port> which is exposed, -d for detach mode and <image_name>. )
 
Cgroups 

#docker run --cpus=.5 --memory=100m -itd <image_name> (this will apply cgroup limits --cpu will use only half of 1 cpu, --memory will alot only 100m) 


Build Centos and Ubuntu images from a Dockerfile. 
How to setup an ssh server within a docker container - DEV Community – Ubuntu image
Centos image:
 
#docker build -t <docker_ac_user_name/image_name> <image_path>
#docker build -t avnimahesh95/centos-ansible . (this will read the Dockerfile from (.) current dir and will create a Centos image)

Ubuntu image:
  
#docker build -t avnimahesh95/ubuntu-ansible . (this will read the Dockerfile from (.) current dir and will create an Ubuntu image)

Create containers with these images:
#docker run -itd --name <cont_name> --hostname <cont_host_name> --network <netw_name> <image_name>
#docker run -itd --name host1 --hostname host1.example.com --network ansible avnimahesh95/ubuntu-ansible
Listing IP Addresses of all Containers in a Docker Compose

#docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq) (this will print ip addresses of all the containers with their names)


Sharing Network namespace among containers

Similar to host, we can share network namespaces among containers. As a result, two or more containers can share the same network stack and reach each other through localhost.
Let's run a new container and retrieve its IP address:
$ docker container run -it --name=c5 busybox /bin/sh
: eth0@if11: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue
    link/ether 02:42:ac:11:00:03 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.3/16 scope global eth


Now, if we start a new container with the --net=container:CONTAINER option, the second container will show the same IP address.
$ docker container run -it --name=c6 --net=container:c5 busybox /bin/sh
/ # ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
12: eth0@if13: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue
    link/ether 02:42:ac:11:00:03 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.3/16 scope global eth0


#docker logs container_name 


Deploy containers using env variables

#docker run --name c1 -d -e APP_COLOR=pink -e MYSQL_ROOT_PASSWORD=db_pass123 <image_name>

{-e refers to environment variables}







# Commands vs. Entrypoints




Differ bw CMD in Dockerfile and ENTRYPOINT in Dockerfile

#docker run <image_name> <args> {here the args is value given for the CMD or the ENTRYPOINT in the Dockerfile.}


To run a container with a sleep command metioned in the Dockerfile in Entrypoint command:

#docker run ubuntu 10 {10 is the number of sleep seconds}


If you don’t want to specify command or args while deploying a container, mention the command and args in the Dockerfile.

ENTRYPOINT [“sleep”] {this is the command which will be run when the container starts and the format of the command is json.}

CMD [“5”] {this is the args for the sleep commands if you don’t want to mention the number of seconds as well. This is also written in json format}

If you wish to deploy container with another command than the one in Dockerfile then do:
#docker run --entrypoint <command_name> <container_image> <cmd_args>
#docker run --entrypoint sleep2.0 ubuntu-sleeper 10


# DOCKER COMPOSE 

After launching two different containers, you can link them together using --link option while launching a container.

--link <container_name:host_name>
#docker run -d --name=vote -p 5000:80 --link redis:redis <image_name>


Create a docker-compose.yml file to use it to bring up the application stack.

#docker-compose up {this is used to bring the whole application stack up)


When using Version 2 format, specify version: 2  at the top of the docker-compose.yml file.

The links:  option is no longer required in version 2 and version 3 formats.

You can also priorities Applications. If app A is dependent on app B, then:

you can write- depends_on:
					- app B 
in the metadata of app A  in the compose.yml file. 

Version 3 uses Docker Swarm. 


# Networking within applications

First add networks: map at the root level in the compose.yml file and then under each services, create a networks property and provide a list of networks you wish the application to connect to.

Mention the networks in all the applications and you are good to go. 


Docker-compose.yml

Version: 2 
Services:
	redis:
		image: redis
		networks: 
			- front-end
			- back-end


Networks:
	front-end:
	back-end: 






DOCKER-COMPOSE.YML file

redis:
image: redis
container_name: redis

db:
image: postgres:9.4
environment:
POSTGRES_PASSWORD: postgres
container_name: db 

vote:
image: voting-app
container_name: voting-app
ports:
- 5000:80
links:
- redis

worker:
image: worker-app
container_name: worker-app
links: 
- db 
- redis

result:
image: result-app
container_name: result-app
ports:
- 5001:80 
links: 
- db

First create a docker-compose.yml file, with the necessary services, ports, links properties and then run the command:
#docker-compose up (run this command in the same dir where the docker-compose.yml file is kept)

The command will run all the containers with necessary properties.



# RUN AWS INSTANCE WITH COMMANDS

In the User data field on the configure Instance page, 

write a bash script with all the commands.

#!/bin/bash

yum install docker -y 
systemctl enable --now docker
yum install vim -y
yum install httpd

These commands will be installled and configured on your new EC2 Instance. 


Run Docker from a remote host

#docker -H=remote-docker-engine:2375 

Run an Nginx container on a remote docker host:

#docker -H=10.123.2.1:2375 run nginx (-H is the remote host) 


To limit resource use by a container: (CGROUP)

#docker run --cpu=0.5 ubuntu (this will launch a container with <ubuntu_image> and the container will only use 50% of cpu) 

#docker run --memory=100m ubuntu (this will launch a container with <ubuntu_image> and the container will only use 100mb of memory) 


MOUTING A CONTAINER WITH A VOLUME

Volume Mounting:

#docker run -v data_volume:/var/lib/mysql <image_name> (here -v specifies the volume to be mounted with the path inside the container)

Bind Mounting:

#docker run -v /data/mysql:/var/lib/mysql <image_name> (this is called bind mounting. It mounts a dir on the host system to the path inside the container)

New Mounting options

--mount 

#docker run --mount type=bind,source=/data/mysql,target=/var/lib/mysql <image_name> 

Here we specify, the mount type --mount type=bind



Networking in Docker

By default, docker creates 3 networks:
1. Bridge (private network – 172.17.0.1-0.254)
2. None, and
3. Host

#docker run ubuntu (it will attach the container to Bridge network by defautl)

To specify a network:

#docker run --network=host ubuntu 

#docker run --network=none ubuntu 


# Create a Network

#docker network create --driver bridge --subnet 182.18.0.0/16 <network_name> 

#docker network ls 


