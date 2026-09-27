# GLB Viewer APK

Viewer 3D mobile pour fichiers **.glb / .gltf**.
Tourne au doigt, pinch zoom, animations, Draco.
PWA prête à transformer en **APK Android**.

Repo : https://github.com/Chasmet/glb-viewer-apk

## 1. Activer GitHub Pages (obligatoire une fois)

1. Ouvre le repo → **Settings** → **Pages**
2. Source : **GitHub Actions**
3. Relance le workflow : onglet **Actions** → *Deploy GitHub Pages* → *Run workflow*

URL une fois déployé :
**https://chasmet.github.io/glb-viewer-apk/**

Sur téléphone Chrome : menu → **Ajouter à l'écran d'accueil** = app sans store.

## 2. Générer un vrai APK (PWABuilder)

1. Va sur https://www.pwabuilder.com
2. Colle l'URL Pages ci-dessus
3. **Package** → **Android** → Generate
4. Télécharge le zip : tu as un `.apk` de test + un `.aab` Play Store

Package ID conseillé : `com.chasmet.glbviewer`

Sans ordi : tu peux aussi installer la PWA depuis Chrome. L'APK n'est pas générable depuis ce repo tout seul (pas de SDK Android ici).

## 3. Ajouter TES fichiers GLB

1. Upload tes `.glb` dans le dossier `models/` (GitHub → Add file)
2. Dans `index.html`, édite le tableau :

```js
const MODELS = [
  { name: "Helmet (démo)", url: "https://threejs.org/examples/models/gltf/DamagedHelmet/glTF-Binary/DamagedHelmet.glb" },
  { name: "Mon kart", url: "./models/kart.glb" }
];
```

Ou appuie sur **Ouvrir .glb** dans l'app (fichier local du téléphone, pas besoin de GitHub).

## Limites (important)

- GitHub file : 100 Mo max par fichier (vise < 15 Mo)
- Un jeu ultra-réaliste en APK unique = trop lourd. Ce repo = **viewer**, pas Godot/engine natif
- Les démos Helmet/Duck viennent de threejs.org (besoin réseau la 1re fois)
- GLB locaux dans `models/` marchent hors-ligne après cache PWA

## Stack

- Three.js r169 + GLTFLoader + Draco + OrbitControls
- PWA (manifest + service worker)
- GitHub Pages (Actions)
