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
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147776468-673026ad-78f0-4533-b874-a866783f1bf6.png)

#### Nombre d'acteurs qui sont nées en 1950, 1960, 1970,1980,1990
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147777284-8969c41f-4208-48ea-ba89-41c0e7e3f477.png)

---
# title.crew
### Visualisation de la table en Grafana
![image](https://user-images.githubusercontent.com/71117842/147785688-d061b8d2-fb4b-44c3-8afc-309753db21ab.png)

### Requêtes et résultats effectués

#### Combien d'écriteurs il y en a ?
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147785676-1dbda04f-06da-4758-b0d8-5d5b56414bcd.png)

#### combien des films ont réalisé chaque écrivain?
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147787100-e2e85ece-e9bb-4f50-ad88-89894380e33d.png)

---

# title.principals
### Visualisation de la table en Grafana
![image](https://user-images.githubusercontent.com/71117842/147790803-aac61799-f0b0-45e6-b5fa-b0248d184732.png)

### Requêtes et résultats effectués

![image](https://user-images.githubusercontent.com/71117842/147778148-34bafaf2-5c76-49e1-93f9-6adab6053701.png)

![image](https://user-images.githubusercontent.com/71117842/147778540-d164a5c4-b5dc-4a30-a673-3eac68c5158a.png)

### La réponse au pourcentage de film dans la base de donnée de IMDB est 33% 
Il s'agit d'un des graphiques que nous pouvons obtenir, il permet de répondre à la question : quel est la proportion de type de contenu que vous proposez ? 
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 

![image](https://user-images.githubusercontent.com/71117842/147707405-e2949695-682f-4758-a4a5-7fc6414d3a28.png)
---

# title.ratings
### Visualisation de la table en Grafana
![image](https://user-images.githubusercontent.com/71117842/147788915-936ef204-3777-4df4-abb8-b32340198dfa.png)

### Requêtes et résultats effectués
### La moyenne les plus hautes avec les votes effectués
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147789218-0ea3b0ed-1753-4c08-a9f1-41cf5c0925b8.png)
### Savoir le maximum de votes effectués
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147790172-3e718fe5-4539-46c8-a165-425a0a941ded.png)
### Savoir la moyenne de rating les plus votés par les utilisateurs
Ci-dessous, le résultat obtenu après avoir paramétré Grafana afin de joindre ces informations : 
![image](https://user-images.githubusercontent.com/71117842/147790361-9768d8da-b4f0-49b1-8a62-b76ee3d8b8a2.png)

---


