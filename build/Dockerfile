FROM hypriot/rpi-node:7.4
MAINTAINER Elze Kool <info@kooldevelopment.nl>

# Install Node-RED Globally
RUN npm install -g node-red

# Install GPIO/SenseHat tools
RUN apt-get update \
 && apt-get install -y \
         python-rpi.gpio raspi-gpio wiringpi python-sense-hat sense-hat \
 && rm -rf /var/lib/apt/lists/*

# Install generic extension for Node-RED
RUN npm install -g node-red-dashboard \
 && npm install -g node-red-node-feedparser \
 && npm install -g node-red-node-base64

# Install service based extensions for Node-RED
RUN npm install -g node-red-node-email \
 && npm install -g node-red-node-weather-underground \
 && npm install -g node-red-contrib-amqp

# Install hardware extensions for Node-RED
RUN npm install -g node-red-node-pi-sense-hat \
 && npm install -g node-red-node-serialport --unsafe-perm --build-from-source \
 && npm install -g node-red-node-pi-neopixel

# Install NeoPixel python library
RUN buildDeps='build-essential python-dev git scons swig' \
 && set -x \
 && apt-get update && apt-get install -y $buildDeps --no-install-recommends \
 && rm -rf /var/lib/apt/lists/* \
 && cd / \
 && git clone https://github.com/jgarff/rpi_ws281x.git \
 && cd rpi_ws281x \
 && scons \
 && cd python \
 && sudo python setup.py install \
 && apt-get purge -y --auto-remove $buildDeps \
 && cp /rpi_ws281x/python/neopixel.py /usr/local/lib/python2.7/dist-packages/neopixel.py \
 && rm -rf /rpi_ws281x

# Create volume for Node-RED storage
VOLUME /root/.node-red/

# Expose port 1880
EXPOSE 1880

# Setup start command
CMD node-red-pi --max-old-space-size=256
