# Docker Registry

Docker registry image for https://github.com/geniusrabbit/registry

    @license Apache-2.0

## Environment

```sh
REGISTRY_DNS=http://registry:8500/dc1?refresh_interval=5
```

## Example of your service Dockerfile

```sh
FROM ubuntu:trusty

ENV SERVICE_NAME=archivarius
ENV SERVICE_WEIGHT=1                                          # Importance of the service in the group of same services
ENV REGISTRY_DNS=http://consul:8500/dev?refresh_interval=5    # If you use discover service of registry
ENV CHECK_HTTP=http://{{address}}/v1/check                    # {{address}} automaticaly replaced to real address of service
ENV CHECK_INTERVAL=5s
ENV CHECK_TIMEOUT=2s

EXPOSE {port}, ...
```

### Run regestry

Have to be runs on each server with your docker services.

```sh
docker run -d -e 'REGISTRY_DNS=http://consul:8500/dev?refresh_interval=5' geniusrabbit/registry
```
