# Tout savoir sur PDO

## C'est quoi PDO ?
`PDO` signifie PHP data objects, il est introduit depuis la version 5 de PHP. En gros, PDO est une interface de programmation qui permet d'utiliser différente système de base de donnée en executant des requêtes SQL.
PDO est compatible avec plusieurs système de base de donnée telle que : `MySQL`,`PostgreSQL`,`SQLite`, etc...

## Ce connecter à une base de donnée :
```PHP
$conn = new PDO('mysql:host=localhost;dbname=coursmysql', "root", "");
```
`mysql` -> Permet de spécifié le type de base de donnée,

`host=localhost` -> Permet de présicer qu'on se connecte en local à la base de donnée,

`dbname=coursmysql` -> Le nom de la base de donnée qu'on veux intégrer sur notre site (Ici elle s'appelle `coursmysql`),

`root` -> Spécifie l'utilisateur sur laquelle on veux ce connecter (En localhost l'utilisateur s'appelle toujours `root`),

`""` -> Le mot de passe qui permet de  se connecter à la base de donnée (Sur windows on n'a pas besoin de mot de passe en local).
