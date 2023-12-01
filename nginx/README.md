# nginx
Nginx is our reverse proxy, allowing us to easily create routing rules and expose our other services over http

This config sets up nginx as a proxy in front of our services and gates access to services so they are not exposed to the web. Services are set up using a subdomains, so `homeassistant.jeremygleeson.com` will route to the home assistant container etc.

Internal services are accessible on the local network, or through the wireguard vpn.

Shoutout to `oddlama` for finding a [fix](https://github.com/esphome/issues/issues/2677#issuecomment-1474520959) for esphome's issues with nginx `Host` header.
