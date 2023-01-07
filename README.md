# Home Assistant Docker Setup
Home assistant docker setup with:
- homeassistant
- portainer
- mosquitto
- nodered
- cloudflared
- esphome
- avahi


## Setup
Most setup is going to be container-specific. For example, adding an admin user to portainer, nodered, and mosquitto are all things you should do, but the process is different for each. If there are specific notes about migrating, they will be included in the readme for that service. Otherwise, please consult the documentation for the image.

### homeassistant
[homeassistant](homeassistant/README.md)

### portainer
[portainer](portainer/README.md)

### mosquitto
[mosquitto](mosquitto/README.md)

### nodered
[nodered](nodered/README.md)

### cloudflared
To set up cloudflared, you need a cloudflare account.

In order to use cloudflare tunnels, the env var `CLOUDFLARE_TUNNEL_TOKEN` should be populated in `.env` in the project root.

Once you set your tunnel token, you can add tunnels:
- `homeassistant.your-domain.com` -> http://homeassistant:8123
- `portainer.your-domain.com` -> http://portainer:9000
- `nodered.your-domain.com` -> http://nodered:1800

### esphome
[esphome](esphome/README.md)

### avahi
We're using avahi to reflect mdns on our local network to a docker network. This is so esphome can find esp's which create mdns entries.  
If the server is shut down, avahi will break. You can fix this with:
```
docker rm -v mdns-reflector
```