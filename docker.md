# Matomo dans Docker

Ce fichier décrit l'installation en local de Matomo et MySql dans deux conteneurs Docker.

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

Accès à Matomo à localhost:8088

---

Config PHP pour accéder à Matomo sur le port 8080 (en local):

```bash
# ajoute la ligne 'enable_trusted_host_check=0'
# dans la partie '[General]' du fichier ./config/config.ini.php

docker exec -it matomo sed -i -e "s/\"localhost\"/\"localhost\"\\nenable_trusted_host_check=0/g" ./config/config.ini.php
```
