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
```
    create nomBase, 'CF', 'CF'

## Hbase --> Hive
Nous allons maintenant créer une table externe sur Hive qui va correspondre aux données qui sont sur Hbase, nous précisions que les données ne sont pas sur edge mais sur hbase et finalement, nous réalisons une sorte de correspondance entre la table Hive et les données de Hbase.
```
    CREATE EXTERNAL TABLE hbase_table (A COMPLETER) 
    STORED BY 'org.apache.hadoop.hive.hbase.HBaseStorageHandler'
    WITH SERDEPROPERTIES ("hbase.columns.mapping" = ":key,cf:nom de la column family")
    TBLPROPERTIES ("hbase.table.name" = "client");
```
