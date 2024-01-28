# common-proxy
Common proxy for multiple websites on single server, with HTTPS enabled

## Steps

* Create / Edit .conf files in proxy directory.
* Run the stack
    ```
    docker compose down
    docker compose up -d
    ```
* Dry run the certbot
    ```
    docker compose run --entrypoint certbot --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --agree-tos -n -m <YOUR_EMAIL> -d <DOMAIN> --dry-run
    ```
    > In case you are using arm processor, add "arm64v8-latest" tag in <b>certbot > image</b> section of compose.yaml file.
* Create the certificates by removing --dry-run from above command.

## For the service using this common-proxy

* In your compose.yaml file
    * Add the network `common-proxy_default` to the service you want to expose to the proxy.
        ```
            networks:
            - common-proxy_default
        ```
    * Also declare it as external network
        ```
        networks:
        common-proxy_default:
            external: true
        ```
