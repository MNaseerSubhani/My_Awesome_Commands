# My_Awesome_Commands
This repo contains  the commands that i need to use in future. 



# split data from file name's .txt
 ```
cat file.txt | xargs -n 1 -d'\n' -I {} mv ./source/{} target/
 ```
 
 # check service status in ubuntu
 ```
 systemctl status service-name
 ```


# For Documentatiomn
```
sudo apt install python-sphinx -y
tree -L 3                              #for directory tree
sphinx-quickstart
sphinx-apidoc -o . ..
make html                              # to convert in html format
sudo pip install sphinx_rtd_theme
```
# pyTorch and tf with docker 
```
FROM nvcr.io/nvidia/l4t-pytorch:r32.6.1-pth1.9-py3   or NVIDIA L4T ML

sudo docker build -t "container name"
xhost local:root      # to add docker root in local
sudo docker run -it --device /dev/video0 -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --rm --runtime nvidia --privileged  --network host container name
```
# Docker commands
```
docker build -t image/name .   # . is the current folder 
docker run image/name
docker ps 
docker ps -a    # all containers
docker  run image/name: latest     #  version as container
docker run -d image/name           # -d is for detach and run the container in background
docker attach image/name           # attach container 
docker rmi -f container-id         # delete container , -f is forced
docker login
docker tag image:template    image/tag
docker push image/name
docker system prune     # delete all stopped docker images

# Push docker image
docker login
docker tag local-image:tag  hub-image:tag
docker push hub-image:tag
```
#### Build and run multi-architecture images
```
docker buildx ls
docker buildx create --name mybuilder

docker buildx use mybuilder
docker buildx inspect --bootstrap

#Test the workflow to ensure you can build, push, and run multi-architecture images. Create a simple example Dockerfile, build a couple of image variants, and #push them to Docker Hub.

#The following example uses a single Dockerfile to build an Ubuntu image with cURL installed for multiple architectures.

FROM ubuntu:20.04
RUN apt-get update && apt-get install -y curl

#build the docker
docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 -t username/demo:latest --push .

#test the image
docker buildx imagetools inspect username/demo:latest
```

#### create a base image from host
```
$ sudo debootstrap focal focal > /dev/null
$ sudo tar -C focal -c . | docker import - focal

sha256:81ec9a55a92a5618161f68ae691d092bf14d700129093158297b3d01593f4ee3

$ docker run focal cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS"
```
# NoMachine for jetson
[Jetson](https://www.nomachine.com/download/download&id=116&s=ARM)

# Git 
```
before merge pull main branch





```
# Display
```
xrandr --fb 1920x1080    # to focefully adjust the display resolution, without a monitor , ubuntu

```
# Port forward React with flask 
```
run npn eject 

#In config/path.js change
appBuild: resolveApp("../backend/static/react"),

# in config/webpack.config.js remove "static/" and add
new HtmlWebpackPlugin(
    Object.assign(
      {},
      {
       ...
        filename : path.resolve("../backend/templates/index.html")
      },
      
# in package.js add 
...
"private": true,
"homepage": "/static/react",
```


```
npm install # to install required packages
npm run build   # to build the files
```


# update Node js to latest version
```
sudo npm cache clean -f
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash   # install vnm
source ~/.nvm/nvm.sh
command -v nvm
nvm install 16.13.1
```
# Set python to default version
```
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 1     
```