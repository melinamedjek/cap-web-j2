# Conventions de Cap Web

Ce fichier est lu par l'agent comme par un nouveau développeur.

## Nommage

- Une fonction porte un verbe qui dit ce qu'elle fait, en camelCase : validateMessage, replyTo, renderMessages.
- Une constante partagée s'écrit en MAJUSCULES : LIMITE, MOTS, REPONSES.
- Une variable porte un nom qui dit ce qu'elle contient, pas son type : motsConnus plutôt que liste.
- Un fichier de public/js porte un nom court, en minuscules, qui dit son rôle : brain.js décide, view.js affiche, app.js relie.
- Un message de commit commence par son type, puis dit en français ce qui change :
  fix: (correction), feat: (nouveauté), test: (tests), docs: (documentation), refactor: (renommage ou rangement sans changer le comportement).
  Exemple : « fix: un message fait seulement d'espaces est refusé ».

## Interdits

1. Ne modifie jamais tests/contrat/, browser/contrat.spec.js ni cahier-personnel.json. Si un test te semble faux, arrête-toi et explique pourquoi.
2. N'écris jamais de clé, de mot de passe ou de donnée personnelle dans un fichier, et ne recopie pas la limite ni les deux mots du binôme ailleurs que dans brain.js.
3. N'utilise jamais innerHTML, outerHTML ni insertAdjacentHTML : un message s'affiche comme du texte (textContent).
4. brain.js ne touche jamais à la page : ni document, ni window, ni localStorage.
5. N'ajoute aucune dépendance qui n'est pas dans dependances-autorisees.json, et ne lance pas npm audit fix.
6. Ne fais aucun commit ni push toi-même : propose le changement, le binôme relit le diff et décide.
