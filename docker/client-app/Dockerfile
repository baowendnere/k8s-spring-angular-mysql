FROM node:current-alpine3.18 as node
# Définit l'image de base comme Node.js dans sa version actuelle (alpine3.18) et la nomme 'node'.

WORKDIR /usr/src/app
# Définit le répertoire de travail dans le conteneur Docker comme /usr/src/app.

COPY package.json /usr/src/app
# Copie le fichier package.json depuis le répertoire local dans /usr/src/app du conteneur.

RUN npm install
# Exécute la commande 'npm install' pour installer les dépendances du projet Node.js.

COPY . /usr/src/app
# Copie tous les fichiers du répertoire local vers /usr/src/app dans le conteneur.

RUN npm run build --prod
# Exécute la commande 'npm run build --prod' pour générer la construction de production de l'application.

FROM nginx:stable-alpine3.17-slim
# Définit une nouvelle étape en utilisant l'image de base Nginx (stable-alpine3.17-slim).

COPY --from=node /usr/src/app/dist/angular-16-crud /usr/share/nginx/html
# Copie les fichiers de construction générés précédemment depuis 'node' vers le dossier HTML de Nginx.

EXPOSE 8081:80
# Expose le port 8081 du conteneur Docker sur le port 80 de l'hôte pour permettre l'accès à l'application.
