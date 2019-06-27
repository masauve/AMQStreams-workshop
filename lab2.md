## Réplication

#### Étape 1:  Création du Topic Kafka

En utilisant l'operator AMQ Streams, créer un topic Kafka nommer "demo-2" avec 3 partitions et 3 replicas:

Dans la console OpenShift

1) Sélectionner le project userXX-kafka
2) Sélectionner "Installed Operators" dans le menu de gauche
3) Créer un nouveau Topic avec le bouton "Create New"

![Console](images/lab1-partitions-01.png)

Dans la page de configuration du topic, utiliser les paramêtres suivants:
name:  demo-2
partitions: 3
replicas: 3

![Topic YAML](images/lab1-partitions-02.png)

Le nouveau Topic demo-2 apparait dans la liste des topics disponible. 
Le topic "my-topic" devrait aussi être présent. Ce topic a été créé automatiquement lors du lab 1.  L'operator a detecté le changement de configuration et à ajouter le topic à la liste des topics disponible. 

![Topic Liste](images/lab1-partitions-03.png)


#### Étape 2: Exploration des partitions

