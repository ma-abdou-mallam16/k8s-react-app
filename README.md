# Application React sur Kubernetes

## À propos du projet

Ce projet est une démonstration de déploiement d'une application React simple sur Kubernetes. L'application affiche un message "Bonjour le Monde !" et est conteneurisée avec Docker puis déployée sur un cluster Kubernetes.

## Structure du projet

- `app/` : Contient l'application React TypeScript
  - `src/` : Code source de l'application
  - `Dockerfile` : Configuration pour la création de l'image Docker
- `deployment.yaml` : Configuration du déploiement Kubernetes
- `service.yaml` : Configuration du service Kubernetes pour exposer l'application
- `ingress.yaml` : Configuration de l'Ingress pour l'accès externe à l'application

## Technologies utilisées

- React 19
- TypeScript
- Docker
- Kubernetes
  - Deployment
  - Service (NodePort)
  - Ingress (NGINX)

## Prérequis

- Node.js et npm
- Docker
- Un cluster Kubernetes (Minikube, k3s, Docker Desktop, etc.)
- kubectl

## Installation locale

1. Cloner le dépôt :
   ```
   git clone <URL_du_dépôt>
   cd k8s-react-app
   ```

2. Installer les dépendances et lancer l'application en local :
   ```
   cd app
   npm install
   npm start
   ```

## Déploiement sur Kubernetes

1. Construire l'image Docker :
   ```
   cd app
   docker build -t <votre-nom-utilisateur>/k8s-react-app .
   docker push <votre-nom-utilisateur>/k8s-react-app
   ```

2. Déployer sur Kubernetes :
   ```
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   kubectl apply -f ingress.yaml
   ```

3. Accéder à l'application :
   - Via NodePort : http://<adresse-ip-noeud>:31111
   - Via Ingress : http://<adresse-ingress>/ (si configuré)

## Architecture

L'application est déployée avec 3 réplicas pour assurer la haute disponibilité. Elle est exposée via un service NodePort sur le port 31111 et peut être accessible de l'extérieur via un Ingress NGINX.

## License

Mit