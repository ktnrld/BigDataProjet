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
| Grafana | 6.7.1 |
| mongoose | 5.11.8 |

---
## Prerequisites:

## Setting Up avec le cluster d'Adaltas

1. Ouvrir l'appliction OpenVPN Connect
2. Ouvrir le powershell si vous êtes sur windows
3. utiliser la commande suivante pour ouvrir la session sur le cluster ensuite rentrez votre mot de passe
```diff
    ssh username@edge-1.au.adaltas.cloud
    ssh username@10.0.0.63
```
## Notre application

Nous souhaitons faire une application en nous mettons dans la peau d'un utilisateur sur le site de IMDB, pour cela nous allons créer des tables sur HDFS ensuite nous allons faire des rêquettes sur HIVE et sur HBASE.


Vous pouver vérifier la création des répertoires dans HDFS

```diff
    Hdfs dfs -mkdir /education/ece_2021_fall_app_1/nomprojet
```
Nous allons créer un sous dossier à ce projet :
```diff
    Hdfs dfs -mkdir /education/ece_2021_fall_app_1/nomprojet/sousDirectory
```
Puis, nous allons faire une copie de edge sur hdfs :
```diff
    Hdfs dfs -copyFromLocal sousDirectory/fichier /education/ece_2021_fall_app_1/nomprojet
```
# Requêtes et résultats sur : Hive
## 1. Création du HIVE DB :
## 2. Création des Tables dans le format ORC :
## 3. Requêttes simples sur chaque table :
## 4. Partitions faite sur les tables :
## 5. Reqûettes plus complexes sur les tables :

# Requêtes et résultats sur : HBase

# Visualisation du dashboard : Grafana



