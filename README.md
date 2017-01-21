# Node-RED for Raspberry Pi

Based on the [hypriot/rpi-node](https://hub.docker.com/r/hypriot/rpi-node/) image this Docker image provides a Node-RED installation
toghether with a list of plugins that are usefull when running on a Raspberry PI (SenseHat/Serial/Neopixel. etc)

## Running the image
The easiest way to run this image is to use [Hypriot OS](https://blog.hypriot.com/downloads/), with this OS you know 
you have a recent Docker version and that it works good on a Raspberry PI.

The image itself can be run with Docker compose: `docker-compose up -d`, Node-RED will then be available on port 1880.

## Building the image
The most recent version of the image is available on [Docker Hub](https://hub.docker.com/r/elzekool/rpi-nodered/) and building
is not needed. If you still want to build the image you can do that with `docker-compose build`.

