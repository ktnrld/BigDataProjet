# RESULTATS DE REQUETES. 
Nous avons testé les deux configurations avec grafana à savoir la connection avec le plugin GoogleSheet et le plugin CSV.
Nous avons pris connaissance du logiciel grafana, et nous avons commencé à tester nos tables.
Tout d'abord, nous avons affiché nos 4 tables (reduites parce que avec la version free de grafana tout le dataset de IMDB était trop loud). Nous avons opté pour réduire les tables à 10000 lignes.

Ensuite nous avons lancé des requêtes sur les tables. Regardons plus en détails les résultats:
# names.basics
### Visualisation de la table en Grafana
![image](https://user-images.githubusercontent.com/71117842/147782243-d5b21b7d-e1c6-4b4b-851d-8adb5c1f34b2.png)

### Requêtes et résultats effectués

#### Combien d'acteurs et actrices il y en a?

![image](https://user-images.githubusercontent.com/71117842/147776468-673026ad-78f0-4533-b874-a866783f1bf6.png)

#### Nombre d'acteurs qui sont nées en 1950, 1960, 1970,1980,1990

![image](https://user-images.githubusercontent.com/71117842/147777284-8969c41f-4208-48ea-ba89-41c0e7e3f477.png)
# title.crew
### Visualisation de la table en Grafana
### Requêtes et résultats effectués

# title.principals
### Visualisation de la table en Grafana
### Requêtes et résultats effectués

# title.ratings
### Visualisation de la table en Grafana
### Requêtes et résultats effectués

### La réponse au pourcentage de film dans la base de donnée de IMDB est 33% 
Il s'agit d'un des graphiques que nous pouvons obtenir, il permet de répondre à la question : quel est la proportion de type de contenu que vous proposez ? 
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147707405-e2949695-682f-4758-a4a5-7fc6414d3a28.png)


![image](https://user-images.githubusercontent.com/71117842/147770387-f4bc69c3-3b9f-49e4-b947-4afb2503523f.png)
![image](https://user-images.githubusercontent.com/71117842/147771603-96f8b0bb-007f-4710-8463-bbb956e8a3d3.png)

![image](https://user-images.githubusercontent.com/71117842/147778148-34bafaf2-5c76-49e1-93f9-6adab6053701.png)

![image](https://user-images.githubusercontent.com/71117842/147778540-d164a5c4-b5dc-4a30-a673-3eac68c5158a.png)

