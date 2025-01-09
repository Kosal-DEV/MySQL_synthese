## Les commandes SQL
**1. Créer une database :**
```SQL
CREATE DATABASE nomDB DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```
**2. Supprimer une base de donnée :**
```SQL
DROP DATABASE nomDB;
```
**3. Créer une table dans la base de données avec 4 champs :**
```SQL
CREATE TABLE nomTable (
  id INT AUTO_INCREMENT PRIMARY KEY,
  firstname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL,
  lastname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL,
  gender ENUM('M','F','X') COLLATE utf8mb4_general_ci NOT NULL,
  date_of_birth DATE NOT NULL
) ENGINE = InnoDB;
```
**4. Créer un champ "adresse" dans notre table :**
```SQL
ALTER TABLE users ADD address VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL; 
```
**5. Supprimer un champ de notre base de donnée :**
```SQL
ALTER TABLE nomTable DROP nomChamp; 
```
**6. Ce connecter à MySQL via l'invite de commande :**
```SQL
mysql -u root -p;
```
**7. Pour voir les DATABASES de disponible :**
```SQL
SHOW databases;
```
**8. Pour selectionner la DATABASES sur laquelle nous voulons travailler :**
```SQL
USE nomDB;
```
**9. Pour voir les TABLES qu'il y'a dans notre DATABASE :**
```SQL
SHOW tables;
```
**10. Pour afficher la structure d'une table :**
```SQL
DESCRIBE nomTable;
```
**11. Pour afficher les enregistrements dans une table :**
```SQL
SELECT * FROM nomTable;
```
