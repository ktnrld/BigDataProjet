# MISE EN PLACE DE HBase

### Téléchargement des tables

Nous avons télécharger sur IMDB les différentes tables concernant les films.

### Local --> Edge

Puis, nous souhaitons mettre ces fichiers sur edge, cela est faisable grâce à la commande ci-dessous :

```
    scp chemin\title.tsv k.rouland-ece@edge-1.au.adaltas.cloud:
```

Nous faisons cela pour chacune des tables qui nous interessent sur imdb, ici nous avons selectionné quatre tables :

- movie
- name
- rating
- title

### Connection

```
    ssh k.rouland-ece@edge-1.au.adaltas.cloud
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

### Création des tables Hive

Nous allons donc créer 7 tables correspondant aux 7 fichiers sur HDFS, mais cette fois-ci sur Hive.
Ces tables sont externes et elles sont créées afin que nous puissions les requêtés. Ces tables pointent sur le fichier où les données du fichier tsv sont.

#### Names.basics

```
    CREATE EXTERNAL TABLE ece_2021_fall_app_1.k_rouland_ece_IMDB_name_basics
    (
        nconst STRING,
        primaryName STRING,
        birthYear INT,
        deathYear INT,
        primaryProfession STRING,
        knownForTitles STRING
    )
    ROW FORMAT DELIMITED
    FIELDS TERMINATED BY '\t'
    LINES TERMINATED BY '\n'
    STORED AS TEXTFILE
    LOCATION '/education/ece_2021_fall_app_1/r.ould-kaci-ece/project/bdd/name.basics';
```

#### Affichage de name basics

```
    SELECT * FROM ece_2021_fall_app_1.k_rouland_ece_IMDB_name_basics  LIMIT 5;
```

Cette ligne de code permet d'avoir les 5 premiers résultats de la table pour vérifier qu’elle n’est pas vide.

On créé le reste des fichiers de la même façon

#### Création des tables en format orc

Nous allons créer d'autres tables Hive mais cette fois-ci stocké sous le format orc, dans un autre fichier. On ingère le fichier csv des premières tables dans ces nouvelles tables.
