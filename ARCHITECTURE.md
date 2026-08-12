# Architecture — 60-30-10

## Principe général

60-30-10 est une application web autonome contenue dans un seul fichier principal : `603010.html`.

Aucun framework, paquet npm, serveur ou processus de compilation n’est nécessaire.

## Arborescence

```text
/
├── 603010.html       Application
├── index.html        Page de présentation
├── fav603010.png     Favicon
├── README.md         Présentation et utilisation
├── CHANGELOG.md      Historique des versions
├── ARCHITECTURE.md   Architecture technique
├── NOTICE.md         Mentions, crédits et licences
└── LICENSE.md        Licences du projet
```

## `603010.html`

Le fichier regroupe :

1. **HTML** — structure de l’interface ;
2. **CSS** — mise en page responsive et composants visuels ;
3. **JavaScript** — calculs colorimétriques, état, traduction, rendu et interactions.

### Organisation du JavaScript

Le script est découpé en blocs bilingues :

- `Utilitaires / Helpers` ;
- `Données / Data` ;
- `Références DOM / DOM references` ;
- `État / State` ;
- `Disposition aléatoire / Random layout` ;
- `Rendu / Rendering` ;
- `Initialisation / Initialization` ;
- `Événements / Events`.

## Couleur

La couleur de travail repose principalement sur **OKLCH** (`L`, `C`, `H`). Le script convertit les couleurs vers sRGB pour produire les formats complémentaires : HEX, RGB, HSL, HSV, CMJN/CMYK et Lab.

Les valeurs sRGB hors gamut sont ramenées dans l’intervalle affichable lors de la conversion.

## Modes

### Classique / Classic

Les trois couleurs sont réglées indépendamment par leurs valeurs OKLCH.

### Caractère / Character

Chaque rôle utilise un profil définissant luminosité et chroma. La teinte reste modifiable et peut être décalée globalement pour les trois couleurs.

## Internationalisation

L’interface FR/EN est pilotée par les objets de traduction JavaScript. La langue active est appliquée au contenu dynamique ainsi qu’à l’attribut `lang` du document.

## Persistance

L’état est enregistré dans le navigateur avec `localStorage`. Il comprend notamment :

- langue ;
- mode ;
- valeurs du mode Classique ;
- profils et teintes du mode Caractère ;
- décalage global de teinte ;
- disposition de la visualisation.

Aucune base de données externe n’est utilisée.

## Déploiement

Le projet est compatible avec un hébergement statique, notamment GitHub Pages. `index.html` constitue la page d’entrée et renvoie vers `603010.html`.
