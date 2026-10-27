# Jeu d'arènes Pokémon — Dossier de cadrage

Oct 8, 2026 · Clémentin LY, Emi LIM, Clément BAS

## 1. Définition des besoins

### Contexte

Pokémon est l'une des franchises de jeu vidéo les plus populaires au monde. Sa communauté s'étend sur plusieurs générations, des joueurs qui ont découvert la série à la fin des années 1990 jusqu'aux joueurs d'aujourd'hui.

Les jeux de la série principale demandent plus de 30 heures de jeu, reposent sur une longue phase d'exploration et nécessitent une console. Une grande partie des fans, notamment ceux qui ont grandi avec les premiers jeux, n'a plus le temps de s'y investir, tout en restant attachée à l'univers.

### Problématique

Il n'existe pas d'expérience Pokémon courte, accessible depuis un simple navigateur, qui permette de retrouver l'essentiel du plaisir de la série (combattre, collectionner, progresser) en quelques minutes par session.

### Objectifs

- Permettre aux fans de profiter de l'univers Pokémon en sessions courtes, sans console ni installation.
- Leur offrir un sentiment de progression durable, qui donne envie de revenir.
- Satisfaire à la fois les joueurs occasionnels et ceux qui recherchent un véritable défi.
- Valoriser la collection, l'un des moteurs historiques de la franchise.
- Permettre aux joueurs de se mesurer entre eux de façon équitable.

### Besoins fonctionnels

Le joueur doit pouvoir :

- créer un compte et retrouver sa progression sur n'importe quel appareil ;
- commencer à jouer immédiatement, sans préparation ;
- relever des défis de difficulté croissante ;
- être récompensé de ses efforts, même en cas d'échec ;
- collectionner des Pokémon et composer son équipe ;
- comparer sa progression à celle des autres joueurs.

### Besoins non fonctionnels

- **Sécurité** : progression et classement protégés contre la triche.
- **Performance** : jeu rapide à charger et fluide.
- **Accessibilité** : jouable sur ordinateur et sur mobile.
- **Maintenabilité** : contenu du jeu facile à faire évoluer.

### Contraintes

- Jeu en 2D, jouable dans un navigateur web.
- Projet non commercial et non publié : l'univers Pokémon et ses visuels appartiennent à Nintendo / The Pokémon Company.

## 2. Étude des utilisateurs (personae)

La cible principale est le joueur nostalgique de 20 à 35 ans qui veut des sessions courtes ; trois profils secondaires orientent la difficulté, le classement et l'ergonomie.

|  | Lucas, le nostalgique | Inès, la compétitrice | Théo, le collectionneur | Sarah, la joueuse occasionnelle |
| --- | --- | --- | --- | --- |
| Âge, situation | 27 ans, développeur en CDI | 21 ans, étudiante en informatique | 16 ans, lycéen | 34 ans, infirmière, deux enfants |
| Rapport à Pokémon | A grandi avec Rouge et Bleu, ne joue plus aux jeux récents | Joue en compétitif, connaît les stats et les faiblesses par cœur | Collectionne les cartes du JCC, adore ouvrir des boosters | Connaît les Pokémon emblématiques, sans plus |
| Contexte de jeu | Pauses déjeuner, soirées, sur ordinateur | Longues sessions, sur ordinateur | Téléphone, dans les transports | Téléphone, 10 minutes le soir |
| Objectifs | Retrouver l'ambiance de la 1ʳᵉ génération sans 30 h d'aventure | Venir à bout des adversaires les plus difficiles et être 1ʳᵉ du classement | Compléter sa collection des 151 | Se détendre, sentir qu'elle progresse |
| Frustrations | Les jeux trop longs, les mécaniques modernes qu'il ne connaît plus | Les jeux trop faciles, la chance qui décide de tout, la triche | Les doublons, les Pokémon rares introuvables | Être bloquée, les interfaces chargées |
| Attentes | Une partie qui reprend où il l'a laissée, en quelques clics | Un vrai défi stratégique, un classement fiable | Un suivi clair de sa collection, des boosters variés | Une prise en main immédiate, une progression qui ne la bloque jamais |

**Ce que les personae attendent du produit :**

