# Carnet de bord · J2

Binôme : b02 · Membres : Maitriya, Melina · Nos réglages sont dans `atelier/cahier-personnel.json` : ne les recopiez pas ici.

## Mon positionnement (chacun de vous deux)

Pour chaque notion, chacun écrit « à l'aise » ou « à renforcer ». Ce n'est ni évalué ni classé : c'est votre point de départ pour le bilan individuel de fin de module.

| Notion | Membre 1 : Maitriya | Membre 2 : Melina |
|---|---|---|
| Structure HTML | à l'aise | à l'aise |
| CSS et responsive | à l'aise | à l'aise |
| JavaScript | à renforcer | à l'aise |
| DOM et événements | à renforcer | à renforcer |
| Git | à renforcer | à l'aise |
| Tests | à renforcer | à renforcer |

Chacun, en une phrase, son objectif personnel pour J2 et J3.

Membre 1 : Comprendre comment marchent les tests automatisés et savoir expliquer le code à l'oral.

Membre 2 : Écrire mes propres tests et savoir expliquer chaque changement que je garde.

## R1 · Les tests automatisés

Les tests rouges du départ, et ce que vous en avez fait :

| Test rouge | Cause trouvée (une phrase) | Fichier | Message du commit `fix:` |
|---|---|---|---|
| refuse le vide et les espaces seuls | On vérifiait si le message était vide avant d'enlever les espaces, donc un message fait seulement d'espaces passait. | `public/js/brain.js` | fix: un message fait seulement d'espaces est refusé |
| accepte notre limite de caractères et refuse notre limite + 1 | La vérification de la longueur utilisait le nombre 280 écrit en dur au lieu de notre limite. | `public/js/brain.js` | fix: la longueur maximale suit notre limite |
| mesure la longueur après avoir retiré les espaces | La vérification de la longueur utilisait le nombre 280 écrit en dur au lieu de notre limite. | `public/js/brain.js` | fix: la longueur maximale suit notre limite |
| ignore la casse et les espaces autour | Pour choisir la réponse, on mettait le message en minuscules sans enlever les espaces autour, donc « salut » avec des espaces n'était pas reconnu. | `public/js/brain.js` | fix: les majuscules et les espaces autour ne gênent plus la réponse |
| reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour | Pour choisir la réponse, on mettait le message en minuscules sans enlever les espaces autour, donc « salut » avec des espaces n'était pas reconnu. | `public/js/brain.js` | fix: les majuscules et les espaces autour ne gênent plus la réponse |
| répond à une phrase inconnue par un repli distinct | Une phrase inconnue recevait la même réponse que « aide », alors qu'elle doit avoir sa propre réponse. | `public/js/brain.js` | fix: une phrase inconnue reçoit sa propre réponse |
| view.js affiche du texte et ne décide pas des réponses | | | |

Avec l'agent : ce qu'il a proposé et que vous avez refusé, et pourquoi.

Pour aller plus loin : le nom renommé par votre commit `refactor:`, et pourquoi le nouveau est plus clair.

## R2 · Documenter le projet

Vos trois documents sont dans `atelier` : `README.md`, `SPEC.md` et `AGENTS.md`. Rien à recopier ici.

Pour aller plus loin, avec l'agent, les demandes du formateur :

| Demande | Ce qu'a fait l'agent | Votre décision | Règle d'`AGENTS.md` concernée (ou ajoutée) |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

## R3 · Premiers tests unitaires

| À remplir | Votre réponse |
|---|---|
| Fonction tirée | |
| Le rouge vu (message exact) | |
| Identifiant du commit `test:` | |
| Identifiant du commit `feat:` | |
| Casse volontaire : la ligne changée | |
| Casse volontaire : le test devenu rouge | |
| Pour aller plus loin : la deuxième fonction | |

Les critères C1 à C5 de votre fonction, recopiés de la fiche :

## R4 · La revue de code

| Patch | Accepté ou refusé | Fichier et ligne | Raison |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

Pour aller plus loin : le patch que vous avez corrigé, et ce que vous avez changé.

## Fin de journée

Chacun, une phrase : ce que vous savez faire ce soir et que vous ne saviez pas faire ce matin. Relisez votre positionnement : une notion est-elle passée de « à renforcer » à « à l'aise » ?
