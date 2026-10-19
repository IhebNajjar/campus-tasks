# Campus Tasks

## Démarrage

Projet utilisé dans les ateliers DevOps.

## Santé du service

Point prévu : GET /health

## Support
Contact equipe A : equipe-a@example.invalid
Contact equipe B : equipe-b@example.invalid

## Docker

```bash
docker build -t campus-tasks:1.1 .
docker run -d --name campus-api -p 8080:8080 campus-tasks:1.1
curl http://localhost:8080/health
```
