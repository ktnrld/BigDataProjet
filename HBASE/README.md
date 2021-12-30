# MISE EN PLACE DE HBase
![image](https://user-images.githubusercontent.com/71117842/147707253-9772cbb3-b5d8-4508-a018-8162d94e1b0c.png)

## Connection à Hbase
Premièrement, nous nous rendons sur hbase.
```
    hbase shell
```

## Table Hbase
Dans HBase les données sont organisées dans des tables. Les noms des tables sont des chaînes de caractères.
Dans chaque table, les données sont organisées dans des lignes. Une ligne est identifiée par une clé unique (RowKey). La Rowkey n’a pas de type, elle est traitée comme un tableau d’octets. Les données au sein d’une ligne sont regroupées par column family. Chaque ligne de la table a les mêmes column families, qui peuvent être peuplées ou pas. Les column families sont définies à la création de la table dans HBase. Les noms des column families sont des chaînes de caractères.

Nous cherchons à faire une table comme cela : 
![hbase table](https://user-images.githubusercontent.com/71653765/147701808-205d6bad-df65-4fb4-b0c9-86b7f6c97676.png)

## Création d'un fichier excel spécial


## Création de la table Hbase
Nous allons prendre le modèle ci-dessous:
![image](https://user-images.githubusercontent.com/71653765/147788673-a2af5a55-7c28-4828-bebf-38c8e57da042.png)

```
    create 'ece_2021_fall_app_1:hbaseTable', 'tconst'
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147789920-efccc926-f488-42c3-98ea-76753fd14e72.png)

## CSV --> Hbase
Nous avons tout d'abord créer manuellement un fichier csv.
Nous avons vérifié que les tconst correspondaient afin de tout mettre sur la même ligne.

Vu du fichier excel : 
![image](https://user-images.githubusercontent.com/71653765/147789080-35789b58-334a-4e25-b25c-623739550926.png)

Mettons le tout sur edge :
![image](https://user-images.githubusercontent.com/71653765/147788860-cf26e5bb-7e24-4c16-9378-348204e4ae1a.png)
![image](https://user-images.githubusercontent.com/71653765/147789131-f96df1d7-f270-466d-9f10-fed857bb6ff4.png)

Vérifions qu'il est bien dans edge : 
![MicrosoftTeams-image (1)](https://user-images.githubusercontent.com/71653765/147788814-ac98bf99-e3b6-4075-899d-b487c1887311.png)



## Vérification 
```
    list
```
ou
```
    scan 'ece_2021_fall_app_1:hbaseTable'
```
![image](https://user-images.githubusercontent.com/71653765/147790293-e9f92912-1f16-4464-a9a4-7dffe8be61ee.png)
## Csv --> Hbase
Comme nous pouvons le voir ci-dessous, la table est vide, nous allons donc la remplir grâce à :
```
hbase org.apache.hadoop.hbase.mapreduce.ImportTsv -Dimporttsv.separator=';' -Dimporttsv.columns=HBASE_ROW_KEY,tconst ece_2021_fall_app_1:hbasetable /k.rouland-ece/hbase/hbaseexcel.csv
```

Nous mettons donc bien les données :
![image](https://user-images.githubusercontent.com/71653765/147791446-84c26fa3-e359-4d82-bdc2-2559e0b7592f.png)

## Hbase --> Hive
Nous allons maintenant créer une table externe sur Hive qui va correspondre aux données qui sont sur Hbase, nous précisions que les données ne sont pas sur edge mais sur hbase et finalement, nous réalisons une sorte de correspondance entre la table Hive et les données de Hbase.
```
    CREATE EXTERNAL TABLE hbaseTableOnHive (tconst string)
    STORED BY 'org.apache.hadoop.hive.hbase.HBaseStorageHandler'
    WITH SERDEPROPERTIES ("hbase.columns.mapping" = ":key,cf:"tconst")
    TBLPROPERTIES ("hbase.table.name" = "hbaseTable");
```

