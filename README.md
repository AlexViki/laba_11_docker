# laba 11 Install docker, run images, create image

### Check your version docker: 
`docker --version`
`sudo systemctl status docker`
`docker info`

### Stop all running containers:
`docker stop $(docker ps -a -q)`

### Delete all unrunning containers:
`docker rm <your-image-id>`
`docker rm $(docker ps -a -q)`

### To remove the image:
`docker rmi <your-image-id>`

### Remove multiple images:
`docker rmi <your-image-id>`
`docker rmi $(docker images -q)`

`docker ps -a --format "table {{.ID}}\t{{.Image}}\t{{.CreatedAt}}\t{{.Names}}"`

### Docker run vs start
`docker run = docker create + docker start + docker attach`

#### Run bash in container
`docker exec -it 92598c51c879 bash`

### Connect CLI to created container
`docker attach 92598c51c879`
Disconnect from container: Ctrl + p, Ctrl + q

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


## 2
`export GOOGLE_PROJECT=learn-docker`

`docker-machine create --driver google --google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts --google-machine-type n1-standard-1 --google-zone europe-west3-c --google-project learn-docker docker-host-web`

### Check the list of created containers
`docker-machine ls `

### switching between containers in GCP Cloud via:
`eval $(docker-machine env docker-host)` - in GCP
`eval $(docker-machine env --unset)` - local docker

### Delete:
`docker-machine rm <name>`

