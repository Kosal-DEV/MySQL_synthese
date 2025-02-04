# 🔑 Clé étrangère et relations en MySQL

## 1️⃣ Clé étrangère (FOREIGN KEY)
Une **clé étrangère** est une colonne qui fait référence à la **clé primaire** d'une autre table. Elle garantit **l'intégrité référentielle**, empêchant des incohérences dans la base de données.

### ✅ Exemple :
```sql
CREATE TABLE departements (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL
);

CREATE TABLE employes (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL,
    departement_id INT,
    FOREIGN KEY (departement_id) REFERENCES departements(id)
);
```
**Explication** :
- `departement_id` est une clé étrangère qui référence `id` dans `departements`.
- Un employé appartient à un seul département existant.

---

## 2️⃣ Types de relations en MySQL

### 🔹 1. Relation **1 à 1** (One-to-One)
Un enregistrement dans une table correspond à **un seul** enregistrement dans une autre table.

#### ✅ Exemple :
```sql
CREATE TABLE utilisateurs (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL
);

CREATE TABLE cartes_identite (
    id INT PRIMARY KEY AUTO_INCREMENT,
    utilisateur_id INT UNIQUE,
    numero VARCHAR(50) NOT NULL,
    FOREIGN KEY (utilisateur_id) REFERENCES utilisateurs(id)
);
```
➡️ Chaque utilisateur a **au plus** une carte d’identité.

---

### 🔹 2. Relation **1 à plusieurs** (One-to-Many)
Un enregistrement dans la première table correspond à **plusieurs** enregistrements dans la deuxième table, mais **chaque enregistrement dans la deuxième table appartient à un seul enregistrement de la première**.

#### ✅ Exemple :
```sql
CREATE TABLE departements (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL
);

CREATE TABLE employes (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL,
    departement_id INT,
    FOREIGN KEY (departement_id) REFERENCES departements(id)
);
```
➡️ Un département peut contenir **plusieurs employés**.

---

### 🔹 3. Relation **plusieurs à plusieurs** (Many-to-Many)
Chaque enregistrement dans une table peut être lié à **plusieurs enregistrements** dans l'autre table, et **vice versa**.

#### ✅ Exemple :
```sql
CREATE TABLE etudiants (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL
);

CREATE TABLE cours (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL
);

CREATE TABLE etudiant_cours (
    etudiant_id INT,
    cours_id INT,
    PRIMARY KEY (etudiant_id, cours_id),
    FOREIGN KEY (etudiant_id) REFERENCES etudiants(id),
    FOREIGN KEY (cours_id) REFERENCES cours(id)
);
```
➡️ La table **intermédiaire `etudiant_cours`** gère l'association entre les étudiants et les cours.

---

## ✅ **Résumé des relations**

| Type de relation | Exemple | Clé étrangère |
|-----------------|----------|--------------|
| **1 à 1** | Un utilisateur a une seule carte d'identité | `utilisateur_id` dans `cartes_identite` |
| **1 à plusieurs** | Un département a plusieurs employés | `departement_id` dans `employes` |
| **Plusieurs à plusieurs** | Un étudiant suit plusieurs cours | `etudiant_id` et `cours_id` dans `etudiant_cours` |

---

🔥 **Prochaine étape** : Apprendre à utiliser ces relations avec les **jointures** (`JOIN`) en SQL !
