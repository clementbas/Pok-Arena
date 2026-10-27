# Pok’Aréna : Spécification technique

**Équipe** : Clémentin LY (front-end), Emi LIM (game design), Clément BAS (back-end et base de données)

**Documents liés** : [Fiche de cadrage](fiche-de-cadrage.md) · [Wireframes Figma](https://www.figma.com/design/ifk933rnzkzElYfMFhCt2N)

Ce document complète la fiche de cadrage : les parties 1 à 3 en reprennent l'essentiel, les parties 4 à 6 détaillent la solution technique.

## Sommaire

1. [Expression du besoin](#1-expression-du-besoin)
2. [Analyse des utilisateurs](#2-analyse-des-utilisateurs)
3. [État de l'art et positionnement](#3-état-de-lart-et-positionnement)
4. [Solutions possibles](#4-solutions-possibles)
5. [Solution retenue](#5-solution-retenue)
6. [Points à définir](#6-points-à-définir)

---

## 1. Expression du besoin

Les jeux Pokémon de la série principale demandent plus de 30 heures de jeu et une console. Beaucoup de fans, notamment ceux qui ont grandi avec les premiers jeux, n'ont plus le temps de s'y investir mais restent attachés à l'univers.

**Besoin** : une expérience Pokémon courte, jouable dans un navigateur, qui reprend l'essentiel du plaisir de la série : combattre, collectionner et progresser, en quelques minutes par session.

**Comment Pok’Aréna y répond**

| Objectif | Réponse |
| --- | --- |
| Jouer par sessions courtes, sans installation | Jeu web en 2D. Une arène se joue en quelques minutes et la progression est sauvegardée côté serveur. |
| Progresser durablement | 4 arènes de difficulté croissante, pièces, boosters, amélioration des Pokémon avec les doublons, classement. |
| Contenter occasionnels et compétiteurs | Difficulté graduée de facile à impossible. |
| Valoriser la collection | Boosters de type et de rareté, cartes officielles du JCC révélées une par une. |
| Un classement équitable | Tous les calculs sont faits par le serveur, aucun achat avec de l'argent réel. |

**Contraintes** : jeu en 2D, uniquement dans le navigateur (ordinateur et mobile), projet non commercial.

---

## 2. Analyse des utilisateurs

La fiche de cadrage décrit quatre profils. Ce qu'ils attendent du produit :

| Profil | Attente principale | Conséquence sur le jeu |
| --- | --- | --- |
| **Lucas**, 27 ans, le nostalgique (cible principale) | Retrouver l'ambiance de la 1ʳᵉ génération, reprendre sa partie en quelques clics | 151 Pokémon de la 1ʳᵉ génération, progression sauvegardée |
| **Inès**, 21 ans, la compétitrice | Un vrai défi et un classement fiable | Arènes difficiles, combats sans hasard, calculs côté serveur |
| **Théo**, 16 ans, le collectionneur | Compléter sa collection, ouvrir des boosters | Ouverture de booster soignée, doublons utiles, interface mobile |
| **Sarah**, 34 ans, la joueuse occasionnelle | Prise en main immédiate, ne jamais être bloquée | Équipe de départ fournie, pièces gagnées à chaque combat, interface simple |

---

## 3. État de l'art et positionnement

La fiche de cadrage détaille les jeux étudiés (Pokémon Rouge et Bleu, JCC Pokémon Pocket, Pokémon GO, Pokémon Champions, Pokémon Showdown, PokéRogue). En résumé :

| Ce que l'on aime | Où on le trouve | Ce qui manque |
| --- | --- | --- |
| Progression par arènes | Jeux principaux | Trop long, console obligatoire |
| Ouverture de boosters | JCC Pokémon Pocket | Pas de combats Pokémon |
| Combat dans le navigateur | Pokémon Showdown, PokéRogue | Pas de progression par arènes avec collection |

**Positionnement** : Pok’Aréna réunit en une seule expérience courte la progression par arènes, la collection par boosters et le jeu dans le navigateur. PokéRogue montre qu'un jeu Pokémon 2D tourne bien dans un navigateur avec Phaser.

---

## 4. Solutions possibles

### Solutions de concept

| Concept | Décision | Raison |
| --- | --- | --- |
| **Arènes et collection par boosters, 1ʳᵉ génération** | **Retenu** | Faisable, répond aux quatre profils |
| Remake d'un jeu complet | Écarté | Trop de contenu à produire |
| Roguelite façon PokéRogue | Écarté | Déjà réalisé |
| Gestion de sa propre arène | Écarté (évolution possible) | Éditeur d'arène trop lourd |
| Toutes les générations | Écarté | Trop de Pokémon à équilibrer |
| Jeu en 3D | Écarté | Trop lourd pour un navigateur |

### Solutions techniques

| Besoin | Options étudiées | Choix | Pourquoi |
| --- | --- | --- | --- |
| Front-end | Vue, React | **Vue 3** | Simple à prendre en main, bien documenté |
| Exploration 2D | Phaser, PixiJS, Canvas | **Phaser** | Gère cartes en tuiles, collisions et clavier. PixiJS et Canvas demandent de tout coder. |
| Back-end | Express, Fastify | **Express** | Simple et très répandu |
| Base de données | PostgreSQL, MongoDB | **PostgreSQL** | Données très liées entre elles (joueurs, collections, arènes) |
| Accès à la base | Sequelize, SQL direct | **Sequelize** | Modèles et migrations clairs |
| Connexion | JWT, sessions | **JWT** | Sans état côté serveur |
| Données Pokémon | PokéAPI, saisie à la main | **PokéAPI**, importée une fois en base | Évite de tout saisir. PokéAPI demande de ne pas la solliciter en permanence. |
| Cartes du JCC | TCGdex | **TCGdex** | Images officielles accessibles par une simple adresse |

---

## 5. Solution retenue

### 5.1 Fonctionnalités prévues

Les 16 fonctionnalités de la version 1, reprises de la fiche de cadrage, reliées aux écrans des wireframes.

| ID | Fonctionnalité | Écran |
| --- | --- | --- |
| F01 | Inscription et connexion | 1 |
| F02 | Sauvegarde de la progression côté serveur | tous |
| F03 | Équipe de départ | 7 |
| F04 | Carte des arènes : le joueur se déplace sur une ligne horizontale (inspiration Mario Bros) pour accéder aux arènes | 2 |
| F05 | Déblocage progressif des arènes | 2 |
| F06 | Exploration de l'arène en 2D | 3 |
| F07 | Énigme d'arène (rochers, interrupteurs) | 3 |
| F08 | Combats de dresseurs | 3, 4 |
| F09 | Combat contre le champion | 4 |
| F10 | Récompenses en pièces | 4 |
| F11 | Boutique de boosters (rareté et type, taux affichés) | 5 |
| F12 | Ouverture de booster avec cartes JCC | 6 |
| F13 | Boutique d'objets (potions, rappels, soins) | 5 |
| F14 | Collection, inventaire et équipe | 7 |
| F15 | Amélioration des Pokémon avec les doublons | 7 |
| F16 | Classement | 8 |

### 5.2 Règles de jeu

Les règles de la fiche de cadrage sont conservées. Pour le développement, nous retenons les principes suivants.

- **Le serveur décide.** Pièces, tirages de boosters, résultats de combat, déblocage des arènes et classement sont calculés par le serveur. Le navigateur affiche et envoie les actions du joueur.
- **Combat au tour par tour, sans hasard** (pas de coup critique ni d'attaque ratée) : à chaque tour, le joueur choisit une action (attaque, changement de Pokémon, objet), le serveur calcule le tour et renvoie le résultat.
- **Calcul des dégâts** : puissance de l'attaque, rapport entre l'Attaque de l'attaquant et la Défense de la cible, avec un bonus pour l'efficacité des types.
- **Statistiques** : l'indice de la rareté (100, 160, 250 ou 380) est réparti selon les stats réelles du Pokémon, comme décrit dans la fiche de cadrage. Chaque amélioration ajoute 5 % (5 améliorations au maximum, 10 doublons chacune).
- **Boosters** : le tirage des 6 Pokémon est fait par le serveur au moment de l'achat. Les taux sont stockés en base et affichés dans la boutique.
- **Défaite** : une défaite contre n'importe quel adversaire fait perdre l'arène, à recommencer depuis le début.
- **Reprise** : la progression dans l'arène en cours est sauvegardée, le joueur peut fermer le navigateur et reprendre plus tard.

### 5.3 Architecture logicielle

Trois parties : une application Vue dans le navigateur, une API Express, une base PostgreSQL.

```mermaid
flowchart LR
    A["Navigateur : Vue 3 et Phaser"] -- "requêtes HTTP, JSON" --> B["Serveur : Node.js et Express"]
    B --> C[("PostgreSQL")]
    D["Script d'import"] --> C
    E["PokéAPI"] -.-> D
    F["TCGdex"] -.-> D
    A -. "images des cartes" .-> F
```

- **Front-end** : Vue 3 pour les écrans (connexion, carte des arènes, combat, boutique, ouverture de booster, collection, classement). Phaser sert uniquement à l'exploration de l'arène (déplacement, collisions, énigme). Le combat et l'ouverture de booster sont en Vue et CSS.
- **Back-end** : API REST en JSON avec Express. Le code est séparé en routes, contrôleurs et services (règles de jeu : combat, boosters, boutique).
- **Base de données** : PostgreSQL, accédée avec Sequelize. Un script importe une seule fois les 151 Pokémon, leurs types et leurs attaques depuis PokéAPI, ainsi que les cartes TCGdex.
- **Connexion** : mot de passe haché (bcrypt), jeton JWT stocké dans un cookie `httpOnly` pour protéger la session.

**Principales routes de l'API**

| Domaine | Routes |
| --- | --- |
| Compte | `POST /api/auth/register`, `POST /api/auth/login`, `GET /api/auth/me` |
| Arènes | `GET /api/arenas`, `POST /api/arenas/:id/start` |
| Combats | `POST /api/battles`, `POST /api/battles/:id/actions` |
| Boutique | `GET /api/shop`, `POST /api/shop/boosters/:id/buy`, `POST /api/shop/items/:id/buy` |
| Collection | `GET /api/collection`, `POST /api/collection/:id/upgrade`, `PUT /api/team` |
| Classement | `GET /api/leaderboard` |

### 5.4 Langages et librairies

| Domaine | Technologie |
| --- | --- |
| Langage | JavaScript, avec Node.js 24 côté serveur |
| Front-end | Vue 3, Vite, Vue Router, Pinia |
| Jeu 2D | Phaser 4, cartes dessinées avec l'éditeur Tiled |
| Back-end | Express |
| Base de données | PostgreSQL, Sequelize |
| Sécurité | jsonwebtoken, bcrypt |
| Qualité | ESLint, Prettier, Vitest |
| Environnement local | Docker Compose (PostgreSQL) |
| Intégration continue | GitHub Actions |

### 5.5 Modélisations du système

**Cas d'utilisation**

```mermaid
flowchart LR
    J(["Joueur"])
    J --> A["Créer un compte, se connecter"]
    J --> B["Choisir une arène"]
    J --> C["Explorer l'arène et combattre"]
    J --> D["Acheter et ouvrir des boosters"]
    J --> E["Acheter des objets"]
    J --> F["Gérer sa collection et son équipe"]
    J --> G["Consulter le classement"]
```

**Modèle de données**

```mermaid
erDiagram
    USERS ||--o{ PLAYER_POKEMON : possède
    POKEMON ||--o{ PLAYER_POKEMON : "est possédé"
    POKEMON ||--o{ MOVES : connaît
    USERS ||--o{ PLAYER_ITEMS : possède
    ITEMS ||--o{ PLAYER_ITEMS : "est possédé"
    BOOSTERS ||--o{ BOOSTER_RATES : contient
    POKEMON ||--o{ BOOSTER_RATES : "taux de tirage"
    ARENAS ||--o{ TRAINERS : compte
    USERS ||--o{ ARENA_RUNS : tente
    ARENAS ||--o{ ARENA_RUNS : "est tentée"
    USERS ||--o{ ARENA_PROGRESS : progresse
    ARENAS ||--o{ ARENA_PROGRESS : "est battue"

    USERS {
        int id PK
        string pseudo
        string email
        string password_hash
        int coins
    }
    POKEMON {
        int id PK
        string name
        string type1
        string type2
        string rarity
        int hp
        int attack
        int defense
        int special
        int speed
        string tcgdex_card_id
    }
    MOVES {
        int id PK
        int pokemon_id FK
        string name
        string type
        int power
    }
    PLAYER_POKEMON {
        int user_id FK
        int pokemon_id FK
        int duplicates
        int upgrade_level
        int team_slot
    }
    BOOSTERS {
        int id PK
        string kind
        string name
        int price
    }
    BOOSTER_RATES {
        int booster_id FK
        int pokemon_id FK
        int rate
    }
    ITEMS {
        int id PK
        string name
        int price
    }
    PLAYER_ITEMS {
        int user_id FK
        int item_id FK
        int quantity
    }
    ARENAS {
        int id PK
        int position
        string name
        string difficulty
    }
    TRAINERS {
        int id PK
        int arena_id FK
        string name
        boolean is_champion
        int reward
    }
    ARENA_RUNS {
        int id PK
        int user_id FK
        int arena_id FK
        string status
        json state
    }
    ARENA_PROGRESS {
        int user_id FK
        int arena_id FK
        date completed_at
    }
```

Quelques précisions :

- Les équipes adverses de chaque dresseur sont décrites dans un fichier de données, importé en base avec les arènes.
- `ARENA_RUNS` contient la tentative en cours (dresseurs battus, combat en cours) pour permettre la reprise.
- `ARENA_PROGRESS` alimente le classement : arène la plus haute battue, puis date de victoire.
- `BOOSTER_RATES.rate` est exprimé sur 10 000 (700 pour 7 %), pour éviter les erreurs d'arrondi.

### 5.6 Maquettes

Les maquettes sont des wireframes simples en noir et blanc, en version ordinateur et mobile, disponibles dans [Figma](https://www.figma.com/design/ifk933rnzkzElYfMFhCt2N).

| Écran | Description |
| --- | --- |
| 1. Connexion | Connexion et inscription |
| 2. Carte des arènes | Chemin horizontal sur lequel le joueur se déplace, 4 arènes (battue, disponible, verrouillées) |
| 3. Exploration | Vue de dessus de l'arène, dresseurs, énigme, porte du champion |
| 4. Combat | Pokémon face à face, barres de vie, actions, journal du tour |
| 5. Boutique | Boosters de type et de rareté avec taux, objets |
| 6. Ouverture de booster | Révélation des 6 cartes une par une |
| 7. Collection | Pokémon possédés, doublons, amélioration, équipe, objets |
| 8. Classement | Liste des joueurs et rang du joueur |

![Connexion](wireframes/01-connexion-desktop.png)
![Carte des arènes](wireframes/02-arenes-desktop.png)
![Exploration](wireframes/03-exploration-desktop.png)
![Combat](wireframes/04-combat-desktop.png)
![Boutique](wireframes/05-boutique-desktop.png)
![Ouverture de booster](wireframes/06-booster-desktop.png)
![Collection](wireframes/07-collection-desktop.png)
![Classement](wireframes/08-classement-desktop.png)

Les versions mobiles sont dans le fichier Figma et exportées dans `docs/wireframes/` (suffixe `-mobile`).

### 5.7 Méthode d'organisation du travail

**Rôles**

| Personne | Rôle | Responsabilités |
| --- | --- | --- |
| Clémentin LY | Front-end | Écrans Vue, navigation, exploration Phaser, interface de combat et de booster |
| Emi LIM | Game design | Règles et équilibrage (stats, taux, prix, récompenses), composition des arènes et des équipes adverses, énigmes |
| Clément BAS | Back-end et base de données | API, base de données, import des données, moteur de combat |

**Méthode** : Kanban léger avec GitHub Projects.

- Colonnes : À faire, En cours, En revue, Terminé.
- Une issue GitHub par tâche, rattachée à une fonctionnalité (F01 à F16).
- Maximum 2 tâches en cours par personne.
- Un point de 15 minutes par semaine pour faire le bilan et répartir la suite.
- Chaque pull request est relue par un autre membre de l'équipe.

**Étapes prévues**

1. Mise en place : dépôt, base de données, import des Pokémon.
2. Compte et sauvegarde (F01 à F03).
3. Boutique, boosters et collection (F11 à F15).
4. Combat (F08 à F10).
5. Arènes et exploration (F04 à F07).
6. Classement, équilibrage, tests (F16).

### 5.8 Organisation du dépôt Git

Un seul dépôt GitHub (monorepo).

```text
pok-arena/
├─ client/        Application Vue et jeu Phaser
├─ server/        API Express, modèles, scripts d'import, données
├─ docs/          Fiche de cadrage, spécification, wireframes
├─ .github/       Intégration continue, modèle de pull request
├─ docker-compose.yml
├─ .env.example
└─ README.md
```

**Branches**

| Branche | Rôle |
| --- | --- |
| `main` | Version stable, mise à jour à chaque étape terminée |
| `develop` | Intégration du travail en cours |
| `feature/xx-nom` | Une branche par fonctionnalité, créée depuis `develop` et fusionnée par pull request |

**Règles**

- Pas de commit direct sur `main` ni `develop`.
- Messages de commit courts, préfixés : `feat:`, `fix:`, `docs:`.
- Une pull request relue par un autre membre avant fusion, avec les tests de l'intégration continue au vert.
- Aucun secret dans le dépôt : `.env` est ignoré, `.env.example` liste les variables.

---

## 6. Points à définir

Ces points sont à trancher par l'équipe, surtout par le game design. Une recommandation est proposée pour ne pas bloquer le développement.

| Question | Recommandation |
| --- | --- |
| L'équipe est-elle soignée entre deux combats ? (question ouverte de la fiche) | Soin à l'entrée de l'arène uniquement, les potions et rappels servent ensuite |
| Composition des boosters de rareté (16 communs, 5 légendaires) | Tirage uniquement dans la rareté du booster |
| Équipe de départ | 3 Pokémon de types variés, suffisants pour l'arène 1 |
| Statuts (poison, paralysie, sommeil...) | Liste minimale à fixer avant le combat |
| Choix des 4 attaques par Pokémon | 2 attaques de son type, 2 d'un autre type |
| Prix, récompenses et taux des boosters | À calculer par le game design dans un tableur |
