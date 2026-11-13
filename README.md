# Test fonctionnel manuel — SauceDemo

Projet de test manuel d'une application e-commerce de démonstration, réalisé par **Ali Ghoufrane** (Marrakech, Maroc) dans le cadre de ma formation au test logiciel.

## Résumé

- **34 cas de test exécutés : 31 réussis, 3 échoués**
- **4 bugs** documentés (BUG001 à BUG004) et **2 observations** (OBS01, OBS02)
- Techniques de conception de l'ISTQB : table de décision, partitions d'équivalence, valeurs limites, transition d'états, test exploratoire
- Suivi : plan de test, cas de test, rapports de bugs, matrice de traçabilité et résumé calculé automatiquement, dans un fichier Excel

## Application et environnement

| Élément | Détail |
|---|---|
| Application | SauceDemo — https://www.saucedemo.com (site de démonstration) |
| Périmètre | Connexion, catalogue et tri, panier, formulaire de commande, récapitulatif, déconnexion |
| Comptes testés | `standard_user`, `locked_out_user`, `problem_user`, `performance_glitch_user` |
| Système | Windows ; Brave 1.99.55 (Build officiel) (64 bits) |
| Date d'exécution | Novembre 2026 |

Les exigences ont été **déduites du comportement visible du site** : il n'existe pas de spécification officielle.

## Bugs et observations

| ID | Titre | Cas lié | Sévérité | Priorité | Statut |
|---|---|---|---|---|---|
| BUG001 | Les images des produits ne correspondent pas aux produits (problem_user) | TC031 | Majeure | Haute | Ouvert |
| BUG002 | Ajout et retrait d'articles : seule la première action fonctionne (problem_user) | TC032 | Majeure | Haute | Ouvert |
| BUG003 | Formulaire de commande : le champ Last Name ne garde pas la saisie (problem_user) | TC033 | Majeure | Haute | Ouvert |
| BUG004 | Délai d'environ 8 secondes à la connexion (performance_glitch_user) | TC034 | Mineure | Moyenne | Ouvert |
| OBS01 | Aucune limite de longueur sur le prénom (100 et 300 caractères acceptés) | TC024 | Mineure | Basse | Observation |
| OBS02 | Le code postal accepte des lettres (« ABCDE ») | TC026 | Mineure | Basse | Observation |

> Les bugs ont été trouvés avec des **comptes de démonstration conçus avec des défauts** (`problem_user`, `performance_glitch_user`). L'objectif du projet est de montrer comment je détecte, reproduis et documente un défaut, pas de signaler de vraies failles.

### BUG001 — Les images des produits ne correspondent pas aux produits (`problem_user`)

Avec `standard_user`, chaque produit affiche sa propre image :

![standard_user]BUG001_standard_user_images_correctes.png)

Avec `problem_user`, les 6 produits affichent la même photo (un chien avec une balle) :

![problem_user]BUG001_problem_user_meme_image.png)

### BUG002 — Ajout et retrait d'articles : seule la première action fonctionne (`problem_user`)

Seul le premier clic sur « Add to cart » ou « Remove » est pris en compte. *Limite : la capture du bouton qui ne change pas reste à ajouter.*

### BUG003 — Le champ Last Name ne garde pas la saisie (`problem_user`)

Le prénom est saisi, mais le champ du nom reste vide :

![Last Name vide]BUG003_champ_last_name_vide.png)

### BUG004 — Délai d'environ 8 secondes à la connexion (`performance_glitch_user`)

Durée mesurée manuellement : pas de capture.

### Observations (aucune spécification : à valider avec le métier)

- **OBS01** : aucune limite de longueur sur le prénom (100 et 300 caractères acceptés).
- **OBS02** : le code postal accepte des lettres.

![Code postal ABCDE accepté]TC026_code_postal_lettres_accepte.png)

## Exemples de preuves

