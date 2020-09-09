# laba 11 Install docker, run images, create image

### Check your version docker: 
`docker --version`
`sudo systemctl status docker`
`docker info`

#### Run docker without sudo:
- check if docker group exists: cat /etc/group | grep docker; 
- if it doesn't, create with this command: sudo groupadd docker
- add the current user to docker group: sudo usermod -a -G docker $USER; ($USER it's a local varible); to check your user: cat /etc/group | grep docker
- logout, and login again: exit

#### Main commands for docker
- docker ps
- docker ps -a
- docker images
- docker search tomcat; (or other image)
- docker pull tomcat
- docker run -it -p 8080:8080 tomcat; -it, interactive mode
- docker run -it -p 8888:80 nginx
- docker run -d -p 8888:80 nginx; -d, daemonized container
- docker volume ls; list of volumes
- docker rm; delete container
- docker rmi; delete image
- docker rm -f $(docker ps -aq); delete all Containers
- docker rmi -f $(docker images -q); delete all Images