# Architectures monolithiques et monolithes modulaires : CampusLibrary

Un projet conceptuel sur les architectures **monolithiques** et **monolithiques modulaires**. Aucun code n'est demandé : le travail porte sur la compréhension des concepts, l'analyse d'architectures, la lecture de diagrammes et la conception de diagrammes.

## Objectifs

À la fin du projet, vous devez être capable de :

- Définir un monolithe et un monolithe modulaire, et expliquer ce qu'est une unité de déploiement
- Identifier les avantages, les limites et les contextes adaptés d'un monolithe
- Distinguer un module d'un microservice, et la modularité du déploiement
- Expliquer la cohésion, le couplage, les dépendances internes et les dépendances circulaires
- Comprendre la propriété logique des données au-dessus d'une base de données physique commune
- Distinguer une information visible d'une hypothèse lors de la lecture d'un diagramme
- Concevoir un diagramme de monolithe et un diagramme de monolithe modulaire, et le faire évoluer face à de nouvelles contraintes

## Concepts clés

| Concept | Résumé |
|---|---|
| **Monolithe** | Une application principale déployée comme une seule unité. Elle peut tout de même contenir de nombreuses fonctionnalités, couches, modules, types d'utilisateurs et intégrations externes. |
| **Monolithe modulaire** | Un monolithe qui reste une seule unité de déploiement mais qui est organisé en modules métier avec des frontières internes explicites. |
| **Module** | Un groupe cohérent de responsabilités, nommé d'après le métier (par exemple `Comptes`, `Catalogue`), et non d'après des rôles techniques (`Utils`, `Helpers`). |
| **Cohésion** | Le degré de proximité entre les responsabilités d'un même module. Une forte cohésion est recherchée. |
| **Couplage** | Le niveau de dépendance entre les modules. Les dépendances doivent être nécessaires, explicites et limitées. |
| **Dépendance circulaire** | Une chaîne de dépendances qui revient à son point de départ (A → B → C → A). Elle rend le système plus difficile à comprendre et à faire évoluer. |
| **Propriété logique des données** | Chaque module est propriétaire de ses données, même lorsque tous les modules partagent une même base de données physique. |

**Monolithe contre monolithe modulaire**

| | Monolithe | Monolithe modulaire |
|---|---|---|
| Déploiement | Une seule unité | Une seule unité |
| Organisation interne | Variable | Modules métier explicites |
| Dépendances | Pas nécessairement visibles | Visibles et maîtrisées |
| Données | Pas nécessairement structurées | Propriété logique par module |
| Montée en charge | Généralement globale | Généralement globale |

**Avantages possibles d'un monolithe :** déploiement simple, communication interne simple, exploitation facile pour de petites équipes, infrastructure initiale limitée.

**Limites possibles :** déploiement et montée en charge globaux, complexité interne croissante, nombreuses dépendances, coordination entre équipes, impact étendu des défaillances.

> Il n'existe pas d'architecture universellement meilleure. Le bon choix dépend des besoins, des contraintes, des responsabilités, des dépendances et des compromis.

## Cas pratique : CampusLibrary

Une université souhaite créer **CampusLibrary**, une application de gestion de bibliothèque, livrée comme une unité de déploiement principale.

**Les étudiants** peuvent consulter le catalogue, vérifier la disponibilité d'un document, réserver un document, consulter leurs emprunts et renouveler un emprunt lorsque cela est autorisé.

**Les bibliothécaires** peuvent ajouter et modifier des documents, enregistrer des emprunts et des retours, consulter les réservations et gérer certaines pénalités.

**L'application gère :** les comptes, les rôles, le catalogue, les prêts, les retours, les réservations, les pénalités, les notifications et la traçabilité des opérations sensibles.

**Contraintes :** une seule unité de déploiement principale ; aucune technologie, aucun langage ni aucun framework imposé ; aucun diagramme de classes et aucun code ; responsabilités lisibles ; dépendances importantes visibles ; systèmes externes clairement distingués.

## Livrables

Trois diagrammes, stockés dans le répertoire [`diagrammes/`](diagrammes) :

| # | Fichier | Description |
|---|---|---|
| 1 | `diagramme_1_monolith.jpg` | Vue globale de CampusLibrary sans structure interne. Montre l'Étudiant, le Bibliothécaire, CampusLibrary, le Stockage et le service externe de notification. |
| 2 | `diagramme_2_modulaire_simple.jpg` | Vue modulaire. Montre la frontière de CampusLibrary, les modules métier à l'intérieur (comptes et rôles, catalogue, prêts et retours, réservations, pénalités, notifications, audit), les acteurs et le fournisseur de notification à l'extérieur, et une unité de déploiement commune. |
| 3 | `diagramme_3_modulaire_avance.jpg` | Ajoute les principales dépendances entre modules et la propriété logique des données (données Comptes, Catalogue, Prêts, Réservations, Pénalités et Audit) sur une base de données physique commune. |

### Aperçus

![Diagramme 1 - Monolithe](diagrammes/diagramme_1_monolith.jpg)
![Diagramme 2 - Monolithe modulaire simple](diagrammes/diagramme_2_modulaire_simple.jpg)
![Diagramme 3 - Monolithe modulaire avancé](diagrammes/diagramme_3_modulaire_avance.jpg)

## Structure du dépôt

```text
holbertonschool-architectures_monoliths_modulaires/
├── README.md
└── diagrammes/
    ├── diagramme_1_monolith.jpg
    ├── diagramme_2_modulaire_simple.jpg
    └── diagramme_3_modulaire_avance.jpg
```

## Conseils pour les diagrammes

- Commencer par les acteurs, puis le système, puis ses responsabilités
- Regrouper les responsabilités étroitement liées et utiliser des noms métier
- Ne dessiner que les dépendances utiles, avec un sens de flèche clair
- Distinguer les modules, les données et les systèmes externes
- Ne pas supposer que les modules sont des services indépendants, ni qu'une base de données commune empêche la modularité
- Ne pas ajouter de technologies qui n'ont pas été demandées

## Ressources

- [Microsoft Learn : Architectures d'applications web courantes](https://learn.microsoft.com/fr-fr/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures) (FR)
- [Martin Fowler : Monolith First](https://martinfowler.com/bliki/MonolithFirst.html) (EN)
- [C4 Model : Diagrams](https://c4model.com/diagrams) (EN)
- Microsoft Learn : Monolithes modulaires (FR)
