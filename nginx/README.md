# nginx
Nginx is our reverse proxy, allowing us to easily create routing rules and expose our other services over http

This config sets up nginx as a proxy in front of `homeassistant` and `portainer` over http. If you're port forwarding to your host, you should use ssl. Forgoing https here is a shortcut, you should use it so that local traffic is encrypted. Because we're using a cloudflare tunnel to expose our site, external traffic uses ssl (external -> cloudflare -> cloudflared -> nginx -> ha/portainer).