- Des sessions courtes, que l'on peut interrompre et reprendre (Lucas, Sarah).
- Une difficulté progressive, avec un dernier défi réellement exigeant (Sarah, Inès).
- Une progression qui ne bloque jamais : chaque effort doit rapporter quelque chose (Sarah, Théo).
- Une collection valorisée, y compris les doublons (Théo).
- Un classement qu'on ne peut pas truquer (Inès).
- Une interface utilisable sur téléphone (Théo, Sarah).

## 3. État de l'art

Aucun jeu connu ne combine progression par arènes et collection par boosters dans l'univers Pokémon : chaque brique existe séparément, sans qu'aucune offre ne les réunisse.

| Jeu | Éditeur | Ce que nous en retenons | Ce qui lui manque pour notre cible |
| --- | --- | --- | --- |
| Pokémon Rouge / Bleu et jeux principaux | Nintendo / Game Freak | La structure en 8 arènes de difficulté croissante, l'identité de la 1ʳᵉ génération | Aventure longue, exploration obligatoire, console uniquement |
| JCC Pokémon Pocket | The Pokémon Company | L'ouverture de boosters comme moment fort, les raretés, la collection | Pas de progression par arènes, combats de cartes plutôt que combats Pokémon |
| Pokémon GO | Niantic | Des arènes défendues et une économie de pièces | Arènes sans difficulté graduée, jeu basé sur la géolocalisation |
| [Pokémon Champions](https://games.gg/fr/pokemon-champions/) | The Pokémon Works | Un jeu centré uniquement sur le combat | Orienté compétitif classé, sans collection ni progression solo |
| Pokémon Showdown | Fan (open source) | Simulateur de combat dans le navigateur, référence pour les règles | Aucun contenu solo ni progression, outil pour joueurs experts |
| PokéRogue | Fan (open source, Phaser) | Preuve qu'un jeu Pokémon complet tourne dans le navigateur en 2D | Roguelite : on recommence à zéro, pas de collection durable |

**Idée récurrente chez les fans.** Des joueurs réclament depuis longtemps un spin-off de gestion où l'on incarnerait un champion d'arène ([Pokébip](https://www.pokebip.com/espace-membre/blogs/253889/article/241694), [PokéCommunity](https://www.pokecommunity.com/threads/your-own-gym.180417/)), signe d'un intérêt réel pour un jeu centré sur les arènes.

**Hors Pokémon,** les jeux de collection à tirage aléatoire (gacha) montrent les règles à respecter : afficher les taux de chaque rareté, limiter la frustration des doublons, garder une progression possible sans payer.

**Enseignements pour notre projet :**

1. La progression par arènes est un format connu de tous les fans, inutile de l'expliquer.
2. L'ouverture de booster doit être soignée (animation, révélation de la rareté) : c'est le moment le plus attendu.
3. Les taux de rareté doivent être affichés dans la boutique.
4. La technique est éprouvée : un jeu de combat Pokémon 2D tourne très bien dans un navigateur.

## 4. Solution retenue et alternatives

Nous retenons un jeu web de progression par arènes avec collection par boosters, développé en Vue.js et Express, limité aux 151 Pokémon de la 1ʳᵉ génération.

### Le concept

Le joueur reçoit une équipe de départ à sa première connexion. Il traverse 4 arènes : facile, normale, difficile et impossible. Dans chaque arène, il se déplace en 2D, résout une énigme (rochers à pousser, interrupteurs à activer…) et bat 2 à 3 dresseurs avant d'atteindre le champion. Chaque victoire rapporte des pièces, qui achètent des boosters contenant des Pokémon aléatoires. Ces nouveaux Pokémon renforcent son équipe et lui permettent d'affronter l'arène suivante.

### Boucle de jeu

La boucle tient en quatre étapes répétées jusqu'à l'arène impossible.

&#91;embedded content: boucle de jeu · 4 étapes\]

Une défaite ne bloque jamais le joueur : il peut rejouer une arène déjà battue pour gagner des pièces et ouvrir de nouveaux boosters.

### Règles déjà décidées

- **Déblocage strict** : les arènes se font dans l'ordre ; une arène reste verrouillée tant que la précédente n'est pas battue.
- **Déroulement d'une arène** : exploration en 2D, une énigme à résoudre, 2 à 3 combats de dresseurs, puis le combat contre le champion. L'arène n'est validée qu'après la victoire sur le champion. Une défaite contre n'importe quel adversaire fait perdre l'arène : le joueur recommence tous les combats depuis le début.
- **Récompenses par combat** : chaque combat gagné rapporte des pièces, peu pour un dresseur et beaucoup pour un champion. La première victoire contre un adversaire rapporte plus que les suivantes. Le joueur peut donc accumuler des pièces sans battre le champion.
- **Deux usages des pièces** : les boosters, et une boutique d'objets (potions, rappels, soins de statut). Le jeu ne comporte aucun achat réel : seules les pièces gagnées en jeu permettent d'acheter.
- **Boosters de rareté**, tous types confondus, de plus en plus chers. La rareté dépend du stade dans la lignée, la forme finale étant toujours épique :
  - Lignée à 3 stades : base commune, 1ʳᵉ évolution rare, 2ᵉ évolution épique (Salamèche, Reptincel, Dracaufeu)
  - Lignée à 2 stades : base rare, évolution épique (Pikachu, Raichu ; Évoli, puis Aquali, Voltali, Pyroli)
  - Pokémon sans évolution : épique (Ronflex, Lokhlass, Ptéra, Tauros…)
  - Légendaire : Artikodin, Électhor, Sulfura, Mewtwo, Mew
  - Répartition : 16 communs, 54 rares, 76 épiques, 5 légendaires
- **Boosters de type**, couvrant les 15 types ; les types peu fournis sont regroupés. Un Pokémon à double type apparaît dans les deux boosters concernés. Chaque Pokémon a son propre taux, plus faible pour les formes évoluées (par exemple Salamèche 7 %, Dracaufeu 1 %) ; les légendaires du type y sont présents à environ 0,3 %. Les taux d'un booster totalisent 100 % et sont affichés dans la boutique.
  - Feu (12 Pokémon), Eau + Glace (34), Plante (14), Électrik (9), Psy + Spectre (17), Sol + Roche (19), Normal + Combat (32), Poison (33), Insecte (12), Vol + Dragon (21)
- **6 Pokémon par booster**, révélés un par un sous forme de cartes à l'ouverture.
- **Équipes de 6 Pokémon** : pour le joueur et les champions d'arène. Les dresseurs ont de 1 à 6 Pokémon, sauf dans l'arène impossible où dresseurs et champion en ont tous 6.
- **Amélioration par doublons** : tous les 10 doublons d'un Pokémon, le joueur peut l'améliorer pour augmenter ses stats ; 5 améliorations au maximum, soit 50 doublons.
- **1ʳᵉ génération uniquement** : 151 Pokémon, 15 types.

### Statistiques et améliorations

La rareté fixe le niveau de puissance d'un Pokémon, et l'écart entre deux paliers est tel qu'un Pokémon amélioré 5 fois reste sous le palier suivant non amélioré.

| Rareté | Indice de stats de base | Après 5 améliorations (+5 % chacune) | Palier suivant, sans amélioration |
| --- | --- | --- | --- |
| Commun | 100 | 125 | 160 (rare) |
| Rare | 160 | 200 | 250 (épique) |
| Épique | 250 | 312 | 380 (légendaire) |
| Légendaire | 380 | 475 | — |

L'indice correspond au total des stats du Pokémon (PV, Attaque, Défense, Spécial, Vitesse). Ce total est fixé par la rareté, puis réparti selon le profil réel du Pokémon : Ronflex garde beaucoup de PV, Alakazam un Spécial élevé. Les valeurs exactes seront ajustées pendant l'équilibrage, en gardant cette règle d'écart.

### Alternatives envisagées

| Alternative | Pourquoi elle a été écartée |
| --- | --- |
| Remake d'un jeu Pokémon complet (exploration, scénario) | Volume de contenu (cartes, PNJ, dialogues) trop important pour le délai ; copie directe de l'œuvre originale |
| Roguelite inspiré de PokéRogue | Concept déjà réalisé et très abouti |
| Gestion d'arène (le joueur construit son arène, les autres l'affrontent) | Idée originale, mais l'éditeur d'arène et l'équilibrage entre joueurs alourdissent fortement le projet ; gardée comme évolution possible |
| Toutes générations confondues | Plus de 1 000 Pokémon à intégrer et équilibrer ; perte de l'identité « 1ʳᵉ génération » |
|  | trop lourd pour un jeu navigateur |

## 5. Fonctionnalités principales

La première version livre la boucle complète (compte, arènes, pièces, boosters, classement) ; les règles encore ouvertes sont regroupées dans les évolutions.

### Version 1 (MVP)

| Fonctionnalité | Description | Personae |
| --- | --- | --- |
| Inscription et connexion | Création de compte (pseudo, e-mail, mot de passe haché), connexion, déconnexion, session persistante | Tous |
| Sauvegarde de la progression | Pièces, collection, doublons, inventaire, équipe et arènes battues stockées côté serveur, accessibles depuis n'importe quel appareil | Lucas, Sarah |
| Équipe de départ | À la première connexion, le joueur reçoit un ou plusieurs Pokémon définis, suffisants pour battre l'arène 1 | Sarah, Lucas |
| Sélection des arènes | Chaque arène affichée vue de l'extérieur, une à la fois ; flèches gauche et droite pour passer de l'une à l'autre ; statut visible : verrouillée, disponible, battue | Tous |
| Déblocage progressif | Une arène n'est accessible qu'après la victoire sur la précédente ; règle vérifiée par le serveur | Inès, Sarah |
| Exploration de l'arène | Intérieur de l'arène en vue de dessus : déplacement du personnage case par case au clavier ou au toucher, collisions ; une défaite contre n'importe quel adversaire fait perdre l'arène, à recommencer depuis le début | Lucas |
| Énigme d'arène | Une énigme par arène bloque l'accès au champion : rochers à pousser, interrupteurs à activer, ou autre mécanique propre à l'arène | Lucas, Inès |
| Combats de dresseurs | 2 à 3 dresseurs placés sur le chemin du champion, chacun avec 1 à 6 Pokémon (6 dans l'arène impossible), qui déclenchent un combat quand le joueur passe devant eux | Inès, Lucas |
| Combat contre le champion | Combat final de l'arène contre une équipe de 6 Pokémon, au tour par tour : choix de l'attaque, efficacité des types, changement de Pokémon, utilisation d'objets. Résultat calculé par le serveur | Inès |
| Récompenses | Pièces gagnées à chaque combat gagné : peu pour un dresseur, beaucoup pour un champion ; montant plus élevé la première fois que l'adversaire est battu | Sarah, Théo |
| Boutique de boosters | Boosters de rareté (commun, rare, épique, légendaire, prix croissant) et boosters de type avec un taux par Pokémon ; tous les taux affichés | Théo |
| Ouverture de booster | Tirage de 6 Pokémon effectué par le serveur ; révélation animée de la carte officielle du JCC de chaque Pokémon obtenu | Théo |
| Boutique d'objets | Achat de potions, rappels et soins de statut avec les pièces ; objets stockés dans l'inventaire | Inès, Sarah |
| Collection, inventaire et équipe | Liste des Pokémon possédés avec leur nombre de doublons (filtres par type et rareté), objets possédés, composition de l'équipe de 6 Pokémon | Théo, Inès |
| Amélioration par doublons | Tous les 10 doublons, une amélioration de +5 % des stats du Pokémon ; 5 améliorations au maximum (50 doublons), vérifiées par le serveur | Théo |
| Classement | Joueurs classés par arène la plus haute battue, départagés par la date d'obtention | Inès |

### Exigences non fonctionnelles

- **Sécurité** : mots de passe hachés, sessions authentifiées, et calcul côté serveur des pièces, des tirages de boosters et des résultats de combat, pour empêcher la triche.
- **Performance** : chargement de l'application en moins de 3 s, déplacements et combats fluides dans le navigateur.
- **Accessibilité** : jouable sur ordinateur et mobile (responsive), textes lisibles.
- **Maintenabilité** : données des Pokémon stockées en base, arènes paramétrables sans modifier le code.

### Évolutions envisagées

| Fonctionnalité | Description |
| --- | --- |
| Pokédex | Suivi de la complétion des 151 Pokémon, vus et obtenus |
| Doublons au-delà de 50 | Conversion en pièces des doublons d'un Pokémon déjà amélioré 5 fois |
| Gestion des défaites | Récompense de consolation ou coût d'une défaite (la reprise est déjà fixée : l'arène recommence depuis le début) |
| Arène impossible | Équipe et règles spécifiques du dernier champion |
| Classements secondaires | Taille de la collection, meilleur temps ou moins de tours par arène, classement hebdomadaire |
| Profil joueur | Statistiques, badges obtenus, équipe favorite |

À trancher aussi : l'équipe est-elle soignée entre deux combats d'une même arène, ou le joueur doit-il gérer ses PV avec ses potions jusqu'au champion ?
