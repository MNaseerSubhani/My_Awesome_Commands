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
# pyTorch with docker 
```
FROM nvcr.io/nvidia/l4t-pytorch:r32.6.1-pth1.9-py3   or NVIDIA L4T ML

sudo docker build -t "container name"
sudo docker run -it --rm --runtime nvidia --network host "container name"
```
