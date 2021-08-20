docker
=====

Run a container with custom entrypoint

```
docker run -it --entrypoint /bin/bash {container}
```

With GPU support, 

```
docker run --gpus all -it --entrypoint /bin/bash {image}
```

If GPUs aren't working, try reinstalling Docker Nvidia support with [this recipe](https://gist.github.com/nathzi1505/d2aab27ff93a3a9d82dada1336c45041).
