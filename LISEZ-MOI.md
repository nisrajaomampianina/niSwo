# Suivi Diet — installer sur Android

Ce dossier contient l'app complète (`www/index.html`, autonome, plein écran) et tout le nécessaire pour produire l'APK.

## Option A — APK automatique avec GitHub (sans rien installer)
1. Crée un dépôt sur github.com (privé si tu veux) et envoie **le contenu de ce dossier** à sa racine (glisser-déposer dans « Add file › Upload files », y compris le dossier `.github`).
2. Onglet **Actions** : le workflow « Build APK » se lance tout seul (≈ 5 min).
3. Ouvre l'exécution terminée › section **Artifacts** › télécharge **SuiviDiet-apk** (zip contenant `app-debug.apk`).
4. Sur le téléphone : ouvre l'APK, autorise « Installer des applis inconnues » pour ton navigateur ou gestionnaire de fichiers, installe.

## Option B — sur ton ordinateur (Android Studio)
```
npm install
npx cap add android
npx cap sync android
npx cap open android   # puis Build › Build APK(s)
```

## Option C — application web installable (le plus rapide)
Héberge le dossier `www/` (Netlify Drop, GitHub Pages…), ouvre l'URL dans Chrome Android › menu ⋮ › **Installer l'application**. Pour un APK à partir de cette URL : pwabuilder.com › Android › Download.

## Notes
- Les données restent sur le téléphone (stockage local). Pense à l'export JSON dans Paramètres › Sécurité, sauvegardes & données.
- Les photos de fond (Pinterest) sont chargées depuis internet : hors ligne, les fonds seront vides.
- La synchronisation Google Health / Samsung Health / Apple Santé demande d'ajouter le plugin santé (voir DEPLOIEMENT.md du projet).
- L'APK « debug » s'installe directement ; pour le Play Store il faudra une version signée (`./gradlew bundleRelease`).
