# 📖 Guide d'installation détaillé — MathGenius APK

## 🎯 Méthode 1 : GitHub Actions (La plus simple — Zéro installation)

### Étape 1 : Créer un compte GitHub
- Aller sur [github.com](https://github.com) → Sign Up

### Étape 2 : Fork ou importer le dépôt
- Cliquer sur **Fork** en haut à droite du dépôt
- Ou créer un nouveau dépôt et uploader tous les fichiers

### Étape 3 : Activer GitHub Actions
- Aller dans l'onglet **Actions** de votre dépôt
- Cliquer **"I understand my workflows, go ahead and enable them"**

### Étape 4 : Lancer le build
- Dans **Actions** → **Build MathGenius APK**
- Cliquer **"Run workflow"** → **"Run workflow"**
- Attendre 3-7 minutes ⏳

### Étape 5 : Télécharger l'APK
- Cliquer sur le workflow terminé ✅
- Descendre jusqu'à **Artifacts**
- Télécharger **MathGenius-Debug-APK**
- Décompresser le .zip → vous avez `app-debug.apk`

### Étape 6 : Installer sur Android
```
Android 8+ :
  Paramètres → Applications → Paramètres spéciaux
  → Accès spécial → Installer des apps inconnues
  → Votre navigateur/gestionnaire de fichiers → Autoriser

Android 7 et moins :
  Paramètres → Sécurité → Sources inconnues → Activer

Puis : Ouvrir le fichier APK → Installer
```

---

## 🔧 Méthode 2 : Build local (Windows/Mac/Linux)

### Prérequis à installer

1. **Node.js 20 LTS**
   - [nodejs.org/fr/download](https://nodejs.org/fr/download)
   - Vérifier : `node --version` → doit afficher v20.x

2. **Android Studio**
   - [developer.android.com/studio](https://developer.android.com/studio)
   - Installer avec les composants par défaut
   - Accepter les licences SDK

3. **Variables d'environnement** (Windows)
   ```
   ANDROID_HOME = C:\Users\VOTRE_NOM\AppData\Local\Android\Sdk
   PATH += %ANDROID_HOME%\tools
   PATH += %ANDROID_HOME%\platform-tools
   ```

### Build

```bash
# Cloner
git clone https://github.com/VOTRE_USERNAME/mathgenius-app.git
cd mathgenius-app

# Installer Capacitor
npm install

# Synchroniser le projet web → Android
npx cap sync android

# Option A : Ouvrir dans Android Studio
npx cap open android
# Puis : Build → Build Bundle(s) / APK(s) → Build APK(s)

# Option B : En ligne de commande
cd android
chmod +x gradlew    # Mac/Linux seulement
./gradlew assembleDebug    # Mac/Linux
gradlew.bat assembleDebug  # Windows
```

### Trouver l'APK
```
android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 📱 Tester avec un émulateur Android Studio

1. Android Studio → **Device Manager** → **Create Device**
2. Choisir : Pixel 6, API 34
3. Cliquer ▶ pour démarrer l'émulateur
4. Dans le terminal : `npx cap run android`

---

## 🔄 Mettre à jour l'application

Après avoir modifié `index.html` :

```bash
npx cap sync android
npx cap run android
# ou rebuilder l'APK
```

---

## ❓ Problèmes fréquents

### "SDK not found"
```bash
# Créer local.properties dans android/
echo "sdk.dir=/Users/VOTRE_NOM/Library/Android/sdk" > android/local.properties
# Mac: ~/Library/Android/sdk
# Linux: ~/Android/Sdk
# Windows: C:\Users\VOTRE_NOM\AppData\Local\Android\Sdk
```

### "Java version error"
```bash
# Vérifier Java
java -version  # doit être 17+
# Installer Java 17 : https://adoptium.net
```

### L'IA ne fonctionne pas sur l'APK
- L'application a besoin d'une connexion Internet
- L'API Claude est appelée depuis l'app → vérifier la connexion

### Build échoue sur GitHub Actions
- Vérifier que tous les fichiers sont bien committés
- Aller dans Actions → cliquer sur le build rouge → lire les logs
