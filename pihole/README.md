# pihole
We use pihole here as a dns to block ads, but also add a custom dns entry so that dns requests to our domain resolve to our local server instead of global ip. This makes local-only services work and means that if our ISP connection is down, we can still access all our services.

You can also add a wildcard DNS entry for your domain in pihole pointing to the ip of the machine running it (add DHCP reservation too). This prevents requests to anything in this stack from leaving your local network, instead being routed to the local ip of your server. (This means lower latency and the ability to access your services during an ISP outage!)
