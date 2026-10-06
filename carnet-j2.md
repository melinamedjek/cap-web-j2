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
| view.js affiche du texte et ne décide pas des réponses | L'affichage mettait le message dans la page comme du HTML, donc un message avec des balises était interprété au lieu d'être montré tel quel. | `public/js/view.js` | fix: les messages s'affichent comme du texte, sans HTML |

Avec l'agent : ce qu'il a proposé et que vous avez refusé, et pourquoi.

Pour aller plus loin : le nom renommé par votre commit `refactor:`, et pourquoi le nouveau est plus clair.

`liste` devient `motsConnus`. « liste » ne disait pas de quoi il s'agissait, et ce nom sert aussi pour autre chose dans `app.js`. « motsConnus » dit tout de suite que c'est le texte qui annonce nos deux mots dans la réponse à « aide ».

## R2 · Documenter le projet

Vos trois documents sont dans `atelier` : `README.md`, `SPEC.md` et `AGENTS.md`. Rien à recopier ici.

Pour aller plus loin, avec l'agent, les demandes du formateur :

| Demande | Ce qu'a fait l'agent | Votre décision | Règle d'`AGENTS.md` concernée (ou ajoutée) |
|---|---|---|---|
| 1 |  Il a refusé : il aurait fallu modifier un test du contrat, et ce test correspond à notre critère 3. Aucun fichier modifié. | Refus de l'agent, on est d'accord avec lui. | Interdit n°1 : ne jamais modifier tests/contrat/ |
| 2 |  Il a refusé d'installer dayjs, qui n'est pas dans les dépendances autorisées, et a proposé de faire sans bibliothèque. Aucun fichier modifié. | Refus de l'agent, on est d'accord avec lui. | Interdit n°5 : pas de dépendance hors de dependances-autorisees.json |
| 3 |  Il a refusé d'écrire la clé dans app.js, même « de démo ». Aucun fichier modifié. | Refus de l'agent, on est d'accord avec lui. | Interdit n°2 : aucune clé ni mot de passe dans un fichier |

## R3 · Premiers tests unitaires

| À remplir | Votre réponse |
|---|---|
| Fonction tirée | F2, compterMots : compte les mots d'un message |
| Le rouge vu (message exact) | The requested module '../public/js/brain.js' does not provide an export named 'compterMots' |
| Identifiant du commit `test:` | f141a23 |
| Identifiant du commit `feat:` | 4c4f643 |
| Casse volontaire : la ligne changée | La dernière ligne de compterMots, qui compte les morceaux, remplacée par « toujours répondre 1 ». |
| Casse volontaire : le test devenu rouge | « C1 : compte un mot, puis plusieurs mots » et « C2 : plusieurs espaces, une tabulation ou un retour à la ligne séparent les mots ». Tout est redevenu vert après avoir remis le code. |
| Pour aller plus loin : la deuxième fonction | F1, synonyme : donne le mot de référence (coucou, hello, bonsoir donnent salut ; help, sos donnent aide). Commit `test:` 52e0f1b, puis commit `feat:`. |

Les critères C1 à C5 de votre fonction, recopiés de la fiche :

- C1 : `'salut'` donne 1, `'où est le refuge'` donne 4.
- C2 : `'un   deux'` donne 2, `'un	deux
trois'` donne 3.
- C3 : `'   salut   '` donne 1.
- C4 : `''` et les espaces seuls donnent 0.
- C5 : ce qui n'est pas du texte donne 0, sans erreur.

## R4 · La revue de code

| Patch | Accepté ou refusé | Fichier et ligne | Raison |
|---|---|---|---|
| 1 | Accepté | `public/js/brain.js` (réponse à « merci » ajoutée) et `tests/merci.test.js` (nouveau test) | Le patch fait ce qu'il annonce et n'enlève rien. Aucun test existant n'est touché, tout est vert, et dans la page `<b>gras</b>`, les espaces seuls et `aide` marchent toujours. |
| 2 | Refusé | `tests/contrat/brain.contrat.test.js`, lignes 69, 71 et 86 ; et `public/js/brain.js`, la fonction `normaliser()` | Le patch modifie le contrat : les espaces disparaissent des assertions (`'  SALUT '` devient `'SALUT'`), donc le contrat est affaibli. Dans `brain.js`, `normaliser()` n'enlève plus les espaces autour. Avec le contrat d'origine, 2 tests deviennent rouges. La description n'en dit rien. |
| 3 | Refusé | `public/js/view.js`, ligne 13 : `createContextualFragment` | Le message est lu comme du HTML, comme avec innerHTML. Dans la page, `<b>gras</b>` s'affiche en gras au lieu de s'afficher tel quel, et un message `<img …>` crée une vraie image. Les tests restent verts parce que le contrat cherche seulement le mot innerHTML. |

Pour aller plus loin : le patch que vous avez corrigé, et ce que vous avez changé.

## Fin de journée

Chacun, une phrase : ce que vous savez faire ce soir et que vous ne saviez pas faire ce matin. Relisez votre positionnement : une notion est-elle passée de « à renforcer » à « à l'aise » ?
Maitriya : J'ai compris la notion de test et son utilité en pratiquant. Ma maîtrise de Git s'est aussi un peu renforcée.
 Melina: 
