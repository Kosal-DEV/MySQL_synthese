## Les commandes SQL
1. Créer une database :
```SQL
CREATE DATABASE NomDB DEFAULT CHARACTER SET utf8mb3;
```
2. Supprimer une base de donnée :
```SQL
DROP DATABASE nomDB;
```
3. Créer une table dans la base de données avec 4 champs :
```SQL
CREATE TABLE nomTable
(firstname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL,lastname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL,
gender ENUM('M','F','X') COLLATE utf8mb4_general_ci NOT NULL,date_of_birth DATE NOT NULL ) ENGINE = InnoDB;
```
4. Créer un champ "adresse" dans notre table :
```SQL
ALTER TABLE users ADD address VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL ; 
```
