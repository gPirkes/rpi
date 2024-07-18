# Setting up Home Assistant with RPI

## Running homeassistant as a container

First, [install docker](https://docs.docker.com/engine/install/debian/).

Followed [this guide](https://www.home-assistant.io/installation/raspberrypi-other).

```
mkdir -p ~/homeassistant/config

sudo docker run -d \
  --name homeassistant \
  --privileged \
  --restart=unless-stopped \
  -e TZ=Europe/Vienna \
  -v ~/homeassistant/config:/config \
  -v /run/dbus:/run/dbus:ro \
  --device=/dev/ttyUSB0 \
  --network=host \
  ghcr.io/home-assistant/home-assistant:stable
```