# MISE EN PLACE DE HIVE
![image](https://user-images.githubusercontent.com/71117842/147707283-d1d2d35f-fab3-4284-a791-4f325eb88274.png)

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

### Les commandes à faire 
Pour aller sur Hive, nous tapons la commande ci-dessous : 
```
    beeline
```

Puis, nous avons besoin de faire : 
```
    use ece_2021_fall_app_1;
```

En plus, nous pouvons ajouter la commande ci-dessous :
```
    SET hivevar:ece_group=1;
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

#### Affichage de ratings

```
     SELECT * FROM projet_kdr_title_ratings LIMIT 5;
```

Cette ligne de code permet d'avoir les 5 premiers résultats de la table pour vérifier qu’elle n’est pas vide.

On créé le reste des fichiers de la même façon.
![image](https://user-images.githubusercontent.com/71653765/147692796-2f822b6c-2dc1-4123-a5cc-65ff8d09ee3d.png)

#### Création des tables en format orc

Nous allons créer d'autres tables Hive mais cette fois-ci stocké sous le format orc, dans un autre fichier. On ingère le fichier csv des premières tables dans ces nouvelles tables.
```
CREATE TABLE test2(tconst STRING, numvotes SMALLINT)
PARTITIONED BY(averagerating FLOAT)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '\t'
LINES TERMINATED BY '\n'
TBLPROPERTIES('serialization.null.format'='', 'skip.header.line.count'='1');
```

Le format de fichier ORC (Optimized Row Columnar) offre un moyen très efficace de stocker des données Hive. Il a été conçu pour surmonter les limitations des autres formats de fichiers Hive. L'utilisation de fichiers ORC améliore les performances lorsque Hive lit, écrit et traite des données. Le fichier ORC peut contenir des index légers et des filtres de floraison.

![image](https://user-images.githubusercontent.com/71653765/147692729-26ac4570-a0fa-480a-8868-94a20913af7b.png)

### Affichage des tables et Partitions
Nous souhaitons vérifier que nos tables ont bien été crée:

![show tables 2](https://user-images.githubusercontent.com/71653765/147694956-06583a4f-74c1-4034-9ee1-cca006282a0a.png)

Nous remarquons que nousa vons bien nos quatre tables avec leur quatre table orc.

Nous avons aussi quatre table partitionnées, étudions celle de rating : 
![tablepartitionne](https://user-images.githubusercontent.com/71653765/147692620-45d53d43-cd80-4648-b72a-b35fd3360d93.png)

Nous avons choisi de partitionné selon le rating car nous avons précédemment vu que cela nous permettait de diviser le fichier en moins de 100 fichiers contrairement aux deux autres colonnes, par exemple partitionné par l'id auraient été inneficaces car seul le meme nombre de fichier aurait été créer.

Grâce à la commande show partitions nous pouvons montrer cela : 
![showpartition](https://user-images.githubusercontent.com/71653765/147692934-7bc2f592-f8b5-4273-b9ff-1b3af788869c.png)

Nous avons juger bon de partitionner la table title.basics. 
Nous souhaitons partitionner selon : 
- titletype	: the type/format of the title (e.g. movie, short, TV series, TV episode, video, etc)
- isadult	String	0: non-adult title; 1: adult title
- genres	Array	includes the genres associated with the title (which can be documentary, genre, action,…)
-
! Note : nous n'avons pas montré toutes les tables car nous avons pour tous fonctionner de la même manière. Quand nous souhaitions partitionner nous vérifions en avance le nombre de partition que cela créerait, si celle-ci valait moins de 100, nous décidions de partitionné par cette colonne.



