# Projet BigData : Gestion de données de la base IMDB 

Date d'échéance : 31/12/2021
## Consignes 
Le projet doit se concentrer sur les systèmes distribués Open Source.

Un projet technique peut être l'installation d'une pile de technologies et/ou l'écriture de code pour traiter les données sur la pile. Il doit inclure l' implémentation : code, fichiers de configuration. Dans ce cas:
Le code doit être hébergé sur un dépôt Git.
Le code doit être documenté (README, commentaires en ligne).
Le rapport de projet doit inclure une description claire du projet, les étapes de sa mise en œuvre et une liste des problèmes rencontrés.

## Etudiants :

Apprentis Ing5 SI-01 :
```
     ORTIZ DIANA
     ROULAND KATHLEEN
     OULD-KACI RAYAN
```
### Technologies utilisées :
```diff
+ Cluster : Hadoop
+ Exploitation de la base sur : Hive et Hbase
+ Exploitation sur le cluster : Spark 
+ Visualisation des données sur Graphana
```

![image](https://user-images.githubusercontent.com/71117842/147662245-1bc3959e-7cdb-4209-90f3-155826a96a57.png)


# Informations sur le projet

Le projet cherche à exploiter l’ensemble des données de IMDb. Les données de ces fichiers sont accessibles et peuvent être consultés ainsi que téléchargés à partir de https://datasets.imdbws.com/. A savoir que les données sont actualisées quotidiennement.

De plus, nous avons accès à 7 fichiers de données :
```diff
-	name.basics.tsv.gz
-	title.akas.tsv.gz
-	title.episode.tsv.gz
+	title.basics.tsv.gz
+	title.crew.tsv.gz
+	title.principals.tsv.gz
+	title.ratings.tsv.gz
```

L’ensemble des données IMDb - Chaque ensemble de données est contenu dans un fichier au format TSV (valeurs séparées par des tabulations) compressé dans le jeu de caractères UTF-8. La première ligne de chaque fichier contient des en-têtes décrivant le contenu de chaque colonne. Un '\N' est utilisé pour indiquer qu'un champ particulier est manquant ou nul pour ce titre/nom.

Regardons le schème de tables :

## Schema of imdb_title.basics
![titleprincipals](https://user-images.githubusercontent.com/71117842/146517468-bc595c48-214e-4c00-9f15-2bd54354003d.png)

## Schema of imdb_title.basics
![basicstitle](https://user-images.githubusercontent.com/71117842/146517469-e59dd63f-39db-4fb3-9635-4ca02db1b606.png)

## Schema of imdb_title.basics
![ratings](https://user-images.githubusercontent.com/71117842/146517470-2e0d22ba-de72-445f-a517-9a8b16976809.png)

## Schema of imdb_title.basics
![titlecrew](https://user-images.githubusercontent.com/71117842/146517471-588ae764-f6e1-4778-a60b-3758fd6de7e9.png)

## Cas d'utilisation
Nous sommes une plateforme qui permet de répondre aux requêtes des clients.

## Stack

| Lib | Version |
| ------ | ------ |
| express | 4.17.1 |
| mongoose | 5.11.8 |

---
## Prerequisites:

## Setting Up avec le cluster d'Adaltas
## Notre application
Vous pouver vérifier la création des répertoires dans HDFS

# Requêtes et résultats sur : Hive
## 1. Création du HIVE DB :
## 2. Création des Tables dans le format ORC :
## 3. Reqêttes simples sur chaque table :
## 4. Partitions faite sur les tables :
## 5. Reqûettes plus complexes sur les tables :

# Requêtes et résultats sur : HBase

# Visualisation du dashboard : Grafana

## 1. Mise en place de Grafana dans un Docker Container

Démarrez le conteneur Docker en liant Grafana au port externe 3000 grâce à la commande :
```diff
docker run -d -p 3001:3000 --name=grafanaserver -e "GF_SECURITY_ADMIN_USER=admin" -e "GF_SECURITY_ADMIN_PASSWORD=password" grafana/grafana:latest
```
Par exemple :

![image](https://user-images.githubusercontent.com/71117842/147662275-ca58a0b6-9500-42e6-b51d-8af81d8c8247.png)

![image](https://user-images.githubusercontent.com/71117842/147663542-3cb483bb-8abe-40e6-b1cd-2f409b30a709.png)

## 2. Installation du Plugin CVS en Grafana
Command to Install Grafana Plugin:
```diff
docker exec -it grafanaserver bash
grafana-cli plugins install grafana-googlesheets-datasource
```
![image](https://user-images.githubusercontent.com/71117842/147662415-bc87b756-0d22-42cf-9a77-709f013ce546.png)

![image](https://user-images.githubusercontent.com/71117842/147665226-211cae47-9b5f-4116-b4e4-759dfac12c9c.png)

## 3. Configuration du CSV datasource en Grafana
## 3. Ecriture des requêttes et creation du dashboard en Grafana



