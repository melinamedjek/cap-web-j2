# Cap Web

## À quoi sert Cap Web

Cap Web est un petit assistant de discussion qui tourne sur votre poste, pour apprendre le web.
Il ne réfléchit pas : il suit des règles. Il répond à « salut », « aide », « test » et à deux mots choisis par le binôme.
Il refuse les messages vides ou trop longs, et affiche les messages comme du texte, jamais comme du HTML.

## Installer et lancer

Il faut Node 24.20 ou plus. Vérifiez votre version :

```powershell
node --version
```

Ouvrez un terminal dans le dossier `atelier`, puis installez les outils :

```powershell
npm ci
```

Créez vos réglages à partir de l'exemple, puis ouvrez `cahier-personnel.json` dans l'éditeur pour y mettre votre limite et vos deux mots :

```powershell
Copy-Item cahier-personnel.exemple.json cahier-personnel.json
```

Lancez Cap Web, puis ouvrez http://127.0.0.1:3000 dans le navigateur. Ctrl+C l'arrête.

```powershell
npm start
```

Lancez les tests :

```powershell
npm test
```

Si PowerShell refuse `npm`, tapez `npm.cmd` à la place.

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
