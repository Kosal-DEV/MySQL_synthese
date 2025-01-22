# Les commandes SQL
`SQL` (Structured Query Language) est un langage informatique utilisé pour interagir avec des bases de données relationnelles. Il permet de définir, manipuler, et interroger des données stockées dans une base de données. Avec `SQL`, tu peux effectuer des opérations comme l'ajout, la mise à jour, la suppression ou la récupération de données. Ce langage est essentiel pour gérer les bases de données de manière structurée et permet de créer des requêtes pour récupérer des informations précises de manière rapide et efficace.

Les commandes `SQL` sont généralement exécutées via un terminal (aussi appelé invite de commandes), qui est un outil permettant d'interagir avec le système informatique en ligne de commande. Dans ce terminal, tu peux saisir des instructions `SQL` qui seront envoyées à un serveur de base de données pour effectuer diverses actions, comme créer des tables, insérer des données ou récupérer des informations. Le terminal sert de point d'entrée pour interagir avec la base de données, en envoyant des commandes qui sont ensuite traitées par le serveur. Cela offre une méthode directe et puissante pour manipuler les bases de données, souvent utilisée par les développeurs, administrateurs de bases de données et autres professionnels.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

### 1. Ce connecter à MySQL via l'invite de commande :
```SQL
mysql -u root -p;
```
- `mysql` : C'est le programme client qui permet de se connecter à un serveur MySQL et d'exécuter des commandes SQL.
- `-u root` : L'option -u spécifie l'utilisateur avec lequel tu souhaites te connecter à la base de données. Dans cet exemple, l'utilisateur est `root`, qui est souvent le compte administrateur par défaut de MySQL.
- `-p` : Cette option indique que le programme doit te demander un mot de passe pour l'utilisateur `root`. Après avoir exécuté la commande, tu seras invité à entrer le mot de passe de l'utilisateur `root`.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 2. Pour voir les bases de données existantes :
```SQL
SHOW databases;
```
- Cette commande est très utile pour visualiser les bases de données existantes sur le serveur avant d'effectuer d'autres opérations, comme sélectionner une base de données spécifique avec `USE`, ou créer de nouvelles bases de données.
- Elle te permet de vérifier si la base de données sur laquelle tu veux travailler existe déjà ou non.

*Voici ce que retourne la commande :*
```SQL
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| my_database        |
+--------------------+
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 3. Pour selectionner la base de données sur laquelle nous voulons travailler :
```SQL
USE nomDB;
```
- Sélection de la base de données : Cette commande est essentielle lorsque tu travailles avec plusieurs bases de données sur un même serveur. Elle permet de spécifier sur quelle base de données tu souhaites effectuer des opérations.
- Facilité de gestion : Une fois que tu as sélectionné la base de données, tu n'as plus besoin de spécifier son nom dans chaque requête. Par exemple, pour insérer une donnée dans une table, tu n'as qu'à indiquer la table, pas le nom de la base de données.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 4. Pour voir les TABLES qu'il y'a dans notre base de donnée :
```SQL
SHOW tables;
```
- Lorsque tu exécutes cette commande, MySQL te montre toutes les tables qui existent dans la base de données sur laquelle tu as effectué un `USE` préalable.
- Si tu n'as pas sélectionné de base de données, tu obtiendras une erreur.

*Voici ce que retourne la commande :*
```SQL
+-------------------+
| Tables_in_nomDB   |
+-------------------+
| users             |
| products          |
| orders            |
+-------------------+
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 5. Pour afficher la structure d'une table :
```SQL
DESCRIBE nomTable;
```
- Lorsque tu exécutes la commande `DESCRIBE` suivie du nom d'une table (par exemple `users`), MySQL renvoie une description détaillée de la structure de cette table.

