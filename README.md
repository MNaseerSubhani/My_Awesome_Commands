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
sudo docker run -it --device /dev/video0 -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:ro --rm --runtime nvidia  --network host container name
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
```
