# Cap Web

## À quoi sert Cap Web

Cap Web est un petit assistant de discussion qui tourne sur votre poste, pour apprendre le web.
Il ne réfléchit pas : il suit des règles. Il répond à « salut », « aide », « test » et aux mots choisis par le binôme, et donne un conseil au hasard quand on écrit « conseil ».
Il refuse les messages vides ou trop longs, affiche un compteur de caractères, et affiche les messages comme du texte, jamais comme du HTML.

## Installer et lancer

Il faut Node 24.20 ou plus. Vérifiez votre version :

```powershell
node --version
```

Récupérez le projet, puis entrez dans le dossier `atelier` :

```powershell
git clone https://github.com/melinamedjek/cap-web-j2.git
cd cap-web-j2telier
```

Installez les outils :

```powershell
npm ci
```

Les réglages du binôme sont déjà dans `cahier-personnel.json` : n'y touchez pas. Seulement si ce fichier manque, créez-le à partir de l'exemple, puis mettez-y votre limite et vos mots dans l'éditeur :

```powershell
Copy-Item cahier-personnel.exemple.json cahier-personnel.json
```

Lancez Cap Web, puis ouvrez http://127.0.0.1:3000 dans le navigateur. Ctrl+C l'arrête.

```powershell
npm start
```

## Tester

Dans un second terminal, toujours dans `atelier`, lancez les tests puis le vérificateur de code. Les deux doivent finir sans erreur (`fail 0` pour les tests) :

```powershell
npm test
npm run lint
```

Si PowerShell refuse `npm`, tapez `npm.cmd` à la place.

## La route `/api/conseil`

Le serveur répond à http://127.0.0.1:3000/api/conseil avec un conseil tiré au hasard, en JSON, par exemple `{"conseil":"Relis ton diff avant chaque commit."}`. Quand on écrit « conseil » dans la page, Cap Web appelle cette route ; si le serveur ne répond pas, il affiche « Le serveur ne répond pas : conseil indisponible. ». La route est testée dans `tests/conseil.test.js`.

## Les 3 modules de `public/js`

- `brain.js` décide. Il vérifie le message (pas vide, pas trop long) et choisit la réponse. Il ne touche jamais à la page. C'est aussi là que sont la limite et les deux mots du binôme.
- `view.js` affiche. Il montre la conversation dans la page, en texte seulement. Il ne choisit aucune réponse.
- `app.js` relie les deux. Il lit le formulaire, demande à `brain.js` de vérifier et de répondre, garde l'historique, puis demande à `view.js` de l'afficher.

On ne modifie jamais `tests/contrat/`, `browser/contrat.spec.js` ni `cahier-personnel.json`.

## Arborescence

```
atelier/
├── public/              la page : ce que voit l'utilisateur
│   ├── index.html       la structure de la page
│   ├── styles.css       l'apparence (couleurs, version mobile)
│   └── js/
│       ├── brain.js     décide : vérifie le message et choisit la réponse
│       ├── view.js      affiche la conversation, en texte seulement
│       └── app.js       relie la page, brain.js, view.js et le serveur
├── server/              le serveur local
│   ├── app.js           les adresses : la page, /version.json, /api/conseil
│   └── start.js         lance le serveur sur le port 3000
├── tests/               les tests (npm test)
│   └── contrat/         le contrat : on n'y touche jamais
└── scripts/             les outils de contrôle (dépendances, tests)
```
