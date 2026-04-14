# Claude AI — Add-in Outlook

Intégrez Claude AI directement dans Outlook pour rédiger, résumer, traduire et améliorer vos emails.

---

## 📁 Structure des fichiers

```
outlook-addin/
├── manifest.xml        ← Manifeste du add-in (à modifier)
├── taskpane.html       ← Interface principale du add-in
├── commands.html       ← Fichier requis par Office.js
├── assets/
│   ├── icon-16.png    ← Icône 16x16 px
│   ├── icon-32.png    ← Icône 32x32 px
│   └── icon-80.png    ← Icône 80x80 px
└── README.md
```

---

## 🚀 Installation — 3 étapes

### Étape 1 : Héberger les fichiers

Déployez les fichiers sur un serveur **HTTPS**. Options :

| Option | Prix | Difficulté |
|--------|------|------------|
| **GitHub Pages** | Gratuit | ⭐ Facile |
| **Vercel** | Gratuit | ⭐ Facile |
| **Netlify** | Gratuit | ⭐ Facile |
| Serveur propre | Variable | ⭐⭐ Moyen |

#### Exemple avec GitHub Pages :
1. Créez un repo GitHub (ex: `claude-outlook-addin`)
2. Uploadez tous les fichiers
3. Activez GitHub Pages dans Settings → Pages
4. Votre URL sera : `https://VOTRE-USERNAME.github.io/claude-outlook-addin/`

### Étape 2 : Modifier manifest.xml

Remplacez **toutes les occurrences** de `https://YOUR-DOMAIN` par votre URL réelle.

Exemple :
```xml
<!-- Avant -->
<SourceLocation DefaultValue="https://YOUR-DOMAIN/taskpane.html"/>

<!-- Après -->
<SourceLocation DefaultValue="https://monnom.github.io/claude-outlook-addin/taskpane.html"/>
```

### Étape 3 : Installer le add-in dans Outlook

#### Outlook Web (OWA) :
1. Allez sur **outlook.office.com** ou **outlook.com**
2. Ouvrez un email → cliquez sur les **3 points** (···)
3. **Obtenir des compléments** ou **Get Add-ins**
4. Cliquez **Mes compléments** → **Ajouter un complément personnalisé**
5. Choisissez **Ajouter à partir d'un fichier**
6. Uploadez `manifest.xml`

#### Outlook Desktop (Windows) :
1. Ouvrez Outlook
2. Menu **Fichier** → **Gérer les compléments**
3. Cela ouvre le gestionnaire web → même procédure qu'OWA

#### Via Microsoft 365 Admin (déploiement entreprise) :
1. Connectez-vous à **admin.microsoft.com**
2. Allez dans **Paramètres** → **Applications intégrées**
3. Uploadez `manifest.xml` pour tous les utilisateurs

---

## 🔑 Configuration de la clé API

1. Obtenez une clé sur **https://console.anthropic.com**
2. Dans Outlook, ouvrez le add-in Claude AI
3. Cliquez sur **⚙** (paramètres)
4. Entrez votre clé API (commence par `sk-ant-...`)
5. Cliquez **Enregistrer**

La clé est stockée localement dans le navigateur/Outlook (localStorage).

---

## ✨ Fonctionnalités

| Bouton | Description |
|--------|-------------|
| **✍️ Rédiger réponse** | Génère une réponse professionnelle à l'email |
| **📋 Résumer** | Résume l'email en points clés |
| **🌐 Traduire** | Traduit l'email dans la langue choisie |
| **✨ Améliorer ton** | Améliore le style et la clarté du texte |

**Instructions supplémentaires** : champ libre pour guider Claude (ex: "Sois formel", "En 3 phrases max")

**Bouton Insérer** : insère le résultat directement dans le corps de l'email (mode composition uniquement)

---

## 🔧 Test en local (développeurs)

Pour tester sans hébergement, utilisez **ngrok** ou **live-server** :

```bash
# Installer live-server
npm install -g live-server

# Lancer dans le dossier du projet
live-server --https=...

# OU avec ngrok
npx serve .
ngrok http 3000
```

Modifiez `manifest.xml` avec l'URL ngrok temporaire.

---

## ⚠️ Prérequis

- Microsoft 365 (Outlook Web, Desktop ou Mobile)
- Compte sur console.anthropic.com avec crédits API
- Serveur HTTPS pour héberger les fichiers

---

## 🛡️ Sécurité

- La clé API est stockée **localement** sur votre appareil (localStorage)
- Les appels API sont faits **directement** depuis votre navigateur vers Anthropic
- Aucune donnée n'est envoyée à un serveur tiers

---

## 📞 Support

Pour toute question, consultez :
- [Documentation Office Add-ins](https://learn.microsoft.com/office/dev/add-ins/)
- [API Anthropic](https://docs.anthropic.com)
