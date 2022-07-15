# Jupyter Foo
STATUS:  Work In Progress

## Install/Use using pip
```
pip install jupyterlab
```

## Run Jupyter as a container
At this point, I like the container option best
```
docker search jupyter 

docker run -p 10000:8888 jupyter/scipy-notebook:6b49f3337709
```

[Docker Stacks Documentation](https://jupyter-docker-stacks.readthedocs.io/en/latest/)  

https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html

## Using Podman (without sudo)
I create a $HOME/Notebooks directory on my machine

-- If you happen to run in to perms issues, run the following 
```
sudo su -
loginctl enable-linger my_ci_user
```
https://github.com/containers/podman/issues/9002

```
mkdir ${HOME}/Notebooks; cd $_
git clone https://github.com/NVIDIA-AI-IOT/jetbot.git

uid=1000
gid=100
subuidSize=$(( $(podman info --format "{{ range .Host.IDMappings.UIDMap }}+{{.Size }}{{end }}" ) - 1 ))
subgidSize=$(( $(podman info --format "{{ range .Host.IDMappings.GIDMap }}+{{.Size }}{{end }}" ) - 1 ))
#podman run -it --rm -p 10000:8888 \
podman run -it --rm -p 8888:8888 \
    -v "${HOME}/Notebooks":/home/jovyan/work --user $uid:$gid \
    --uidmap $uid:0:1 --uidmap 0:1:$uid --uidmap $(($uid+1)):$(($uid+1)):$(($subuidSize-$uid)) \
    --gidmap $gid:0:1 --gidmap 0:1:$gid --gidmap $(($gid+1)):$(($gid+1)):$(($subgidSize-$gid)) \
    docker.io/jupyter/r-notebook:6b49f3337709


```
browse to  
http://127.0.0.1:10000/lab


```
docker run -p 8888:8888 \
           -e JUPYTER_ENABLE_LAB=yes \
           -e JUPYTER_TOKEN=docker \
           --name jupyter \
           -d jupyter/datascience-notebook:latest
```
