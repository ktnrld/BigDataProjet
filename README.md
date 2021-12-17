# Projet BigData : Gestion de données de la base IMDB 

## Etudiants :

Apprentis SI01 class ING5 :
```
     ORTIZ DIANA
     ROULAND KATHLEEN
     OULD-KACI RAYAN
```
### Technologies utilisées :
```diff
+ Cluster : Hadoop
+ Explotation de la base sur : Hive et Hbase
+ Explotation sur le cluster : Spark 
+ Visualisation des données sur Graphana
```
![IMDb_Header_Page](https://user-images.githubusercontent.com/71117842/146515073-0d4678b5-81c1-4f61-9eed-43ee0ee3f447.jpg)

# Informations sur le projet

Le projet cherche à exploiter l’ensemble de données de IMDb. Les données de ces fichiers sont accessibles à tout le monde et peut être consulté ainsi que téléchargé à partir de https://datasets.imdbws.com/. A savoir que les données sont actualisées quotidiennement.

De plus, nous avons accès à 7 fichiers data :
```diff
-	name.basics.tsv.gz
-	title.akas.tsv.gz
-	title.episode.tsv.gz
+	title.basics.tsv.gz
+	title.crew.tsv.gz
+	title.principals.tsv.gz
+	title.ratings.tsv.gz
```

L’ensemble des données IMDb Chaque ensemble de données est contenu dans un fichier au format TSV (valeurs séparées par des tabulations) compressé dans le jeu de caractères UTF-8. La première ligne de chaque fichier contient des en-têtes décrivant le contenu de chaque colonne. Un '\N' est utilisé pour indiquer qu'un champ particulier est manquant ou nul pour ce titre/nom.

Regardons le schème de tables :

## Schema of imdb_title.basics
![titleprincipals](https://user-images.githubusercontent.com/71117842/146517468-bc595c48-214e-4c00-9f15-2bd54354003d.png)

## Schema of imdb_title.basics
![basicstitle](https://user-images.githubusercontent.com/71117842/146517469-e59dd63f-39db-4fb3-9635-4ca02db1b606.png)

## Schema of imdb_title.basics
![ratings](https://user-images.githubusercontent.com/71117842/146517470-2e0d22ba-de72-445f-a517-9a8b16976809.png)

## Schema of imdb_title.basics
![titlecrew](https://user-images.githubusercontent.com/71117842/146517471-588ae764-f6e1-4778-a60b-3758fd6de7e9.png)

## Stack

| Lib | Version |
| ------ | ------ |
| express | 4.17.1 |
| mongoose | 5.11.8 |

---
## Prerequisites:

## Setting Up avec le cluster d'Adaltas
## Notre application
Vous pouver vérifier la créations des répertoires dans HDFS

## Requêtes et résultats sur : Hive
### 1. Création du HIVE DB :
### 2. Création des Tables dans le format ORC :
### 3. Reqêttes simples sur chaque table :
### 4. Partitions faite sur les tables :
### 5. Reqûettes plus complexes sur les tables :

## Requêtes et résultats sur : HBase
## Visualisation du dashboard : Graphana
