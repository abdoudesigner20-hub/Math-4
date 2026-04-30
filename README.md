# 🧮 MathGenius — Application Android

<div align="center">

![MathGenius](https://img.shields.io/badge/MathGenius-v3.0-2563eb?style=for-the-badge&logo=android)
![Android](https://img.shields.io/badge/Android-23%2B-3ddc84?style=for-the-badge&logo=android)
![AI Powered](https://img.shields.io/badge/AI-Claude%20Powered-7c3aed?style=for-the-badge)
![Languages](https://img.shields.io/badge/Langues-6-059669?style=for-the-badge)

**Application de calcul mathématique avec Intelligence Artificielle intégrée**

[📥 Télécharger l'APK](#-téléchargement-de-lapk) • [🚀 Build rapide](#-build-rapide) • [📖 Guide complet](#-guide-complet)

</div>

---

## ✨ Fonctionnalités

| Fonctionnalité | Description |
|---|---|
| 🤖 **Assistant IA** | Basé sur Claude — répond à **toutes** vos questions |
| 🔢 **Calculatrice** | Expressions complexes avec étapes détaillées |
| 📐 **Géométrie** | 9 formes : cercle, rectangle, triangle, sphère, cylindre, cube, cône, trapèze, distance |
| 🔺 **Triangle complet** | Angles, côtés (en cm), hauteurs, médianes, bisectrices, rayons |
| 📚 **Formules** | Bibliothèque interactive de formules mathématiques |
| 📜 **Historique** | Conservation de tous vos calculs |
| 🌍 **6 langues** | 🇫🇷 Français · 🇸🇦 Arabe · 🇬🇧 Anglais · 🇪🇸 Espagnol · 🇩🇪 Allemand · 🇮🇹 Italien |

---

## 📥 Téléchargement de l'APK

### Méthode 1 — GitHub Actions (Automatique) ⭐

1. Aller dans l'onglet **[Actions](../../actions)**
2. Cliquer sur le dernier workflow ✅
3. Télécharger **`MathGenius-Debug-APK`**

### Méthode 2 — GitHub Releases

1. Aller dans **[Releases](../../releases)**
2. Télécharger `app-debug.apk`

### Installation sur Android

```
1. Copier l'APK sur votre téléphone
2. Paramètres → Sécurité → Sources inconnues ✅
   (ou sur Android 8+ : Paramètres → Applications → Autoriser depuis cette source)
3. Ouvrir le fichier APK et installer
4. Chercher "MathGenius" dans votre liste d'applications
```

---

## 🚀 Build Rapide

### Option A : GitHub Actions (Recommandé — 0 installation)

```
1. Fork ce dépôt
2. Aller dans Actions → "Build MathGenius APK"
3. Cliquer "Run workflow"
4. Attendre ~5 minutes
5. Télécharger l'APK dans les Artifacts
```

### Option B : Build Local

#### Prérequis
- **Node.js** 18+ → [nodejs.org](https://nodejs.org)
- **Android Studio** → [developer.android.com/studio](https://developer.android.com/studio)
- **Java 17** (inclus dans Android Studio)

#### Étapes

```bash
# 1. Cloner le dépôt
git clone https://github.com/VOTRE_USERNAME/mathgenius-app.git
cd mathgenius-app

# 2. Installer les dépendances
npm install

# 3. Synchroniser avec Android
npx cap sync android

# 4. Ouvrir dans Android Studio
npx cap open android
# → Build → Build APK(s) → Debug APK
```

L'APK sera dans :
```
android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 📖 Guide Complet

### Structure du projet

```
mathgenius-app/
├── index.html              ← Application complète (HTML/CSS/JS)
├── capacitor.config.json   ← Configuration Capacitor
├── package.json            ← Dépendances Node.js
├── .github/
│   └── workflows/
│       └── build-apk.yml  ← CI/CD GitHub Actions
├── android/                ← Projet Android natif
│   ├── app/
│   │   ├── src/main/
│   │   │   ├── java/com/mathgenius/app/
│   │   │   │   └── MainActivity.java
│   │   │   ├── res/
│   │   │   │   ├── values/
│   │   │   │   │   ├── strings.xml
│   │   │   │   │   ├── styles.xml
│   │   │   │   │   └── colors.xml
│   │   │   │   └── xml/
│   │   │   │       ├── file_paths.xml
│   │   │   │       └── network_security_config.xml
│   │   │   └── AndroidManifest.xml
│   │   └── build.gradle
│   ├── build.gradle
│   ├── settings.gradle
│   ├── variables.gradle
│   └── gradle.properties
└── docs/
    └── SETUP.md
```

### Comment ça fonctionne ?

```
index.html (votre app web)
      ↓ Capacitor wrapping
Android WebView (natif)
      ↓ Compilé en
.apk (installable sur Android)
```

**Capacitor** encapsule votre application web dans une WebView Android native, donnant accès aux APIs du téléphone.

---

## 🔧 Configuration

### Changer l'ID de l'application

Dans `capacitor.config.json` :
```json
{
  "appId": "com.votre_nom.mathgenius",
  "appName": "MonMathGenius"
}
```

Et dans `android/app/build.gradle` :
```gradle
applicationId "com.votre_nom.mathgenius"
```

### Générer un APK Signé (Release)

Pour publier sur le Play Store, un APK signé est requis :

```bash
# Générer un keystore
keytool -genkey -v -keystore mathgenius.keystore \
  -alias mathgenius -keyalg RSA -keysize 2048 -validity 10000

# Build release signé
cd android
./gradlew assembleRelease \
  -Pandroid.injected.signing.store.file=../mathgenius.keystore \
  -Pandroid.injected.signing.store.password=VOTRE_PASSWORD \
  -Pandroid.injected.signing.key.alias=mathgenius \
  -Pandroid.injected.signing.key.password=VOTRE_KEY_PASSWORD
```

---

## 🤝 Contribution

1. Fork le projet
2. Créer une branche : `git checkout -b feature/amelioration`
3. Commit : `git commit -m 'Ajout de fonctionnalité'`
4. Push : `git push origin feature/amelioration`
5. Ouvrir une Pull Request

---

## 📄 Licence

MIT License — Libre d'utilisation, modification et distribution.

---

<div align="center">
Made with ❤️ • Powered by Claude AI • Capacitor + Android
</div>
