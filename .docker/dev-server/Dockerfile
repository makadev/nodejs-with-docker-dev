FROM node:lts-buster

ENV NPM_CACHE "/app/.npm-cache"

RUN set -ex \
    ## update packages and install deps / usefull tools
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get update -y -q \
    && apt-get upgrade -y -q \
    ## cleanup
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* \
    ## setup npm to place cache under moint point (easy reuse in dev)
    && npm set cache ${NPM_CACHE}

## Mountpoint for App Source & Workdir
VOLUME /app
WORKDIR /app

## Port where Sample Application is served f.e. by http-server
EXPOSE "3000"

## install and startup
CMD npm install \
    && npm run start
