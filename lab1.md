Installation d'un cluster Kafka avec l'opérateur AMQ Streams

Étape 1:  Connection au cluster OpenShift

Étape 2:  Création d'un cluster Kafka

L'opérateur AMQ Streams a été installé par l'administrateur du cluster et est disponible pour votre projet.

Dans le projet userXX-Kafka, à partir du catalogue, ajouter un cluster Kafka (bouton "Browse Catalog")

![Catalog](images/lab1-install-01.png)

Choisir l'option 'Kafka"

![Catalog](images/lab1-install-02.png)

Créer un cluster Kafka (bouton "Create")

![Catalog](images/lab1-install-03.png)

Examiner le fichier YAML. Ce fichier est utilisé par l'opérateur pour configurer et installer le cluster Kafka.

![Catalog](images/lab1-install-04.png)

1)  Nom du cluster et projet dans lequel il sera installé.
2)  Définition des 'listeners' qui seront déployés (Interne au cluster, externe, encryption ou non) et nombre de brokers Kafka
3)  Type de stockage pour Kafka (pour le lab - stockage éphémère dans le conteneur)
4)  Nombre de replicas pour le Zookeeper et type de stockage pour le Zookeeper 
5)  Operators additionnels a déployer

Pour le lab, les paramêtres par défaut seront utilisés
