# Home Assistant Docker Setup
Home assistant docker setup with:
- Smart home services
    - esphome
    - homeassistant
    - mosquitto
    - nodered
- Infrastructure
    - avahi
    - certbot
    - cloudflare-ddns
    - nginx
    - pihole
    - portainer
    - wireguard

## Setup
Most setup is going to be container-specific. For example, adding an admin user to portainer, nodered, and mosquitto are all things you should do, but the process is different for each. If there are specific notes about migrating, they will be included in the readme for that service. Otherwise, please consult the documentation for the image.

## Services
### Smart Home

#### esphome
[esphome](esphome/README.md)

#### homeassistant
[homeassistant](homeassistant/README.md)

#### mosquitto
[mosquitto](mosquitto/README.md)

#### nodered
[nodered](nodered/README.md)

### Infrastructure
#### avahi
We're using avahi to reflect mdns on our local network to a docker network. This is so esphome can find esp's which create mdns entries.  
If the server is shut down, avahi will break. You can fix this with:
```
docker rm -v mdns-reflector
```

I've found that some of my esps do not transmit mdns except for when they are powered on. These devices often show up as unavailable, and I have yet to find a resolution to this issue.

#### certbot
[certbot](certbot/README.md)

#### cloudflare-ddns
To set up cloudflare-ddns, you need a cloudflare account. Follow setup in container documentation: https://hub.docker.com/r/oznu/cloudflare-ddns/

In order to use cloudflare ddns with certbot, add a file at `.secrets/certbot/cloudflare.ini` with the following:
```
dns_cloudflare_api_token = YOUR_CLOUDFLARE_API_TOKEN
```

If your isp uses a CGNAT and you have no public ip, you can use tunnels instead of DDNS to expose services. There is a sample `cloudflared` service, but you will need some manual setup to expose your services. Setting up a wildcard tunnel for `*.your-domain.com` -> `https://nginx` should work. (If you use this setup please PR with what worked for you.)

#### nginx
[nginx](nginx/README.md)

#### pihole
[pihole](pihole/README.md)

**NOTE:** If you use pihole, make sure you update your router's DNS to point to the machine running the project.

#### portainer
[portainer](portainer/README.md)

## Secrets
A `.env` file should contain:
```
CLOUDFLARE_DNS_TOKEN=CLOUDFLARE_API_TOKEN

PIHOLE_WEB_PASSWORD=YOUR_DESIRED_PASSWORD
```
The cloudflare dns token should also be provided to certbot for the dns challenge (see [certbot](###certbot))