*Voici ce que retourne la commande pour une table `users` :*
```SQL
+------------+-------------+------+-----+---------+----------------+
| Field      | Type        | Null | Key | Default | Extra          |
+------------+-------------+------+-----+---------+----------------+
| id         | int(11)     | NO   | PRI | NULL    | auto_increment |
| firstname  | varchar(100)| NO   |     | NULL    |                |
| lastname   | varchar(100)| NO   |     | NULL    |                |
| email      | varchar(100)| YES  | UNI | NULL    |                |
| created_at | datetime    | NO   |     | NULL    |                |
+------------+-------------+------+-----+---------+----------------+
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 6. Pour afficher les enregistrements d'une table :
```SQL
SELECT * FROM nomTable;
```
- `SELECT` : Cette commande est utilisée pour sélectionner des données dans une base de données.
- `*` : Ce symbole signifie "toutes les colonnes". Cela indique à MySQL de renvoyer toutes les colonnes de chaque ligne de la table spécifiée.
- `FROM nomTable` : Cette partie indique de quelle table les données doivent être extraites (ici, la table s'appelle nomTable).

*Voici ce que retourne la commande pour une table `users`* :
```SQL
+----+-----------+----------+----------------------+
| id | firstname | lastname | email                |
+----+-----------+----------+----------------------+
|  1 | John      | Doe      | john.doe@mail.com     |
|  2 | Jane      | Smith    | jane.smith@mail.com   |
|  3 | Mike      | Johnson  | mike.johnson@mail.com |
+----+-----------+----------+----------------------+
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 7. Créer une base de donnée :
```SQL
CREATE DATABASE nomDB DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```
- `CREATE DATABASE` : Cette partie de la commande permet de créer une nouvelle base de données.
- `nomDB` : C'est le nom de la base de données que tu souhaites créer. Remplace `nomDB` par le nom réel que tu veux donner à la base de données.
- `DEFAULT CHARACTER SET utf8mb4` : Cette partie définit l'encodage des caractères par défaut pour la base de données à utf8mb4, qui est un encodage capable de stocker des caractères Unicode sur 4 octets.
`utf8mb4` est l'encodage recommandé pour garantir la prise en charge de tous les caractères Unicode, y compris les emoji et certains caractères spéciaux, contrairement à `utf8`, qui ne prend en charge que jusqu'à 3 octets.
- `COLLATE utf8mb4_general_ci` : `COLLATE` définit le jeu de caractères de la base de données, c'est-à-dire comment les caractères doivent être comparés et triés.
`utf8mb4_general_ci` est une collation sensible à la casse (ci pour "case-insensitive"), utilisée pour le tri et la comparaison de chaînes de caractères.
Cette collation est une option générique pour les langues et caractères qui n'ont pas de règles de tri spécifiques. Elle est souvent utilisée comme valeur par défaut.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 8. Supprimer une base de donnée :
```SQL
DROP DATABASE nomDB;
```
- `DROP DATABASE` : Cette instruction supprime complètement la base de données spécifiée.
- `nomDB` : Il s'agit du nom de la base de données que tu souhaites supprimer. Assure-toi de remplacer `nomDB` par le nom réel de la base de données que tu veux supprimer.

**ATTENTION : supprimer une base de donnée est irrévérsible !**

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 9. Créer une table users dans la base de données avec 5 champs :
```SQL
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  firstname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL,
  lastname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL,
  gender ENUM('M','F','X') COLLATE utf8mb4_general_ci NOT NULL,
  date_of_birth DATE NOT NULL
) ENGINE = InnoDB;
```
- `CREATE TABLE users` : Cette partie de la commande crée une nouvelle table nommée `users`.

`id INT AUTO_INCREMENT PRIMARY KEY` :
- `id` : Le nom de la colonne.
- `INT` : Le type de données de cette colonne est un entier.
- `AUTO_INCREMENT` : Cette option indique que la valeur de cette colonne va s'auto-incrémenter à chaque nouvelle insertion (utile pour les identifiants uniques).
- `PRIMARY KEY` : Cela définit cette colonne comme la clé primaire de la table. Une clé primaire assure que les valeurs de la colonne id seront uniques et non nulles, garantissant ainsi l'intégrité des données.

