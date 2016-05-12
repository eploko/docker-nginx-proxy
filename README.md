# Docker NGINX Proxy

Clone this into a directory named `docker-nginx-proxy` and add a service definition in your `docker-compose.yml` like this:

```yaml
version: '2'
services:
  api:
    image: whatever:latest
    environment:
      VIRTUAL_HOST: api.whatever.dev
      VIRTUAL_PORT: 8080
    external_links:
      - dockernginxproxy_nginx-proxy_1
    networks:
      - proxy
    restart: unless-stopped
networks:
  proxy:
    external:
      name: dockernginxproxy_default
```