| Cas | Capture |
|---|---|
| TC002 — compte verrouillé | ![TC002]TC002_compte_verrouille.png) |
| TC008 — majuscules refusées | ![TC008]TC008_majuscules_refuse.png) |
| TC010 — accès direct sans connexion | ![TC010]TC010_acces_direct_sans_connexion.png) |
| TC021 — code postal requis | ![TC021]TC021_code_postal_requis.png) |
| TC027 — totaux corrects (89,97 $ + 7,20 $ = 97,17 $) | ![TC027]TC027_totaux_recapitulatif.png) |
| TC030 — retour à la connexion après déconnexion | ![TC030]TC030_page_connexion_apres_logout.png) |

## Liste des cas de test

| ID | Titre | Technique | Statut |
|---|---|---|---|
| TC001 | Connexion valide | Table de décision | Réussi |
| TC002 | Compte verrouillé | Table de décision | Réussi |
| TC003 | Username valide, mot de passe incorrect | Table de décision | Réussi |
| TC004 | Username inconnu, mot de passe valide | Table de décision | Réussi |
| TC005 | Champs vides | Partition d'équivalence | Réussi |
| TC006 | Username vide, mot de passe saisi | Partition d'équivalence | Réussi |
| TC007 | Username saisi, mot de passe vide | Partition d'équivalence | Réussi |
| TC008 | Username en majuscules | Partition d'équivalence | Réussi |
| TC009 | Espaces autour du username | Partition d'équivalence | Réussi |
| TC010 | Accès direct à la page produits sans connexion | Contrôle d'accès | Réussi |
| TC011 | Tri « Name (A to Z) » | Partition d'équivalence | Réussi |
| TC012 | Tri « Name (Z to A) » | Partition d'équivalence | Réussi |
| TC013 | Tri « Price (low to high) » | Partition d'équivalence | Réussi |
| TC014 | Tri « Price (high to low) » | Partition d'équivalence | Réussi |
| TC015 | Page de détail d'un produit | Partition d'équivalence | Réussi |
| TC016 | Ajouter un article au panier | Transition d'états | Réussi |
| TC017 | Ajouter trois articles | Transition d'états | Réussi |
| TC018 | Retirer un article du panier | Transition d'états | Réussi |
| TC019 | Formulaire de commande vide | Partition d'équivalence | Réussi |
| TC020 | Prénom seul renseigné | Partition d'équivalence | Réussi |
| TC021 | Prénom et nom sans code postal | Partition d'équivalence | Réussi |
| TC022 | Données valides | Partition d'équivalence | Réussi |
| TC023 | Champs d'un seul caractère | Valeurs limites | Réussi |
| TC024 | Champs de 100 puis de 300 caractères | Valeurs limites | Réussi |
| TC025 | Espaces seulement dans le prénom | Partition d'équivalence | Réussi |
| TC026 | Code postal contenant des lettres | Partition d'équivalence | Réussi |
| TC027 | Calcul du total au récapitulatif | Partition d'équivalence | Réussi |
| TC028 | Finaliser la commande | Transition d'états | Réussi |
| TC029 | Annuler depuis le formulaire de commande | Transition d'états | Réussi |
| TC030 | Déconnexion | Transition d'états | Réussi |
| TC031 | problem_user : affichage des produits | Test exploratoire | Échoué |
| TC032 | problem_user : ajout et retrait d'articles | Test exploratoire | Échoué |
| TC033 | problem_user : formulaire de commande | Test exploratoire | Échoué |
| TC034 | performance_glitch_user : temps de connexion | Test exploratoire | Réussi |

## Contenu du dépôt

```
QA-Portfolio-SauceDemo/
├── Projet_QA_SauceDemo.xlsx   (plan de test, techniques, cas, bugs, traçabilité, résumé, captures)
├── captures/                  (captures principales en haute qualité)
└── README.md
```

## Limites

- Pas de spécification officielle : les exigences sont déduites.
- BUG002 : la capture du clic défaillant reste à ajouter ; BUG004 : durée mesurée à la main.
- Test manuel uniquement : pas d'automatisation, pas de test d'API sur cette application.

## Compétences démontrées

Conception de cas de test avec les techniques ISTQB · exécution et suivi des résultats · rédaction de rapports de bugs · distinction entre bug et observation · traçabilité exigences / cas de test · preuves par captures d'écran.

## Contact

ghou911@gmail.com
