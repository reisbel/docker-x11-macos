# docker-x11-macos
Run X11 apps in Docker in macOS

Based on [this tutorial](https://techsparx.com/software-development/docker/display-x11-apps.html)
## Requirement

- https://www.xquartz.org/

## Steps

1.- Get Ip address

```bash
export IP=$(ifconfig en0 | grep inet | awk '$1=="inet" {print $2}')
```

2.- Open XQuartz

3.- Execute docker

```bash
xhost +$IP
$ docker run --rm  --name firefox -e DISPLAY=$IP:0 -e XAUTHORITY=/.Xauthority --net host -v /tmp/.X11-unix:/tmp/.X11-unix -v ~/.Xauthority:/.Xauthority  jess/firefox
```

4.- Running the below command we get Firefox for Ubuntu displaying on a Mac OS X desktop.

```bash
xhost +local:docker
```
