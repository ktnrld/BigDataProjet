# <img src="https://img.icons8.com/fluency/40/000000/futurama-bender.png"/> Projet BigData : Gestion des données de la base IMDB <img src="https://img.icons8.com/fluency/40/000000/futurama-bender.png"/> 
![image](https://user-images.githubusercontent.com/71117842/147707307-2163329b-66d9-4892-b2c4-e532d2d85d96.png)

Date d'échéance : 31/12/2021
## <img src="https://img.icons8.com/cotton/40/000000/books--v2.png"/> Consignes 
Le projet doit se concentrer sur les systèmes distribués Open Source.

Un projet technique peut être l'installation d'une pile de technologies et/ou l'écriture de code pour traiter les données sur la pile. Il doit inclure l' implémentation : code, fichiers de configuration. Dans ce cas : Le code doit être hébergé sur un dépôt Git.
Le code doit être documenté (README, commentaires en ligne).
Le rapport de projet doit inclure une description claire du projet, les étapes de sa mise en œuvre et une liste des problèmes rencontrés.

## <img src="https://img.icons8.com/color/48/000000/github-2.png"/> Etudiants :

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

# 🎯 Informations sur le projet

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

Regardons le schéma des tables :

## Schema of imdb_name.basics

![image](https://user-images.githubusercontent.com/71117842/147791412-45d41348-bd60-4367-92ca-f3d52afa745d.png)
---

## Schema of imdb_title.basics

![image](https://user-images.githubusercontent.com/71117842/147791682-9ad802f8-32cc-461c-bf28-1ba6d72fee3b.png)
---
## Schema of imdb_title.ratings

![image](https://user-images.githubusercontent.com/71117842/147791481-e9bf50e3-3bed-4432-bdaf-0d69a53b924d.png)
---
## Schema of imdb_title.crew

![image](https://user-images.githubusercontent.com/71117842/147791580-f1d373b7-6aed-4334-9cb2-d3bf9605bc06.png)
---

## Cas d'utilisation / Description du projet
Nous sommes une plateforme qui permet de répondre aux requêtes des clients : par exemple, le client peut savoir rapidement, grâce à nos tables Hive partitionnées, quel est le type de film qui a la meilleur note. De plus, avec Grafana, nous proposons aux clients de visualiser différentes informations sous la forme de graphique ( dont les données sont directement issus de nos bases). Puis, nous avons ajouté l'aspect Hbase pour nous entrainer dans notre apprentissage.

Toutes les étapes pour réaliser ce projet ont été définis dans les dossiers Hive, Hbase et Grafana. Vous y trouverez aussi nos requêtes et résultats.

---
## 🏭 Prerequisites:

## Setting Up avec le cluster d'Adaltas

1. Ouvrir l'application OpenVPN Connect.
2. Ouvrir le powershell si vous êtes sur windows.
3. Utiliser la commande suivante pour ouvrir la session sur le cluster ensuite entrez votre mot de passe :
```diff
    ssh username@edge-1.au.adaltas.cloud
    ssh username@10.0.0.63
```
## Notre application

Nous souhaitons faire une application en nous mettons dans la peau d'un utilisateur sur le site de IMDB, pour cela nous allons créer des tables sur HDFS ensuite nous allons faire des requêtes sur HIVE et sur HBASE.

Vous pouvez vérifier la création des répertoires dans HDFS : 
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
## <img src="https://img.icons8.com/color/40/000000/program.png"/> Requêtes et résultats sur : Hive
Aller voir le dossier HIVE : https://github.com/ktnrld/BigDataProjet/tree/main/HIVE
Dans le dossier vous allez trouver :
- Un README qui contient tous les informations techniques faites.
- Un fichier qui contient les requêtes effectuées ainsi que son résultat en image.

## <img src="https://img.icons8.com/color/40/000000/program.png"/> Requêtes et résultats sur : HBase
Aller voir le dossier HBase : https://github.com/ktnrld/BigDataProjet/tree/main/HBASE
Dans le dossier vous allez trouver :
- Un README qui contient tous les informations techniques faites.
- Un fichier qui contient les requêtes effectuées ainsi que son résultat en image.

## <img src="https://img.icons8.com/color/40/000000/program.png"/> Visualisation du dashboard : Grafana
Aller voir le dossier Grafana : https://github.com/ktnrld/BigDataProjet/tree/main/GRAfANA
Dans le dossier vous allez trouver :
- Un README qui contient tous les informations techniques faites.
- Un fichier qui contient les requêtes effectuées ainsi que son résultat en image.

## Difficultés rencontrées
Pour Hive, nous n'arrivions pas à partitionner la table car nous ne trouvions pas la "formulation correcte". Cependant, nous avons finalement réussi à partitionner deux tables selon deux éléments pertinents. 

Pour Hbase, le plus compliqué a été de réfléchir à comment créer une seule table alors que nous en avons plusieurs.

Pour Grafana, nous avions rencontré un problème lors de l'ajout de donnée, nous supposons donc que le problème était lié à la trop grande quantité de donnée que nous voulions ingérer d'un seul coup.

## 🚀 Pour aller plus loin 
