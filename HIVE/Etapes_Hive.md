## Etapes Hive 

### Téléchargement des tables 
Nous avons télécharger sur IMDB les différentes tables concernant les films.

### Local --> Edge 
Puis, nous souhaitons mettre ces fichiers sur edge, cela est faisable grâce à la commande ci-dessous :
```
    scp chemin\title.tsv k.rouland-ece@edge-1.au.adaltas.cloud:
```

### Edge --> HDFS
Puis, nous souhaitons mettre le tout sur hdfs. Nous créons donc un dossier projet.
```
    Hdfs dfs -mkdir /education/ece_2021_fall_app_1/nomprojet
```
Nous allons créer un sous dossier à ce projet :
```
    Hdfs dfs -mkdir /education/ece_2021_fall_app_1/nomprojet/sousDirectory
```
Puis, nous allons faire une copie de edge sur hdfs :
```
    Hdfs dfs -copyFromLocal sousDirectory/fichier /education/ece_2021_fall_app_1/nomprojet
```
