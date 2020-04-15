# Configurations Docker

## Environnement de développement (localhost)

```bash
# démarre l'application dans des conteneurs Docker
# en mode `development`
# accessible à http://localhost:PORT
docker-compose -f ./docker-compose.localhost.yml up --build
```

## Environnement local

Pour lancer l'application en local dans un environnement de production

Pré-requis:

- une installation locale active de https://github.com/jwilder/nginx-proxy
- modifier le fichier `hosts` de l'environnement de dev pour faire pointer `127.0.0.1` vers `URL`
- un certificat ssl auto-signé

[Instructions complètes](https://medium.com/@francoisromain/set-a-local-web-development-environment-with-custom-urls-and-https-3fbe91d2eaf0)

```bash
# démarre l'application et la base de données dans des containers Docker
# en mode `production`
# accessible à https://{URL}
docker-compose -f ./docker-compose.local.yml up --build
```

## Environnement de production

Pré-requis:

- une installation active de https://github.com/jwilder/nginx-proxy
- [instructions](https://medium.com/@francoisromain/host-multiple-websites-with-https-inside-docker-containers-on-a-single-server-18467484ab95)

```bash
# démarre l'application et la base de données dans des containers Docker
# en mode `production`
# accessible à http://api.camino.beta.gouv.fr
docker-compose up -d --build
```
