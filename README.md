# Issho Ni Flashcards

![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-4285F4?style=for-the-badge&logo=jetpackcompose&logoColor=white)
![Licence propriétaire](https://img.shields.io/badge/Licence-Propri%C3%A9taire-red?style=for-the-badge)

Application Android d'apprentissage et de révision du vocabulaire japonais, conçue pour les élèves de la formation **Issho Ni**. Elle propose un système de flashcards bilingues (français ↔ japonais) avec suivi de progression, listes personnalisées et synchronisation entre appareils.

Une partie du contenu est librement accessible. L'accès aux modules de formation et à la synchronisation de progression nécessite d'être élève Issho Ni.

[<img src="https://play.google.com/intl/en_us/badges/static/images/badges/fr_badge_web_generic.png" height="70">](https://play.google.com/store/apps/details?id=com.isshoni.flashcards)

---

| Accueil | Session de cartes | Mes listes |
|---|---|---|
| <img src="screenshots/screen_welcome.png" width="220"> | <img src="screenshots/screen_flashcard.png" width="220"> | <img src="screenshots/screen_home.png" width="220"> |

---

## ✨ Fonctionnalités

### Accessible sans compte
- **Listes par défaut** : vocabulaire (animaux, couleurs, visage, corps, sports, boissons, fruits, légumes, transports) + kana (hiragana, katakana, tous les kana) — plus de 500 cartes incluses
- **Listes personnalisées** : créer, renommer, supprimer, réordonner ses propres listes par glisser-déposer
- **Cartes personnalisées** : ajouter français, kana, kanji, une phrase exemple et une image
- **Sessions de révision** : choix du sens (FR→JP ou JP→FR), animation de retournement de carte
- **Piles verte/orange** : trier les cartes maîtrisées et les cartes à revoir pendant la session
- **Synthèse vocale** : écouter la prononciation japonaise (TTS natif Android)
- **Favoris** : marquer n'importe quelle liste comme favorite pour y accéder rapidement
- **Import / export** : sauvegarder et restaurer ses listes au format JSON
- **Aide & légal** : tutoriel, politique de confidentialité, licences

### Réservé aux élèves (connexion requise)
- **Modules de formation** : accès aux listes N5, N4, etc. selon les droits du compte
- **Synchronisation de progression** : retrouver sa progression sur tous ses appareils

---

## 🎴 Retournement de carte

![Retournement de carte](screenshots/gif_flashcard_flip.gif)

---

## 🌸 Animation sakura

![Animation sakura](screenshots/gif_sakura.gif)

---

## 🛠️ Stack technique

| Composant | Technologie |
|---|---|
| Langage | Kotlin 2.3.20 |
| UI | Jetpack Compose + Material3 |
| Navigation | Navigation Compose 2.9.7 |
| Base de données locale | Room 2.8.4 |
| Réseau | Retrofit 3.0.0 + OkHttp + Gson |
| Stockage sécurisé | AndroidX Security Crypto 1.1.0-alpha06 (EncryptedSharedPreferences) |
| Préférences | DataStore Preferences 1.1.4 |
| Chargement d'images | Coil 3.2.0 (coil-compose + coil-network-okhttp) |
| Synthèse vocale | Android TTS natif |
| Drag & drop | Reorderable 2.4.3 |
| Tests | JUnit 4, MockK, kotlinx-coroutines-test |
| Build | Gradle (KTS), KSP |
| Min SDK | 24 (Android 7.0) |
| Target SDK | 36 |

> Tests unitaires : logique de progression, gestion des états offline/online, fusion des données.

**Permission requise :** `INTERNET` (synchronisation de progression et téléchargement des modules)

---

## 📁 Structure du projet

```
app/src/main/java/com/isshoni/flashcards/
│
├── data/
│   ├── local/                          # Entités Room, DAOs, Database
│   ├── remote/                         # API Retrofit, DTOs
│   └── repository/                     # Source unique de vérité, gestion offline/online
│       
├── ui/
│   ├── components/
│   ├── navigation/
│   ├── screens/
│   ├── theme/
│   ├── tts/
│   └── viewmodels/
│
└── assets/
    └── fonts/licences/
```

---

## 💡 Défis techniques notables
- Synchronisation de progression offline/online avec gestion des conflits
- Persistance de progression entre sessions imbriquées, nécessitant une analyse fine du cycle de vie du ViewModel et de la fusion des états dans le Repository
- Composition IME japonaise et recherche réactive
- Recherche multilingue et collation MySQL
- Chiffrement des tokens d'authentification avec EncryptedSharedPreferences
- Animation Canvas personnalisée (pétales de sakura)
- Drag & drop sur listes avec persistance de l'ordre


## 🔒 Politique de confidentialité

L'application collecte des données personnelles uniquement dans le cadre de la connexion au compte Issho Ni (identifiants, progression pédagogique). Ces données ne sont jamais revendues à des tiers.

[Consulter la politique complète](https://www.isshoni.fr/politique-de-confidentialite/)

---

## 📄 Licence

Ce logiciel est distribué sous licence propriétaire. Tous droits réservés — © Stéphane FRERET.

Toute reproduction, modification ou redistribution est interdite sans autorisation écrite explicite.

Les polices utilisées (Dekko, Modak, Noto Sans JP) sont distribuées sous [licence OFL](https://openfontlicense.org).
