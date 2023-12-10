# Étape 1 : Utilisation de l'image Maven pour la compilation
FROM maven:3.9.5-eclipse-temurin-17-alpine AS maven

# Étiquette pour le mainteneur du Dockerfile
LABEL MAINTAINER="tanguykabore@yahoo.fr"

# Définition du répertoire de travail dans le conteneur
WORKDIR /usr/src/app

# Copie des fichiers de l'application dans le répertoire de travail
COPY . /usr/src/app

# Exécution de la compilation et du packaging de l'application dans un JAR exécutable
RUN mvn clean package

# Étape 2 : Création d'une image minimale Alpine pour exécuter l'application
FROM eclipse-temurin:17-jre-alpine

# Définition d'un nouveau répertoire de travail
WORKDIR /opt/app

# Copie du JAR résultant depuis l'étape de build Maven vers le répertoire de travail
COPY --from=maven /usr/src/app/target/spring-boot-data-jpa*.jar /opt/app/backend.jar

# Exposition du port 8080 pour les connexions externes
EXPOSE 8080

# Définition du point d'entrée pour l'exécution de l'application Spring Boot
ENTRYPOINT ["java", "-jar", "/opt/app/backend.jar"]