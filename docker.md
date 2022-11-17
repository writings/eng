docker
=====

### Run with custom entrypoint

Run a container with custom entrypoint

```
docker run --rm -it --entrypoint /bin/bash {container}
```

With GPU support, 

```
docker run --rm --gpus all -it --entrypoint /bin/bash {image}
```

### NVidia Container Toolkit 

If docker can't run with GPU capabilities, eg. 

```
docker: Error response from daemon: could not select device driver "" with capabilities: [[gpu]].
```

Install the container toolkit: 

```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit

sudo systemctl restart docker
```

From [this recipe](https://gist.github.com/nathzi1505/d2aab27ff93a3a9d82dada1336c45041) 
([also](https://www.server-world.info/en/note?os=Ubuntu_22.04&p=nvidia&f=2)).