`firstname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL` :
- `firstname` : Le nom de la colonne.
- `VARCHAR(255)` : Le type de données est une chaîne de caractères de longueur variable, avec une longueur maximale de 255 caractères.
- `COLLATE utf8mb4_general_ci` : Cette option spécifie que les valeurs dans cette colonne doivent être encodées en utilisant le jeu de caractères utf8mb4 et la collation utf8mb4_general_ci, qui est insensible à la casse et adaptée pour la prise en charge des caractères Unicode.
- `NOT NULL` : Cela garantit que cette colonne ne pourra pas contenir de valeurs nulles.

`lastname VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL` :
- De même que pour `firstname`, cette colonne va stocker les noms de famille des utilisateurs. Elle a également une longueur maximale de 255 caractères, utilise la même collation, et ne permet pas les valeurs nulles.

`gender ENUM('M', 'F', 'X') COLLATE utf8mb4_general_ci NOT NULL` :
- `gender` : Le nom de la colonne.
- `ENUM('M', 'F', 'X')` : Le type de données est un ENUM, qui permet de définir un ensemble limité de valeurs possibles. Dans ce cas, seules les valeurs 'M', 'F' ou 'X' sont autorisées (respectivement pour "Masculin", "Féminin" et "Autre").
- `COLLATE utf8mb4_general_ci` : La collation spécifiée est utf8mb4_general_ci.
- `NOT NULL` : Comme pour les autres colonnes, cette colonne ne peut pas contenir de valeurs nulles.

`date_of_birth DATE NOT NULL` :
- `date_of_birth` : Le nom de la colonne.
- `DATE` : Le type de données est une date, qui stocke la date de naissance dans un format `YYYY-MM-DD`.
- `NOT NULL` : Cette colonne est également définie comme `NOT NULL`, ce qui signifie qu'une date de naissance doit toujours être fournie lors de l'insertion des données.

`ENGINE = InnoDB` :
- `ENGINE = InnoDB` spécifie que la table doit utiliser le moteur de stockage InnoDB, qui est le moteur par défaut dans MySQL. InnoDB prend en charge les transactions, les clés étrangères, et l'intégrité des données, ce qui le rend adapté pour des applications nécessitant une gestion avancée des données.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 10. Créer un champ "adresse" dans notre table users :
```SQL
ALTER TABLE users ADD address VARCHAR(255) COLLATE utf8mb4_general_ci NOT NULL; 
```
Cette commande ajoute une colonne `address` de type chaîne de caractères (avec une longueur maximale de 255 caractères) à la table `users`, en veillant à ce que cette colonne ne puisse pas contenir de valeur `NULL` et que le texte soit stocké avec l'encodage `UTF-8`.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 11. Supprimer un champ de notre base de donnée :
```SQL
ALTER TABLE nomTable DROP nomChamp; 
```
La commande permet de supprimer une colonne (champ) de la table `nomTable`. Une fois la commande exécutée, la colonne `nomChamp` et toutes les données qu'elle contient seront supprimées de manière définitive.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 12. Modifier le nom d'une table :
```SQL
ALTER TABLE nomDeLaTable RENAME AS nouveauNomDeLaTable;
```
Cette command permet de modifier le nom d'une table.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 13. Voir une commande utilisée poue créer une table :
```SQL
SHOW CREATE TABLE users;
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 14. Créer 5 enregistrements dans notre base de donnée users :
```SQL
INSERT INTO users VALUES
 ('null', 'Jessica', 'Biel', 'F', 1985-11-02, 'Los Angeles', 59),
 ('null', 'Mohamed', 'Salah', 'M', 1989-03-10, 'Caire', 80),
 ('null', 'Sadio', 'Mané', 'M', 1990-05-17, 'Dakar', 82),
 ('null', 'Nathan', 'Drake', 'X', 2010-06-30, 'El Dorado', 75),
 ('null', 'Angelina', 'Jolie', 'F', 1973-09-21, 'Texas', 55);
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 15. Modifier une table pour ajouter une clé id pour créer une relation entre les tables :
```SQL
ALTER TABLE articles ADD id_user_article INT NOT NULL ;
```
`ALTER` permet de modifier la table,
`articles` est le nom de la table,
`ADD` permet de faire un ajout,
`id_user_article` le nom de la clé étrangére

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### 16. 
