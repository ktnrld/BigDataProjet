# REQUETES SUR LES TABLES HIVE
Rappel : 
```
    use ece_2021_fall_app_1;
```
### ORDONNENCEMENT DES MOYENNES DE RATINGS
```
    SELECT * from ece_2021_fall_bda_${ece_group}.projet_kdr_title_ratings order by averagerating desc limit 5;
```
Résultat : 
![c1](https://user-images.githubusercontent.com/71653765/147704353-49023874-d220-4193-8e21-df5ca8e1dbf7.png)

### DUREE DES FILMS SOUHAITES

#### Nombre de films dont la durée est inférieur à 1 heures - FILM COURT
```
    SELECT count(*) AS nbFilmCourt
    FROM projet_kdr_title_basics
    WHERE runtimeminutes < 60;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147705287-09c4c7d3-5737-491f-987e-b79c6eb01993.png)
#### Nombre de films dont la durée est comprise entre 1 et 2 heures - FILM NORMAL
```
    SELECT count(*) AS nbFilmNormal
    FROM projet_kdr_title_basics
    WHERE runtimeminutes > 60 AND runtimeminutes < 120;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147705641-d6cef80a-6722-42a2-b382-434aa22ea4ca.png)

#### Nombre de films dont la durée est supérieur à 2 heures - FILM LONG
```
    SELECT count(*) AS nbFilmLong
    FROM projet_kdr_title_basics
    WHERE runtimeminutes > 120;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147705412-35fb113f-562b-4ed5-b551-82d05e98d785.png)
### FILM ROMANTIQUE - DUREE MOYENNE
#### Durée moyenne des films romantiques.
```
    SELECT avg(runtimeminutes) AS DureeMoyenneFilmRomantique
    FROM projet_kdr_title_basics
    WHERE genres == "Romance";
```

### FILM DRAMATIQUE - DUREE MOYENNE
#### Durée moyenne des films dramatiques.
```
    SELECT avg(runtimeminutes) AS DureeMoyenneFilmDramatique
    FROM projet_kdr_title_basics
    WHERE genre == "Drama";
```
### MEILLEUR FILM ROMANTIQUE
#### Note moyenne des films romantique
```
    SELECT avg(averagerating) AS noteMoyFilmRomantique
    FROM (
      SELECT tconst
      FROM projet_kdr_title_basics
      WHERE array_contains(genres, 'Romance')
    ) titles JOIN projet_kdr_title_basics ratings
    ON titles.tconst = ratings.tconst;
```
#### Note moyenne des films dramatique
```
    SELECT avg(averagerating) AS noteMoyFilmDramatique
    FROM (
      SELECT tconst
      FROM projet_kdr_title_basics
      WHERE array_contains(genres, 'Drama')
    ) titles JOIN projet_kdr_title_basics ratings
    ON titles.tconst = ratings.tconst;
```
### Requête demandé par notre professeur
#### Top 5 des films qui ont été réalisés par Tarantino
```
    SELECT
      t.tconst AS tconst,
      t.primarytitle AS title,
      r.averagerating AS avg_rating
    FROM (
      SELECT nconst
      FROM projet_kdr_title_basics
      WHERE primaryname = 'Quentin Tarantino'
    ) n
    JOIN projet_kdr_title_basics_title_crew c ON array_contains(c.director, n.nconst)
    JOIN projet_kdr_title_basics_title_ratings r ON c.tconst = r.tconst
    JOIN projet_kdr_title_basics_title_basics t ON c.tconst = t.tconst
    ORDER BY r.averagerating DESC
    LIMIT 5;
```
