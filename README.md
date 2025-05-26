Space News Aggregator - Pipeline DevOps
Ce projet met en place un pipeline d’intégration et déploiement continu (CI/CD) pour l’application Space News Aggregator, développée en Spring Boot.

Objectif
Automatiser la construction, la création d’image Docker, la publication et le déploiement de l’application, tout en assurant son monitoring.

Description du pipeline Jenkins
Le pipeline comprend plusieurs étapes :

Construction Maven : compilation et packaging de l’application depuis le dépôt GitHub.

Création de l’image Docker : construction d’une image Docker propre de l’application.

Publication sur Docker Hub : connexion sécurisée et push de l’image vers Docker Hub.

Déploiement avec Docker Compose : arrêt des anciens conteneurs et lancement des nouveaux via Docker Compose.

Monitoring
Le monitoring est assuré par :

Prometheus : collecte des métriques applicatives.

Grafana : visualisation des données pour le suivi en temps réel.

Prérequis
Jenkins avec Maven et Docker configurés.

Compte Docker Hub avec identifiants enregistrés dans Jenkins.

Serveur avec Docker et Docker Compose installés.

Configuration fonctionnelle de Prometheus et Grafana pour le monitoring.

Utilisation
Lancer le pipeline Jenkins permet de :

Récupérer le code source.

Construire et packager l’application.

Construire et publier l’image Docker.

Déployer automatiquement la nouvelle version.

Suivre les performances grâce à Prometheus et Grafana.

Ressources
Dépôt GitHub : https://github.com/m-elhamlaoui/development-platform-sneakpeak

Image Docker Hub : hibaalaouii/devops-integration