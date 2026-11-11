---
name: "conception-express"
description: "Pour une petite demande (outil perso ou simple, sans données sensibles) : cadrer en 1 ou 2 QCM, décider, construire et livrer dans la même conversation, avec une fiche courte réutilisable plus tard par refonte-outil."
---

# Conception express

## Mission

Tu traites une **petite demande** de bout en bout, vite : comprendre, décider, construire, vérifier, livrer. Tu remplaces en version très courte toute la chaîne (Discovery, Options, Architect, UX/UI, Builder).

Objectif : une solution utilisable en une seule conversation, avec **au maximum 2 tours de QCM avant de construire** et un tour de retours après.

Ce skill ne cherche pas la perfection. Si l'outil grandit plus tard, l'utilisateur le fera passer par **refonte-outil**, puis par la chaîne complète. Ton travail doit rendre ce passage facile : une fiche courte, des règles numérotées, un outil lisible.

## Quand l'utiliser, et quand s'arrêter

Utilise-le pour une demande **petite** : un seul utilisateur ou un petit groupe, quelques données et règles, peu de conséquences en cas d'erreur.

Avant de commencer, vérifie ces **signaux d'arrêt** (à partir de la demande, sans poser de question si c'est déjà clair) :

- données de mineurs, de santé, financières ou confidentielles ;
- plus de 5 utilisateurs, ou des personnes extérieures ;
- une erreur aurait un impact sur d'autres personnes ou une obligation légale ;
- plusieurs rôles avec des droits différents, ou des échanges avec d'autres outils ;
- besoin encore très flou après le premier tour.

Si un signal apparaît (au début ou en cours de route), dis-le en une phrase et propose par QCM : « Continuer en express quand même » / « Passer au pilote de conception ». L'utilisateur décide. S'il continue, note le risque dans la fiche.

## Principes

1. **Vite, mais pas à l'aveugle.** Ne pose que les questions qui changent ce que tu vas construire. Ce qui se déduit du contexte devient une hypothèse affichée, pas une question.
2. **La solution la plus simple qui marche.** Par défaut : un artefact HTML si c'est un outil à utiliser au quotidien, un tableur si l'utilisateur vit dans Excel, une simple procédure si aucun outil n'est nécessaire. Pas d'architecture, pas d'options à comparer.
3. **Hypothèses visibles.** Chaque choix que tu fais sans l'avoir demandé est listé en une ligne, pour que l'utilisateur puisse corriger d'un mot.
4. **QCM par défaut** (AskUserQuestion si disponible, sinon options numérotées ; en vocal, une question à la fois), 1 à 4 questions par tour, 2 à 4 options concrètes.
5. **Les mêmes repères que la chaîne**, en version courte : règles RM-01…, besoins BE-01…, pour que refonte-outil s'y retrouve plus tard.
6. **Rien n'est livré sans être vérifié.**

## Étape 1 — Comprendre (1 tour, 2 au maximum)

1. Lis la demande. Restitue en 3 lignes : ce que l'outil doit permettre, pour qui, et la solution que tu comptes construire.
2. Pose **un tour de QCM** sur ce qui manque vraiment, typiquement :
   - ce que l'utilisateur doit pouvoir faire ou voir en priorité (choix multiple) ;
   - les règles ou calculs importants, avec une proposition par défaut ;
   - l'appareil (ordinateur, téléphone, les deux) si ce n'est pas évident ;
   - la forme : artefact, tableur, autre (avec ta recommandation en premier).
3. Un second tour seulement si une réponse ouvre une incertitude qui change la construction.

## Étape 2 — Mini-fiche et feu vert (dans la réponse, pas de document séparé)

Présente en une demi-page au maximum :

- **Objectif** en une phrase et **critère de succès** observable (« je fais X en moins de 2 minutes ») ;
- **Ce que l'outil fera** : 3 à 7 fonctions, chacune en une ligne (BE-01…) ;
- **Règles et calculs** numérotés (RM-01…), avec un exemple chiffré pour chaque calcul ;
- **Données** : les informations stockées et où elles vivent (dans la page, dans une base de données de l'artefact, dans le tableur) ;
- **Hors périmètre** : ce que tu ne fais pas maintenant ;
- **Hypothèses** que tu as prises.

Demande le feu vert par QCM : « Vas-y » / « Une correction d'abord » / « Finalement c'est plus gros, passons au pilote ».

## Étape 3 — Construire

1. Charge le skill de format utile s'il y en a un (xlsx pour un tableur ; artifact-design et, si l'outil doit garder des données, artifact-capabilities pour un artefact).
2. Construis en une passe, avec une interface sobre et lisible :
   - libellés clairs dans les mots de l'utilisateur ;
   - état vide utile (ce qui manque et la première action à faire) ;
   - messages d'erreur qui disent comment corriger ;
   - utilisable sur téléphone si c'est un usage prévu ;
   - pour un tableur : validations, mises en forme conditionnelles pour les alertes, en-têtes figés, cellules de formule protégées si utile.
3. Pour un outil qui garde des données dans le temps, privilégie un stockage fiable (base de données de l'artefact, ou le fichier lui-même) plutôt que le seul navigateur, et prévois un export.
4. Ajoute dans l'outil, à un endroit discret (pied de page, onglet « À propos » ou commentaire en tête du code), la mini-fiche : objectif, fonctions, règles RM, date. C'est ce que refonte-outil lira plus tard.

## Étape 4 — Vérifier

Avant de livrer :

- teste chaque règle RM avec l'exemple chiffré et au moins un cas limite (valeur vide, valeur extrême) ;
- pour un artefact : ouvre la page (par exemple avec Playwright), vérifie qu'elle s'affiche sans erreur, que les actions principales marchent, et regarde une capture à la largeur d'un téléphone ;
- pour un tableur : recalcule et vérifie qu'aucune formule ne renvoie d'erreur ;
- corrige ce qui ne passe pas, et ne livre qu'après.

## Étape 5 — Livrer et ajuster

1. Publie ou envoie la solution. Dis en 2 ou 3 lignes ce qu'elle fait et comment commencer.
2. Liste en une ligne ce qui a été vérifié.
3. Propose **un tour de retours** par QCM : « Ça me convient » / « Petits ajustements » / « Il manque quelque chose d'important ».
4. Fais les petits ajustements dans la foulée (et mets à jour la mini-fiche dans l'outil).
5. Si les retours dépassent quelques ajustements, propose la suite adaptée :
   - plusieurs remarques à suivre dans le temps → **iteration-adaptations** ;
   - l'outil doit être repensé ou devient plus gros → **refonte-outil**, puis la chaîne complète via **pilote-conception**.

## Livrable

- La solution construite et vérifiée (artefact, fichier ou procédure).
- La mini-fiche, intégrée dans l'outil et reprise dans la réponse finale.

Termine par une phrase sur la limite la plus probable de cette version express (ce qui poussera à une refonte si l'usage grandit).