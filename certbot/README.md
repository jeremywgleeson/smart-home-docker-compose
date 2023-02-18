# certbot
Certbot will generate certs for your domain

renew certs with:
    docker compose run --rm certbot renew    
    
    docker-compose run --rm --entrypoint \
    "certbot certonly \
    --register-unsafely-without-email \
    --dns-cloudflare \
    --dns-cloudflare-credentials /secrets/certbot/cloudflare.ini \
    -d *.jeremygleeson.com \
    -d jeremygleeson.com \
    --rsa-key-size 4096 \
    --agree-tos \
    --force-renewal" certbot


Add cloudflare api key to `.secrets/certbot/cloudflare.ini` (path from project root) to allow dns challenge completion.