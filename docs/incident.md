# Compte rendu d'incident - Mise en service v0.9.0 et Retour arrière

1. Ce qui s'est passé : Le déploiement de la version v0.9.0 a échoué car le conteneur API a planté au démarrage suite à une erreur applicative critique (commande de démarrage en échec).
2. Moment de détection : L'incident a été détecté immédiatement par le script `scripts/wait-healthy.sh` qui a constaté l'échec des requêtes `/health` et a conclu à « staging non sain ».
3. Actions menées : Diagnostic rapide dans les journaux avec `docker compose logs api`, puis rollback immédiat vers la version saine `v1.0.0` sans reconstruire l'image (`IMAGE_TAG=v1.0.0`).
4. Durée d'indisponibilité : Le service a été indisponible pendant environ 60 secondes, correspondant au cycle de détection du test de santé et à la relance instantanée de la version précédente.
5. Prévention : Bloquer la publication de toute image non validée par la chaîne CI (job test obligatoire) et automatiser le rollback dès l'échec du healthcheck de pré-déploiement.
