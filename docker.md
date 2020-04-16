# Matomo dans Docker

> installation de Matomo et MySql dans deux conteneurs Docker (sans docker-compose).

## Mysql

```bash
docker pull mysql
docker run --name mysql -e MYSQL_ROOT_PASSWORD=mdp -d mysql:latest
```

## Matomo

```bash
docker pull matomo
docker run -d -p 8088:80 --name matomo --link mysql:db -v matomo:/var/www/html matomo
```

Matomo est accessible à localhost:8088

### Accéder à Matomo sur un port autre que 80

Par défaut le conteneur Matomo est accessible uniquement sur le port 80. Pour changer ce réglage, il faut modifier la config de PHP dans le conteneur.

```bash
# ouvre un shell dans le conteneur Docker matomo
docker exec -it matomo sh

# install nano (éditeur de texte) dans le conteneur
apk update
apk add nano

# édite le fichier config/config.ini.php
nano config/config.ini.php

# ajoute le port sur la ligne
trusted_hosts[] = "localhost:7000"
```
