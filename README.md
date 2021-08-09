# nodejs-with-docker-dev
NodeJS LTS with Docker for Development Template comes with
* a docker-compose configuration to mount the project path under `/app` inside a container for serving/building/modifications
* a simply command to start up a bash inside a nodejs container usefull for running `npm` commands, tests and so on
* a simple server command which is usally enough to startup a http-server for development
* an npm cache config which puts the cache in `.npm-cache` such that you won't loose the cache evertime the container is rebuild

## checklist

* check `.gitignore`
* check `.docker/dev-toolbox/Dockerfile` has all the tools you need
* check `.docker/dev-server/Dockerfile` has the correct starting command

## toolbox (command line)

Start a new bash inside a container with:
```bash
docker compose run --rm toolbox
```

Be aware that this can be run multiple times and it is always a new container created (and with `--rm` flag also deleted) so modifications like installing other stuff outside of the mounted path won't be saved. 

## server (or watch)

Start a new server inside a container with:
```bash
docker compose up server
```

and stop it from another shell with
```bash
docker compose down server
```

The default setup is configured to map container port `3000` to `127.0.0.1:8080`.

## cleanup

Sometimes it is usefull to run:
```bash
docker compose down --remove-orphans
```
to cleanup created containers which were not deleted for whatever reason.