📌 Présentation générale

Ce projet consiste à développer une application Java dédiée à la gestion des employés et de leurs salaires au sein de l’entreprise OCP.
L’application met en pratique les concepts de la programmation orientée objet et s’appuie sur :

JavaFX pour l’interface graphique

JDBC + MySQL pour la gestion et la persistance des données

Elle permet de gérer différents types d’employés, avec prise en compte des règles de calcul de salaire et des cas particuliers tels que les employés « à risque ».

📁 Structure du projet
src/
│── basedonne.sql
│── Main.java
│
├── connection/
│   └── DBConnection.java
│
├── Controller/
│   └── Controller.java
│
├── implementation/
│   └── GestionEmployeDB.java
│
├── modele/
│   ├── Employe.java
│   ├── Commercial.java
│   ├── Vendeur.java
│   ├── Representant.java
│   ├── Producteur.java
│   ├── Manutentionnaire.java
│   ├── ProdARisque.java
│   ├── ManutARisque.java
│   └── PrimeR.java
│
└── view/
    └── Interface.fxml

🧩 Description des composants
🔹 Main.java

Point d’entrée de l’application.
Il initialise JavaFX, charge l’interface graphique et affiche la fenêtre principale.

🔹 Base de données (basedonne.sql)

Script SQL permettant de :

créer la base de données MySQL,

définir les tables nécessaires,

initialiser la structure utilisée par l’application.

🔹 Connexion à la base (connection/)

DBConnection.java
Gère la connexion JDBC à MySQL (URL, identifiants, driver).
Utilisée par la couche d’accès aux données.

🔹 Contrôleur JavaFX (Controller/)

Controller.java
Assure la liaison entre l’interface graphique et la logique métier :

récupération des données saisies,

validation des champs,

gestion des événements (boutons),

appel des méthodes CRUD via la couche DAO.

🔹 Accès aux données (implementation/)

GestionEmployeDB.java
Implémente les opérations CRUD (Create, Read, Update, Delete) sur la table Employe.
Utilise JDBC pour exécuter les requêtes SQL.

🔹 Modèle métier (modele/)

Contient les classes représentant les différents types d’employés :

Employe : classe de base

Commercial, Vendeur, Representant

Producteur, Manutentionnaire

ProdARisque, ManutARisque : variantes avec prime de risque

PrimeR : gestion de la prime de risque

Chaque classe implémente ou spécialise le calcul du salaire selon le type d’employé.

🔹 Interface graphique (view/)

Interface.fxml
Définit l’interface utilisateur en JavaFX (champs de saisie, choix du type d’employé, options « à risque », boutons d’actions).
Liée au contrôleur via fx:controller.

🔄 Fonctionnement global

L’application démarre depuis Main.java.

L’interface graphique est chargée via Interface.fxml.

Le contrôleur traite les actions utilisateur.

Les objets métier sont créés selon le type d’employé.

Les données sont enregistrées ou récupérées depuis MySQL via JDBC.

⚠️ Remarques importantes

Seuls Producteur et Manutentionnaire peuvent être marqués comme employés « à risque ».

La structure de la base de données doit rester cohérente avec les requêtes JDBC.

Les identifiants de connexion doivent être configurés dans DBConnection.java.

▶️ Exécution du projet
Prérequis

Java 8 ou supérieur

JavaFX

MySQL

MySQL Connector/J (JDBC)

Étapes

Exécuter le script basedonne.sql dans MySQL.

Configurer la connexion dans DBConnection.java.

Lancer Main.java.
