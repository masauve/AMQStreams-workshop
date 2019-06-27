## Installation d'un cluster Kafka avec l'opérateur AMQ Streams

#### Étape 1:  Connection au cluster OpenShift

Connection au cluster OpenShift avec l'usager et password fournit durant l'atelier.


#### Étape 2:  Création d'un cluster Kafka

L'opérateur AMQ Streams a été installé par l'administrateur du cluster et est disponible pour votre projet.

Dans le projet userXX-Kafka, à partir du catalogue, ajouter un cluster Kafka (bouton "Browse Catalog")

![Catalog](images/lab1-install-01.png)

Choisir l'option 'Kafka"

![Catalog](images/lab1-install-02.png)

Créer un cluster Kafka (bouton "Create")

![Catalog](images/lab1-install-03.png)

Examiner le fichier YAML. Ce fichier est utilisé par l'opérateur pour configurer et installer le cluster Kafka.

![Operator Config](images/lab1-install-04.png)

1)  Nom du cluster et projet dans lequel il sera installé.
2)  Définition des 'listeners' qui seront déployés (Interne au cluster, externe, encryption ou non) et nombre de brokers Kafka
3)  Type de stockage pour Kafka (pour le lab - stockage éphémère dans le conteneur)
4)  Nombre de replicas pour le Zookeeper et type de stockage pour le Zookeeper 
5)  Operators additionnels a déployer

Pour le lab, les paramêtres par défaut seront utilisés

Pour créer le cluster, utiliser le bouton "Create"

L'opéator AMQ Streams démarre le processus de création de votre cluster Kafka:

![Catalog](images/lab1-install-05.png)

Attendre que le cluster Kafka démarrre.   

![Catalog](images/lab1-install-06.png)

Pour valider l'état du cluster, dans la console OpenShift, selectionner le menu Pod, dans votre projet (userXX-kafka). 
Attendre que les 7 pods du cluster Kafka soient 'Running' et 'Ready'

ou avec l'outil ligne de commande oc:
```
oc get pods -w -n userXX-kafka
```

#### Étape 3:  Validation de l'installation

Avec le client OpenShift, demarrer dans deux fenêtres differentes un producteur et un consommateur:

Producteur:

```
oc project userXX-kafka

oc run kafka-producer -ti --image=registry.access.redhat.com/amq7/amq-streams-kafka:1.1.0-kafka-2.1.1 --rm=true --restart=Never -- bin/kafka-console-producer.sh --broker-list my-cluster-kafka-bootstrap:9092 --topic my-topic 
```


Consommateur:
```
oc run kafka-consumer -ti --image=registry.access.redhat.com/amq7/amq-streams-kafka:1.1.0-kafka-2.1.1 --rm=true --restart=Never -- bin/kafka-console-consumer.sh --bootstrap-server my-cluster-kafka-bootstrap:9092 --topic my-topic --from-beginning
```

Le producteur est un "console" producer, un client Kafka qui envoie tous les messages entrer dans la console dans un topic kafka.
Entrez un message dans la console du producteur, le message devrait être affiché dans la fenêtre du consommateur.

![Kafka Test](images/lab1-kafka-test.png)


