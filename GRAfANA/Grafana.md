# GRAFANA

## Pourquoi grafana
Grafana est un logiciel libre sous licence GNU Affero General Public License Version 3 qui permet la visualisation de données. Il permet de réaliser des tableaux de bord et des graphiques depuis plusieurs sources dont des bases de données temporelles comme Graphite, InfluxDB et OpenTSDB.

## Télécharger Grafana
```
    https://grafana.com/docs/grafana/latest/installation/
```
Nous avons ensuite continué l'installation. 

## Télécharger  le plug-in Azure Data Explorer
```
    https://grafana.com/grafana/plugins/grafana-azure-data-explorer-datasource/
```
## localhost:3000
Nous sommes par la suite allés sur localhost:3000.
Nous avons entré admin admin, puis nous avons changé notre mot de passe.
![graphana](https://user-images.githubusercontent.com/71653765/147603923-939e4a7e-2e0a-4b45-96bc-6e7e8ba6cd2f.png)

## Ajout une source de donnée
![source](https://user-images.githubusercontent.com/71653765/147604145-9fcb9f55-685a-47ed-b090-8e15cf253edd.png)
On télécharge le plug-in csv afin de pouvoir y mettre nos tables.
![csv](https://user-images.githubusercontent.com/71653765/147604302-f73fe90f-6e91-4e76-a467-a6e821b0e5c6.png)

Nous mettons ensuite nos tables qui sont conservés en local.
![csvtitre](https://user-images.githubusercontent.com/71653765/147604442-8c9f6aa5-85ba-48d7-a697-0b8e2406405d.png)

## Création d'un dashboard
Nous nous rendons sur l'icone création d'un dashboard.
![dashboard](https://user-images.githubusercontent.com/71653765/147604550-8a345bf7-73ae-499d-b2d1-0ede9fd80358.png)
