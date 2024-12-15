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


# Git Commands Cheat Sheet

## 1. Configuring Git

| Command                                         | Description                                    |
|------------------------------------------------|------------------------------------------------|
| `git config --global user.name "Your Name"`   | Sets your global username for Git.           |
| `git config --global user.email "your_email@example.com"` | Sets your global email for Git.            |
| `git config --list`                            | Displays your Git configuration.             |
| `git config --global core.editor [editor]`     | Sets your default editor (e.g., vim, nano).  |

## 2. Initialize a Repository

| Command            | Description                                    |
|--------------------|------------------------------------------------|
| `git init`         | Initializes a new Git repository in the current directory. |

## 3. Clone a Repository

| Command                           | Description                                    |
|-----------------------------------|------------------------------------------------|
| `git clone [URL]`                 | Downloads a repository to your local machine. |
| `git clone [URL] [folder_name]`   | Clones a repository into a specified folder.  |

## 4. Viewing Repository Status

| Command      | Description                                    |
|--------------|------------------------------------------------|
| `git status` | Shows the status of your repository (staged, unstaged, untracked files). |

## 5. Adding Changes

| Command       | Description                                    |
|---------------|------------------------------------------------|
| `git add [file]` | Stages a specific file.                     |
| `git add .`      | Stages all files in the current directory.  |

## 6. Committing Changes

| Command                      | Description                                    |
|------------------------------|------------------------------------------------|
| `git commit -m "message"`  | Commits staged changes with a message.        |
| `git commit -a -m "message"`| Stages and commits all tracked changes in one step. |
| `git commit --amend`         | Modifies the most recent commit.              |

## 7. Pushing Changes

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git push`                             | Pushes changes to the remote repository (default branch). |
| `git push origin [branch]`             | Pushes changes to a specific branch.          |
| `git push -u origin [branch]`          | Pushes changes and sets upstream branch for future pushes. |

## 8. Pulling Changes

| Command                         | Description                                    |
|---------------------------------|------------------------------------------------|
| `git pull`                      | Fetches and merges changes from the remote repository. |
| `git pull origin [branch]`      | Pulls changes from a specific branch.         |

## 9. Branch Management

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git branch`                           | Lists all branches.                          |
| `git branch [branch_name]`             | Creates a new branch.                        |
| `git checkout [branch_name]`           | Switches to a specific branch.               |
| `git checkout -b [branch_name]`        | Creates and switches to a new branch.        |
| `git branch -d [branch_name]`          | Deletes a branch.                            |
| `git branch -D [branch_name]`          | Deletes a branch forcefully.                 |
| `git merge [branch_name]`              | Merges another branch into the current branch. |

## 10. Undoing Changes

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git restore [file]`                   | Discards changes in a working directory.      |
| `git restore --staged [file]`          | Unstages a file.                              |
| `git reset [file]`                     | Removes a file from the staging area.         |
| `git reset --hard`                     | Resets the working directory and staging area to the last commit. |
| `git reset [commit]`                   | Resets to a specific commit.                 |
| `git revert [commit]`                  | Creates a new commit that undoes the changes of a specific commit. |

## 11. Viewing Changes

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git diff`                             | Shows differences between working directory and staged changes. |
| `git diff [branch]`                    | Compares your current branch with another branch. |
| `git diff [commit1] [commit2]`         | Shows differences between two commits.        |
| `git log`                              | Displays the commit history.                  |
| `git log --oneline`                    | Shows a compact version of the commit history. |

## 12. Stashing Changes

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git stash`                            | Saves changes for later and reverts to the last commit. |
| `git stash list`                       | Lists all stashed changes.                    |
| `git stash apply`                      | Reapplies the most recent stashed changes.    |
| `git stash drop`                       | Deletes the most recent stash.                |

## 13. Tagging

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git tag [tag_name]`                   | Creates a new tag.                            |
| `git tag -a [tag_name] -m "message"` | Creates an annotated tag.                    |
| `git tag`                              | Lists all tags.                               |
| `git push origin [tag_name]`           | Pushes a tag to the remote repository.        |

## 14. Fetching Updates

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git fetch`                            | Downloads changes from the remote repository without merging. |
| `git fetch origin [branch]`            | Fetches changes for a specific branch.        |

## 15. Remote Repositories

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git remote -v`                        | Lists the remote repositories.               |
| `git remote add [name] [URL]`          | Adds a new remote repository.                |
| `git remote remove [name]`             | Removes a remote repository.                 |

## 16. Working with Submodules

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git submodule add [URL]`              | Adds a submodule to your repository.         |
| `git submodule update --init`          | Initializes and updates submodules.          |
| `git submodule deinit -f [submodule_path]` | Removes a submodule.                       |

## 17. Advanced Commands

| Command                                | Description                                    |
|----------------------------------------|------------------------------------------------|
| `git rebase [branch]`                  | Reapplies commits on top of another branch.  |
| `git cherry-pick [commit]`             | Applies changes from a specific commit.      |
| `git bisect`                           | Used to find the commit that introduced a bug. |
| `git reflog`                           | Displays the reference history.              |
