# DESIGN — Jeu de puzzle bioluminescent (inspiré d'Avatar)

Projet privé, entre potes. Document de référence : toute session de dev repart d'ici.

## 1. Concept

Jeu de **puzzle d'environnement calme**, en écrans fixes, sur mobile (portrait).
Un jeune du peuple de la forêt accomplit son **rite de passage** : monter du sol de la
forêt jusqu'au sommet du monde, **lier un ikran**, puis s'envoler vers l'arbre sacré.
La progression est **verticale** : chaque zone est plus haute que la précédente, et
chaque zone ajoute une mécanique qui s'empile sur les précédentes.

- Pas de chrono, pas de réflexes : on réfléchit sans pression.
- Le danger ne réagit **qu'aux erreurs** du joueur, jamais au temps qui passe.
- Échec = le niveau recommence (instantanément, sans punition).
- Histoire **sans texte** pour l'instant (uniquement visuelle).

## 2. Personnages

- **Le héros** (à l'écran) : jeune du peuple de la forêt, grand, agile, marques
  bioluminescentes sur la peau qui s'allument près des plantes éclairées.
  Il **avance seul** dès qu'un chemin sûr existe, **par étapes** (il s'arrête à chaque
  plante allumée / point d'intérêt). Il ne marche que sur les zones éclairées.
- **La graine de l'arbre sacré** (le curseur du joueur) : petite méduse de lumière
  blanche qui flotte et suit le doigt. C'est elle qui « touche » les éléments.

## 3. Règles générales

- Chaque niveau = un écran fixe ; la **sortie est toujours plus haut**.
- Le joueur agit uniquement au **tap** (une main suffit). La graine se déplace vers le
  point touché et active l'élément.
- **Prédateurs de l'ombre** : vivent dans le noir, on ne voit que leurs yeux.
  Ils ne sortent jamais d'une zone éclairée. Si la lumière s'éteint autour du héros,
  ils l'attrapent → restart. Allumer une plante peut les repousser et libérer un passage.
- Niveau réussi → le décor s'illumine entièrement, puis on monte au niveau suivant.

## 4. Zones et niveaux

### Zone 1 — Le sol de la forêt (mécanique : la lumière)
Ambiance très sombre, humide, racines ; c'est le joueur qui révèle le décor.

Éléments :
- **Plante-lanterne** : touchée → s'allume et allume ses voisines directes.
- **Fleur-porte** : fermée dans le noir, s'ouvre si une lumière est adjacente.
- **Champignon-pont** : grandit à la lumière et forme une plateforme.
- **Plante timide** : s'éteint si elle reçoit trop de lumière (2 voisines allumées).

Niveaux :
1. **Premier éveil** — 3 lanternes alignées : toucher = lumière = chemin.
2. **La fleur endormie** — fleur-porte bloquante ; lanterne cachée derrière une fougère.
3. **Le ruisseau** — 2 champignons dans l'eau doivent être allumés ensemble pour faire pont.
4. **L'ordre des lumières** — introduit la plante timide : l'ordre d'allumage compte.
5. **La lumière ne dure pas** — les lanternes s'éteignent après **X pas du héros**
   (pas de temps réel). Fin : un grand arbre s'illumine et révèle des lianes vers la zone 2.

### Zone 2 — Les troncs et les lianes (mécanique : la croissance)
On grimpe ; l'écran est vertical, la sortie en haut.

Éléments :
- **Liane** : pousse vers la lumière la plus proche ; le héros peut y grimper.
- **Spirale timide** : se replie quand on la touche (ouvre/bloque un passage),
  se rouvre si on la retouche.
- **Mousse lumineuse** : garde la lumière plus longtemps mais ne la propage pas.

Niveaux :
1. **La première liane** — allumer une lanterne en hauteur, la liane pousse, on grimpe.
2. **Deux chemins** — gauche/droite ; un côté mène à un cul-de-sac plein de prédateurs.
3. **La spirale** — la replier libère de la lumière mais révèle aussi une zone sombre.
4. **Changer d'avis** — guider la liane en plusieurs étapes (droite puis gauche).
5. **Le grand tronc** — niveau sur toute la hauteur, combine tout. Fin : on débouche sur
   la canopée sous les étoiles, on aperçoit les îles flottantes au loin.

### Zone 3 — La canopée (mécanique : les animaux)
Branches immenses entre les arbres, un peu de lumière d'étoiles. On n'agit plus
seulement sur des plantes : on **attire** ou on **effraie** des animaux.

Éléments :
- **Petits grimpeurs** (lémuriens lumineux) : attirés par les **fleurs à nectar** allumées,
  vont s'y asseoir ; leur poids fait plier les branches. Ils ont peur du noir et refusent
  de le traverser.
- **Lézards-hélices** : touchés, ils s'envolent en tournoyant et se posent sur l'endroit
  sombre le plus proche, qu'ils éclairent (= lumière mobile).
- **Branches souples** : plient sous un poids → rampe, pont ou passage.

Niveaux :
1. **Le petit grimpeur** — attirer un grimpeur au bout d'une branche pour faire une rampe.
2. **Les hélices** — passage sombre gardé, sans plante : un lézard-hélice chasse les prédateurs.
3. **La balance** — une branche ne plie qu'avec 2 grimpeurs ; ordre des fleurs à gérer.
4. **Ils ont peur aussi** — éclairer le chemin d'un grimpeur pour qu'il ose venir.
5. **Sous les cascades** — grand niveau combiné ; cascades venues des îles, racines qui
   pendent du ciel. Fin : le héros saisit une racine et grimpe vers le ciel.

### Zone 4 — Les îles flottantes (mécanique : le vent)
Rochers flottants, cascades dans le vide, brume entre les îles.

Dangers propres à la zone :
- **Le vide** : si un pont s'écarte sous le héros, il tombe → restart.
- **La brume** : étouffe la lumière ; les prédateurs s'y cachent.
- **Ikrans sauvages endormis** : une lumière trop proche les réveille, ils chassent le
  héros → restart.

Éléments :
- **Plante-soufflet** : allumée, souffle un courant d'air dans une direction.
- **Rocher dérivant** : poussé par le vent, sert de pont.
- **Racines suspendues** : on y grimpe (comme les lianes).

Niveaux :
1. **Les racines du ciel** — un soufflet pousse un rocher pour faire un pont.
2. **Le souffle** — plusieurs soufflets, ordre d'allumage (puzzle de glissement).
3. **La brume** — le vent disperse la brume : révèle le chemin… et les prédateurs.
4. **Les nids** — tracer un chemin de lumière assez loin de chaque nid (puzzle tactique).
5. **Le lien** — un ikran éveillé attend ; c'est lui qui choisit. Ses marques s'allument
   selon un **motif** que le joueur reproduit sur les plantes autour (mémoire/observation).
   3 motifs réussis = le héros s'approche 3 fois → lien créé, lumières synchronisées.

### Final — L'envol (pas de puzzle)
Vol libre sur l'ikran, guidé doucement au doigt ; tout ce qu'on survole s'illumine.
Arrivée au **sommet** : un immense arbre sacré où convergent toutes les lumières
rallumées. Le rite est accompli.

### Récapitulatif
| Zone | Lieu | Mécanique | Danger | Fin de zone |
|---|---|---|---|---|
| 1 | Sol de la forêt | Lumière | Prédateurs de l'ombre | Grand arbre illuminé |
| 2 | Troncs et lianes | Croissance | Idem | Vue sur les îles |
| 3 | Canopée | Animaux | Idem | Racines vers le ciel |
| 4 | Îles flottantes | Vent | Vide, brume, ikrans | Le lien avec l'ikran |
| Final | Le ciel | Vol libre | Aucun | Le sommet |

20 niveaux de puzzle + 1 final.

### Idées en réserve (pas prioritaires)
- **Graines-souvenirs** cachées (bonus facultatifs) révélant ce qui a éteint la forêt.
- **Herbier** qui se remplit avec les plantes et créatures découvertes.
- Un ancien du clan qui dit quelques phrases au début de chaque zone.

## 5. Direction artistique

- **Pixel art** fait dans le code : sprites définis comme grilles de caractères
  (1 caractère = 1 couleur de palette), dessinés sur canvas. Pas d'images générées.
- Sprites petits : **16×16** ou **32×32**. Décors en **tuiles** répétables
  (sol, racines, branches, rochers).
- Grands éléments (ikran, arbre sacré) : composés de plusieurs morceaux.
  Ciel étoilé, brume, cascades, particules : **générés procéduralement**.
- La bioluminescence vient des **effets de lumière** par-dessus les sprites
  (halos, lueurs pulsées, blending additif) sur un fond très sombre.
- **Palette limitée** (16–24 couleurs) : bleus nuit / violets pour le fond ;
  cyan, magenta, vert néon pour les lumières.
- Contraste visuel : nature organique et douce ; prédateurs = yeux luisants dans le noir.

## 6. Technique

- **PWA** hébergée sur **GitHub Pages** (attention : Pages sur dépôt privé = compte payant).
- **Vanilla HTML + JavaScript + Canvas 2D**, sans framework ni build.
- **Mobile d'abord, portrait** ; jouable aussi sur ordinateur (jeu centré, bandes sur les côtés).
- Résolution interne ~**180×320**, agrandie en pixels entiers (rendu net, `image-rendering: pixelated`).
- Entrées : tap / clic uniquement.
- Fonctionne **hors ligne** (service worker) et s'installe sur l'écran d'accueil (manifest).
- Niveaux décrits en **données** (fichiers JS/JSON) pour en ajouter facilement.
- Sauvegarde de la progression en `localStorage`.

## 7. À décider plus tard

- **Son** : musique d'ambiance + bruitages de lumière (plus tard).
- Écrans autour du jeu : écran titre, carte des zones / sélection de niveau.
- Nom du jeu et du héros.

## 8. Plan de développement

1. Prototype du niveau **1-1** : moteur de base (canvas, scaling, tap, graine, héros,
   plante-lanterne, lumière, prédateurs).
2. Zone 1 complète (5 niveaux) + PWA installable + déploiement GitHub Pages.
3. Zone 2, puis zone 3, puis zone 4, puis le final.
4. Écrans titre / carte, sauvegarde, puis son.
