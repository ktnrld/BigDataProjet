# CONFIGURATION DE GRAFANA ET GOOGLE SHEETS

![image](https://user-images.githubusercontent.com/71117842/147694499-746fe4fe-a9f7-4f11-bdef-204b96183ec6.png)

```diff
+ Plugin Google Sheets officiel de Grafana Labs pour la communauté
```

https://grafana.com/grafana/plugins/grafana-googlesheets-datasource/installation

## EXIGENCES :

```diff
+ Docker
+ Compte google
+ Google Drive
+ Données sur des tableau GoogleSheet
```

## 1. Mise en place de Grafana dans un Docker Container

Démarrez le conteneur Docker en liant Grafana au port externe 3000 grâce à la commande :

```diff
docker run -d -p 3005:3000 --name=grafanaserver -e "GF_SECURITY_ADMIN_USER=admin" -e "GF_SECURITY_ADMIN_PASSWORD=admin" grafana/grafana:latest
```

Par exemple :
![image](https://user-images.githubusercontent.com/71117842/147665783-a748c60e-751c-49fe-b4fa-784ce1aa16a7.png)

Ensuite la page pour se loger s'ouvre comme nous avons renseigné le user = admn et password = admin.

![image](https://user-images.githubusercontent.com/71117842/147663542-3cb483bb-8abe-40e6-b1cd-2f409b30a709.png)

## 2. Installation du Plugin googlesheet en Grafana

Commande pour installer le Plugin Google Sheet:

```diff
docker exec -it grafanaserver bash
grafana-cli plugins install grafana-googlesheets-datasource
```

![image](https://user-images.githubusercontent.com/71117842/147665917-9c37c34e-7f39-4ef5-a91a-3c03c8183a1f.png)

Comment se indiqué on rédemarre Grafana :
![image](https://user-images.githubusercontent.com/71117842/147666035-a8c076c0-41aa-4857-aef5-f90a57ad4852.png)

et maintenant nous avons accès au plugin
![image](https://user-images.githubusercontent.com/71117842/147665226-211cae47-9b5f-4116-b4e4-759dfac12c9c.png)

Nous ne pouvons pas ouvrir le dataset il faut se loger avec le plugin actif
![image](https://user-images.githubusercontent.com/71117842/147666646-e5d72001-6c99-43e0-b1e2-11e8df2c1fb4.png)

### Générer la clé API dans Google Console Developer

1. Ouvrez la page Identifiants dans la console API Google.
2. Cliquez sur Créer des informations d'identification, puis sur la clé API.
   ![image](https://user-images.githubusercontent.com/71117842/147694946-6ab2999b-a449-4a09-9852-29dcd2412139.png)
3. Restreindre la clé API pour accéder uniquement à Google Drive et Google Sheets et enregistrer
   ![image](https://user-images.githubusercontent.com/71117842/147694977-011dbfc7-bfcc-44ed-9c45-a3a9d9cd3a12.png)
4. Copiez la clé et collez-la dans le champ Clé API de la source de données.
   ![image](https://user-images.githubusercontent.com/71117842/147666527-26fc3c96-8503-41a0-8a51-16e3be04e9c0.png)

## 3. Configuration de la feuille googlesheet en Grafana

### Rendre votre propre feuille Google publique

Allez simplement sur votre google Drive et sélectionnez votre feuille google, assurez-vous de cliquer sur partager et choisissez avancé en bas à droite
![image](https://user-images.githubusercontent.com/71117842/147695362-34bd7e9a-fe11-4a48-b708-c41c4a44461d.png)

```diff
https://docs.google.com/spreadsheets/d/1q2u8SYBjb3Q_uscxkK2UYAGE0LFKBfk-meOPO5w9EKY/edit?usp=sharing
```

### Construire le tableau de bord

Revenez à Garfana et choisissez Ajouter une requête
Dans les sources de données, sélectionnez Google Sheets, Spreadsheet ID est la valeur comprise entre "/d/" et "/edit" dans l'URL de votre feuille de calcul.

![image](https://user-images.githubusercontent.com/71117842/147695457-ba7e5360-ea4d-4d76-b9c8-b978217a16b3.png)

\*\* ID de feuille de calcul :

```diff
1q2u8SYBjb3Q_uscxkK2UYAGE0LFKBfk-meOPO5w9EKY
```

ID de la feuille de calcul — Sélectionnez celui spreadsheetIdqui est utilisé pour identifier la feuille de calcul à accéder ou à modifier.

Utiliser le filtre de temps - la première colonne sera filtrée par temps, vous pourrez filtrer toutes les lignes de la feuille de calcul qui se trouvent en dehors des limites de la plage de temps spécifiée dans le tableau de bord de Grafana.

## 3. Ecriture des requêttes et creation du dashboard en Grafana

![image](https://user-images.githubusercontent.com/71117842/147689504-7b05dbf3-5a03-4b56-92ee-f2ed31b04a85.png)
