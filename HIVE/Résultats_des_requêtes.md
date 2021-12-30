# REQUETES SUR LES TABLES HIVE
Rappel : 
```
    use ece_2021_fall_app_1;
```
### ORDONNENCEMENT DES MOYENNES DE RATINGS
```
    SELECT * from projet_kdr_title_ratings order by averagerating desc limit 5;
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

### Les plus longs
#### Noms des 10 films les plus longs.
```
    SELECT originalTitle, runtimeminutes
    FROM  projet_kdr_title_basics
    WHERE titletype LIKE 'movie'
    ORDER BY runtimeminutes DESC
    LIMIT 10;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147780083-f3126d9d-2105-4a91-b9e8-a0c81388702b.png)
#### Noms des 10 shorts les plus longs
 ```
SELECT originalTitle, runtimeminutes
FROM  projet_kdr_title_basics
WHERE titletype LIKE 'short'
ORDER BY runtimeminutes DESC
LIMIT 10;
 ```
Résultat :
![image](https://user-images.githubusercontent.com/71653765/147780266-c4e2e225-63a6-41ad-afc2-3b9ec3f86154.png)
### FILM ROMANTIQUE - DUREE MOYENNE
#### Durée moyenne des films débutant par romance.
```
    SELECT avg(runtimeminutes) AS DureeMoyenneFilmDramatique
    FROM projet_kdr_title_basics
    WHERE  primarytitle '(^| )[Rr]omance';
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147779662-2c033990-bae9-4400-8d58-b9ad5e7dd590.png)

### Film Adulte
#### Comptons le nombre de film pour adulte
```
SELECT count(*) AS NombreFilmAdulte
FROM projet_kdr_title_basics 
WHERE titletype LIKE 'movie' AND isAdult = 1;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147780732-f6b8eda5-8405-4b1f-90f5-e26cd027c15b.png)
### Note moyenne d'un genre de film
#### Note moyenne des films romantique
```
    SELECT avg(averagerating) AS noteMoyFilmRomantique
    FROM (
      SELECT tconst
      FROM projet_kdr_title_basics
      WHERE array_contains(genres, 'Romance')
    ) b JOIN projet_kdr_title_ratings r
    ON b.tconst = r.tconst;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147706496-0606da8a-2eb8-425c-bd80-57de0d6423ca.png)

#### Note moyenne des films dramatique
```
    SELECT avg(averagerating) AS noteMoyFilmDramatique
    FROM (
      SELECT tconst
      FROM projet_kdr_title_basics
      WHERE array_contains(genres, 'Drama')
    ) b JOIN projet_kdr_title_ratings r
    ON b.tconst = r.tconst;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147706666-c8748f92-04c7-4e0d-852f-4ba141cf0728.png)

### NUMVOTES
#### Les films qui ont reçu le plus de NumVotes.
```
    SELECT numVotes, originalTitle
    FROM projet_kdr_title_ratings JOIN projet_kdr_title_basics USING (tconst)
    WHERE titletype LIKE 'movie'
    ORDER BY numVotes DESC
    LIMIT 10;
```
Résultat :
![image](https://user-images.githubusercontent.com/71653765/147780988-21986b26-794b-4733-96fc-f7838896ac25.png)

### Requête demandé par notre professeur
#### Top 5 des films qui ont été réalisés par Tarantino
```
    SELECT
      t.tconst AS tconst,
      t.primarytitle AS title,
      r.averagerating AS avg_rating
    FROM (
      SELECT nconst
      FROM projet_kdr_name_basics
      WHERE primaryname = ${director}
    ) nb JOIN projet_kdr_title_crew c ON array_contains(c.directors, nb.nconst)
    JOIN projet_kdr_title_ratings r ON c.tconst = r.tconst
    JOIN projet_kdr_title_basics t ON c.tconst = t.tconst
    ORDER BY r.averagerating DESC
    LIMIT 5;
```
Résultat : 
![image](https://user-images.githubusercontent.com/71653765/147707141-1487e59a-2a95-4884-8d6f-538296179017.png)
