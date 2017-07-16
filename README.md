# Dockerized Sonarqube for PHP analysis

This image extends the [official Sonarqube docker image](https://hub.docker.com/_/sonarqube/) (5.4-alpine).

## Running the container ##

    docker run --name <name of your container> -d kajnelissen/sonarqube-alpine-php:<tag>

## Running the container with a database ##

See this [docker compose file](https://github.com/kajnelissen/docker-compose-collection/blob/master/sonarqube-php-mariadb/docker-compose.yml) for an example.
