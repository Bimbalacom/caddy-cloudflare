# Bimbala's Cloudflare Caddy container

Please see the [Caddy Docker Image](https://hub.docker.com/_/caddy) for deployment instructions.

Structure / idea is forked from [Caddy community](https://caddy.community/t/how-to-guide-caddy-v2-cloudflare-dns-01-via-docker/8007). 

You can obtain your API token from the Cloudflare Portal. 
1. To create a API token:

   1. Log into your dashboard, go to account settings, create API token
   2. grant the following permissions:

      * Zone / Zone / Read
      * Zone / DNS / Edit
      
2. You should add the following to your Caddyfile as the [tls directives](https://caddyserver.com/docs/caddyfile/directives/tls#tls). 

   ```
   tls {$CLOUDFLARE_EMAIL} { 
     dns cloudflare {$CLOUDFLARE_API_TOKEN}
   }
   ```
   
3. Add the following to your environment file (env):

   ```
    CLOUDFLARE_EMAIL=me@example.com 
    CLOUDFLARE_API_TOKEN=12345 
    ACME_AGREE=true
   ```
