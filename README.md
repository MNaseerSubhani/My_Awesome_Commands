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
sudo npm install -g n
sudo n stable
```
