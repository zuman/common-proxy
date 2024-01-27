# common-proxy
Common proxy for multiple websites on single server, with HTTPS enabled

## Steps

1. Create / Edit .conf files in proxy directory.
2. Run the stack
```
docker compose down
docker compose up -d
```
3. Dry run the certbot
```
docker compose run --entrypoint certbot --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --agree-tos -n -m <YOUR_EMAIL> -d <DOMAIN> --dry-run
```
> In case you are using arm processor, add "arm64v8-latest" tag in <b>certbot > image</b> section of compose.yaml file.
4. Create the certificates by removing --dry-run from above command.