# WebCaisseFX - Prototype JavaFX / JDBC (Mission 4)

Ce dépôt contient le code source de l'application **WebCaisseFX**, développée dans le cadre de l'étude de cas WebCaisse (Mission 4). 

L'objectif de ce prototype est de démontrer la mise en pratique d'une interface graphique en **JavaFX** reliée à une base de données **MySQL** de façon sécurisée (prévention des Injections SQL via l'utilisation de `PreparedStatement`), ainsi que de tester la logique métier via **JUnit 5**.

## Fonctionnalités

*   **Interface Graphique (JavaFX)** : Formulaire de recherche des consommateurs réguliers (non fidélisés).
*   **Accès aux données (DAO)** : Requête sécurisée vers la base MySQL pour récupérer les clients selon le nombre de ventes sur une période.
*   **Modèle Objet** : Classes `Conso` et `ConsoFidele` héritant des propriétés du consommateur.
*   **Tests Unitaires** : Tests automatisés validant la logique de calcul des points de fidélité selon 3 tranches d'achats (JUnit 5).

## Technologies Utilisées

*   **Java 17** (minimum)
*   **JavaFX 21**
*   **MySQL Connector/J 8.0**
*   **JUnit 5 (Jupiter)**
*   **Maven** pour la gestion des dépendances et du cycle de vie du projet.

## Prérequis

1.  Avoir un serveur **MySQL** local actif (XAMPP, WAMP, Laragon, etc.) sur le port par défaut (3306) avec un utilisateur `root` et un mot de passe vide (ou ajuster ces paramètres dans `GrcDAO.java`).
2.  Exécuter le script SQL fourni dans l'étude de cas (Mission 4.1) pour créer la base `webcaisse` et insérer le jeu d'essai.

## Comment exécuter l'application

### Depuis un IDE (IntelliJ IDEA, Eclipse, VS Code)

Ce projet est configuré avec **Maven**, ce qui signifie que le téléchargement des bibliothèques JavaFX et MySQL se fera automatiquement.

1.  Ouvrez ce dossier `WebCaisseFX` dans votre IDE préféré.
2.  Laissez Maven télécharger les dépendances (cela peut prendre quelques secondes la première fois).
3.  ⚠️ **Important** : Pour lancer l'application, exécutez la classe **`webcaisse.Launcher`** (et non `Main.java`) afin de contourner les restrictions liées aux modules Java (JPMS).

### Exécuter les tests unitaires

*   Dans le répertoire `src/test/java/webcaisse/modele/`, exécutez la classe `TestPointsFidelite.java` avec le moteur de test de votre IDE pour vérifier la fiabilité du calcul des points de fidélité.

## Structure du Projet

```text
src/
├── main/
│   ├── java/webcaisse/
│   │   ├── controleur/RechercheController.java  # Le contrôleur JavaFX
│   │   ├── dao/GrcDAO.java                      # L'accès à la base de données sécurisé
│   │   ├── modele/Conso.java                    # Le modèle client
│   │   ├── modele/ConsoFidele.java              # Le modèle client VIP
│   │   ├── Launcher.java                        # Le point d'entrée pour contourner les modules JPMS
│   │   └── Main.java                            # La configuration de l'application JavaFX
│   └── resources/webcaisse/vue/
│       └── recherche.fxml                       # L'interface graphique
└── test/
    └── java/webcaisse/modele/
        └── TestPointsFidelite.java              # Les tests métier (JUnit)
```
