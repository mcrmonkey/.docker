# Firefox

... in a container

## Building

Run the following in this dir:

    docker build -t firefox .

## Running


For Just firefox in a container:

```
    docker run -d \
     --memory 2Gb \
     --net host \
     --cpuset-cpus 0 \
     -v /etc/localtime:/etc/localtime:ro \
     -v /tmp/.X11-unix/:/tmp/.X11-unix \
     -e GDK_SCALE \
     -e GDK_DPI_SCALE \
     -e DISPLAY \
     --device /dev/snd \
     --device /dev/dri \
     --name firefox \
      firefox --new-instance

```

If you want persistence map to the profile dir's with the extra options `-v $HOME/.mozilla:/home/firefox/.mozilla -v $home/.cache:/home/firefox/.cache`


