# Docker usage

1. Dockerfile itself:

    FROM ubuntu:latest
    
    RUN apt-get update -y
    
    RUN apt-get install -y gcc make check lcov valgrind
    
2. Create image with your “image_name”

`**docker build** --tag "image_name" .`

3. Remove all containers:

`docker rm -v -f $(docker ps -qa)`

-f:  flag for remove also running containers
4. Remove container:

`docker rm “container_name”`

5. Remove image:

`docker rmi “image_name”`

6. Create and run container (without going into container shell, just running):

`docker run --name “container_name” -d -i -t “image_name” /bin/sh`

This creates and starts a container named `“container_name”` from an `“image_name”` image
with an `sh` shell as its main process. The `-d` option (shorthand for `--detach`)
sets the container to run in the background, in detached mode, with a pseudo-TTY
attached (`-t`). The `-i` option is set to keep `STDIN` attached (`-i`), which
prevents the `sh` process from exiting immediately.

7. Start existed docker container:

`docker start “container_name”`

8. Stop existing docker container:

`docker stop “container_name”`

9. Go into container shell:

`docker exec -it “container_name” bash`

10. Create and run container with binding a mount with local (PWD) files to use them inside the container shell in src folder:

`docker run --name “container_name” -it --mount type=bind,src="$(pwd)",target=/src “image_name” bash`

11. Escape from container shell:

`exit`