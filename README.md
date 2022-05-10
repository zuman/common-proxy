# common-proxy
Common proxy for multiple websites on single server

## Run before docker compose up:

```
docker network create --attachable proxy-network
```

## Install certificates from [Let's Encrypt](https://letsencrypt.org/):

```
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx
```