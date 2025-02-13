# Gestion des Dates en SQL

## 1. Types de Données pour les Dates

En SQL, les types de données couramment utilisés pour stocker les dates sont :

- **DATE** : Stocke uniquement une date (AAAA-MM-JJ).
- **TIME** : Stocke uniquement une heure (HH:MI:SS).
- **DATETIME** : Stocke une date et une heure combinées (AAAA-MM-JJ HH:MI:SS).
- **TIMESTAMP** : Similaire à DATETIME, mais avec un fuseau horaire et utilisé pour l'enregistrement d'événements.

## 2. Fonctions Utiles pour les Dates

### a. Récupération de la Date et Heure Actuelles

```sql
SELECT NOW(); -- Renvoie la date et l'heure actuelles
SELECT CURDATE(); -- Renvoie uniquement la date actuelle
SELECT CURTIME(); -- Renvoie uniquement l'heure actuelle
```

### b. Extraction de Parties d'une Date

```sql
SELECT YEAR(NOW()); -- Année
SELECT MONTH(NOW()); -- Mois
SELECT DAY(NOW()); -- Jour
SELECT HOUR(NOW()); -- Heure
SELECT MINUTE(NOW()); -- Minute
SELECT SECOND(NOW()); -- Seconde
```

### c. Manipulation des Dates

```sql
SELECT DATE_ADD(NOW(), INTERVAL 7 DAY); -- Ajoute 7 jours à la date actuelle
SELECT DATE_SUB(NOW(), INTERVAL 1 MONTH); -- Soustrait 1 mois à la date actuelle
```

### d. Calcul de la Différence entre Deux Dates

```sql
SELECT DATEDIFF('2025-12-31', '2025-01-01'); -- Différence en jours
SELECT TIMEDIFF('12:00:00', '08:30:00'); -- Différence en heures/minutes/secondes
```

## 3. Filtrer avec des Dates dans une Requête

```sql
SELECT * FROM commandes WHERE date_commande = '2025-02-13';
SELECT * FROM commandes WHERE date_commande BETWEEN '2025-01-01' AND '2025-01-31';
SELECT * FROM commandes WHERE YEAR(date_commande) = 2025;
```

## 4. Formatage des Dates

```sql
SELECT DATE_FORMAT(NOW(), '%d/%m/%Y'); -- Format jour/mois/année
SELECT DATE_FORMAT(NOW(), '%W, %M %d, %Y'); -- Format avec jour et mois en texte
```

## Conclusion

La gestion des dates en SQL est essentielle pour manipuler les données temporelles. En utilisant les types de données appropriés et les fonctions dédiées, il est possible d'exécuter des calculs précis et de filtrer les résultats efficacement.
