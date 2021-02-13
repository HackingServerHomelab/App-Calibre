# App-Calibre

## First Time Prerequisites

1. `rm ./Data/books/.gitkeep`
2. Run [Traefik](https://github.com/HackingServerHomelab/App-Traefik)

## Running the Containers

1. Remap the following mounts in [docker-compose.yml](./Docker/docker-compose.yml)
    * `../Data/config:/config`
    * `../Data/books:/books`
2. Update the `GUAC_USER` and `GUAC_PASS` variables in [docker-compose.yml](./Docker/docker-compose.yml)
    * `echo -n password | openssl md5`
3. Update the Traefik host label in [docker-compose.yml](./Docker/docker-compose.yml)
    * ``"traefik.http.routers.calibre-web.rule=Host(`localhost`)"``
4. `docker-compose -f ./Docker/docker-compose.yml up -d`


### Server

1. Visit `http://<your-ip>:8080`
2. Set `/config/Calibre Library` as the calibre library location
3. Continue stepping through the wizard


### Web

These steps should only have to be performed during the first setup of
Calibre-Web

1. Visit `https://<your-ip>/`
2. Set `/books` as the calibre library location
3. Default credentials are `admin:admin123`
4. Set the path of unrar in the admin page (Admin -> Basic Configuration -> External Binaries). Its path is `/usr/bin/unrar`
5. Set the path of the E-Book converter (Admin -> Basic Configuration -> External Binaries). Its path is `/usr/bin/ebook-convert`
6. Configure any other options you may want
