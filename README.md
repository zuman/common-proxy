# common-proxy
Common proxy for multiple websites on single server, with HTTPS enabled

## Steps

1. Create / Edit .conf files in proxy directory.
2. Create an attachable network
```
docker network create --attachable proxy-network
```
3. Create the stack
```
docker compose build
docker compose up -d
```
4. Dry run the certbot
```
docker compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run
```
> In case of error, remove ":arm64v8-latest" in line #17 of compose.yaml file.
5. Create the certificates by removing --dry-run from above command.