## 1. Mise en place de Grafana dans un Docker Container

Démarrez le conteneur Docker en liant Grafana au port externe 3000 grâce à la commande :

```diff
docker run -d -p 3001:3000 --name=grafanaserver -e "GF_SECURITY_ADMIN_USER=admin" -e "GF_SECURITY_ADMIN_PASSWORD=admin" grafana/grafana:latest
```

Par exemple :
![image](https://user-images.githubusercontent.com/71117842/147665783-a748c60e-751c-49fe-b4fa-784ce1aa16a7.png)

Ensuite la page pour se loger s'ouvre comme nous avons renseigné le user = admn et password = admin.

![image](https://user-images.githubusercontent.com/71117842/147663542-3cb483bb-8abe-40e6-b1cd-2f409b30a709.png)

## 2. Installation du Plugin CVS en Grafana

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

![image](https://user-images.githubusercontent.com/71117842/147666527-26fc3c96-8503-41a0-8a51-16e3be04e9c0.png)

## 3. Configuration du CSV datasource en Grafana

```diff
https://docs.google.com/spreadsheets/d/1q2u8SYBjb3Q_uscxkK2UYAGE0LFKBfk-meOPO5w9EKY/edit?usp=sharing
```

## 3. Ecriture des requêttes et creation du dashboard en Grafana

![image](https://user-images.githubusercontent.com/71117842/147689504-7b05dbf3-5a03-4b56-92ee-f2ed31b04a85.png)
