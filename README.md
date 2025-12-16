# 🎓 EduPlatform - Plateforme Éducative Intelligente

> **"L'apprentissage réinventé par l'Intelligence Artificielle"**

[![Status](https://img.shields.io/badge/Status-Production-success?style=flat-square)](https://github.com/imenbenothmen/eduplatform)
[![MERN Stack](https://img.shields.io/badge/Stack-MERN-blue?style=flat-square&logo=mongodb)](https://www.mongodb.com/mern-stack)
[![AI Powered](https://img.shields.io/badge/AI-Gemini%202.0-purple?style=flat-square&logo=google)](https://ai.google.dev/)
[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat-square&logo=node.js)](https://nodejs.org/)

---

## 📖 Table des Matières

1. [À propos du projet](#-à-propos-du-projet)
2. [Démonstration](#-démonstration)
3. [Fonctionnalités IA](#-fonctionnalités-ia)
4. [Fonctionnalités principales](#-fonctionnalités-principales)
5. [Architecture technique](#-architecture-technique)
6. [Installation](#-installation)
7. [Configuration](#-configuration)
8. [Guide d'utilisation](#-guide-dutilisation)
9. [Structure du projet](#-structure-du-projet)
10. [API Endpoints](#-api-endpoints)
11. [Captures d'écran](#-captures-décran)
12. [Technologies utilisées](#-technologies-utilisées)
13. [Sécurité](#-sécurité)
14. [Auteur](#-auteur)

---

## 🌟 À propos du projet

**EduPlatform** est une plateforme d'apprentissage moderne (LMS - Learning Management System) qui intègre l'**Intelligence Artificielle** pour offrir une expérience éducative personnalisée et interactive.

### Vision

Transformer l'éducation en ligne en combinant :
- 🎯 **Personnalisation** : Recommandations adaptées à chaque apprenant
- 🤖 **Automatisation** : Génération de quiz et analyses intelligentes
- 💬 **Interactivité** : Assistant virtuel disponible 24/7
- 📊 **Insights** : Analyses prédictives pour les administrateurs

### Contexte

Développé dans le cadre du **TP10 - React & IA** de ma formation en **4ème année Data Science**, ce projet démontre la maîtrise complète de la stack MERN enrichie par des capacités d'Intelligence Artificielle via Google Gemini.

---

## 🤖 Fonctionnalités IA

> Propulsé par **Google Gemini 2.0 Flash** pour des réponses rapides et précises

### 1. 📊 Dashboard Administrateur Intelligent

**Analyse globale automatisée de la plateforme**

```javascript
// Insights générés par l'IA
- Statistiques en temps réel (cours, étudiants, avis)
- Tendances d'inscription et engagement
- Cours les plus populaires
- Recommandations stratégiques personnalisées
- Prédictions de croissance
```

**Fonctionnalités :**
- 📈 Analyse des métriques clés
- 🎯 Identification des tendances
- 💡 Suggestions d'amélioration
- 📋 Rapports automatiques


---

### 2. 🎯 Système de Recommandations

**Suggestions de cours personnalisées basées sur l'IA**

**Critères d'analyse :**
- Historique de navigation de l'utilisateur
- Cours suivis et complétés
- Préférences de domaine
- Niveau de compétence
- Avis et notes donnés

**Algorithme de recommandation :**

```javascript
// L'IA analyse :
1. Profil de l'apprenant
2. Patterns de comportement
3. Similarité avec d'autres utilisateurs
4. Contenu des cours disponibles

// Génère :
- Top 5 cours recommandés
- Score de pertinence
- Raison de la recommandation
```

**Exemple de résultat :**

```json
{
  "recommendations": [
    {
      "courseId": "abc123",
      "title": "React Hooks Avancés",
      "relevanceScore": 0.95,
      "reason": "Basé sur votre intérêt pour React et JavaScript"
    }
  ]
}
```


---

### 3. 💬 Chatbot Assistant Virtuel

**Assistant conversationnel intelligent pour répondre aux questions**

**Capacités :**
- ❓ Réponses aux questions sur les cours
- 📚 Information sur le contenu pédagogique
- 🎓 Conseils d'apprentissage
- 🔍 Recherche dans la base de connaissances
- 💡 Suggestions de ressources

**Contexte fourni au chatbot :**

```javascript
// Le chatbot a accès à :
- Catalogue complet des cours
- Descriptions détaillées
- Instructeurs et contenus
- Avis des étudiants
- FAQ de la plateforme
```

**Interface utilisateur :**
- Chat en temps réel avec bulles de messages
- Historique de conversation
- Suggestions de questions
- Réponses formatées avec Markdown

**Exemple d'interaction :**

```
👤 Utilisateur : "Quels cours recommandes-tu pour débuter en React ?"

🤖 Assistant : "Pour débuter en React, je vous recommande :

1. **Introduction à React** - Par John Doe
   Idéal pour comprendre les fondamentaux : JSX, composants, props

2. **React Hooks Essentiels** - Par Jane Smith
   Maîtrisez useState, useEffect et les hooks personnalisés

3. **Projet React Complet** - Par Bob Johnson
   Construisez une application de A à Z

Voulez-vous plus de détails sur l'un de ces cours ?"
```


---

### 4. 📝 Générateur de Quiz Intelligent

**Création automatique de quiz adaptatifs à partir du contenu des cours**

**Configuration du quiz :**

```javascript
// Paramètres personnalisables
{
  courseId: "xyz789",
  difficulty: "intermediate",  // easy, intermediate, hard
  numberOfQuestions: 10,
  topics: ["React Hooks", "State Management"],
  questionTypes: ["QCM", "Vrai/Faux", "Code"]
}
```

**Processus de génération :**

1. **Analyse du cours** : L'IA scanne le contenu, la description, et les objectifs
2. **Extraction des concepts** : Identification des notions clés
3. **Génération des questions** : Création de QCM pertinents
4. **Validation** : Vérification de la cohérence et difficulté

**Exemple de quiz généré :**

```json
{
  "quiz": {
    "title": "Quiz - React Hooks Avancés",
    "duration": "15 minutes",
    "questions": [
      {
        "id": 1,
        "question": "Quel hook permet de gérer un état complexe avec un reducer ?",
        "options": [
          "useState",
          "useReducer",
          "useEffect",
          "useContext"
        ],
        "correctAnswer": "useReducer",
        "explanation": "useReducer est idéal pour gérer un état avec logique complexe."
      }
    ]
  }
}
```

**Fonctionnalités du quiz :**
- ⏱️ Timer intégré
- ✅ Correction automatique
- 📊 Score et statistiques
- 💡 Explications détaillées
- 🔄 Régénération possible

**Interface :**
- Design moderne et épuré
- Navigation intuitive
- Feedback visuel immédiat
- Résumé des performances



---

### 5. ✍️ Générateur de Bio Professionnelle

**Création automatique de biographies pour les profils utilisateurs**

**Informations requises :**

```javascript
{
  interests: "Full Stack Development, Data Science, React",
  experience: "4 ans en développement web, projets MERN",
  goals: "Devenir Tech Lead et contribuer à l'open source",
  education: "4ème année Data Science"
}
```

**Styles de bio disponibles :**
- 🎯 **Professionnelle** : Pour LinkedIn et CV
- 🌟 **Créative** : Pour portfolio et réseaux sociaux
- 📚 **Académique** : Pour profils éducatifs

**Exemple de bio générée :**

```
Développeuse Full Stack passionnée avec 4 ans d'expérience 
dans la création d'applications web modernes utilisant la 
stack MERN. Actuellement en 4ème année de Data Science, 
j'allie expertise technique et analyse de données pour 
créer des solutions innovantes. Mon objectif : évoluer vers 
un poste de Tech Lead tout en contribuant activement à des 
projets open source. Spécialisée en React, Node.js et 
Intelligence Artificielle.
```


---

## 🎯 Fonctionnalités principales

### 👤 Gestion des Utilisateurs

**Système d'authentification complet**

```javascript
// Inscription
POST /api/auth/register
{
  "username": "imen_dev",
  "email": "imen@eduplatform.com",
  "password": "SecurePass123"
}

// Connexion
POST /api/auth/login
{
  "email": "imen@eduplatform.com",
  "password": "SecurePass123"
}
```

**Fonctionnalités :**
- 🔐 Inscription / Connexion sécurisée (JWT + bcrypt)
- 👤 Profils utilisateurs éditables
- 📊 Historique d'apprentissage
- ⭐ Gestion des avis et notes
- 🎓 Suivi de progression

**Rôles utilisateurs :**

| Rôle | Permissions |
|------|-------------|
| **Étudiant** | Consulter cours, s'inscrire, donner avis, utiliser IA |
| **Administrateur** | Toutes permissions + Dashboard IA + Gestion complète |

**Devenir administrateur :**
Pour obtenir le rôle admin, inscrivez-vous avec un email contenant **"admin"**.

```javascript
// Exemples valides :
"admin@eduplatform.com"
"superadmin123@example.com"
"imen.admin@gmail.com"

// Le système détecte automatiquement et attribue le rôle
```

---

### 📚 Système de Gestion de Cours (LMS)

**Catalogue complet avec fonctionnalités avancées**

#### Consultation des cours

```javascript
GET /api/courses
// Retourne tous les cours avec filtres et recherche
```

**Filtres disponibles :**
- 🔍 Recherche par titre/description
- 👨‍🏫 Filtrage par instructeur
- ⭐ Tri par note moyenne
- 📅 Tri par date de création
- 👥 Tri par popularité (nombre d'étudiants)

#### Détails d'un cours

```javascript
GET /api/courses/:id
// Informations complètes + avis + étudiants inscrits
```

**Contenu d'un cours :**
- 📖 Titre et description détaillée
- 👨‍🏫 Informateur de l'instructeur
- ⏱️ Durée estimée
- 🎯 Objectifs pédagogiques
- 📊 Statistiques (étudiants, avis)
- 💬 Tous les avis avec notes

#### Inscription à un cours

```javascript
POST /api/courses/:id/enroll
Authorization: Bearer <token>

// L'utilisateur est ajouté à la liste des étudiants
```

#### Système d'avis et notes

```javascript
POST /api/courses/:courseId/reviews
Authorization: Bearer <token>

{
  "rating": 5,
  "comment": "Cours excellent ! Les explications sont claires."
}
```

**Fonctionnalités des avis :**
- ⭐ Note de 1 à 5 étoiles
- 💬 Commentaire détaillé
- 👤 Nom de l'auteur affiché
- 📅 Date de publication
- 📊 Note moyenne calculée automatiquement


---

### 🎨 Interface Utilisateur Moderne

**Design System épuré et responsive**

**Caractéristiques :**
- 🎨 Palette de couleurs professionnelle
- 📱 100% Responsive (Mobile, Tablet, Desktop)
- ⚡ Animations fluides et micro-interactions
- 🌓 Mode sombre (optionnel)
- ♿ Accessibilité WCAG 2.1

**Composants réutilisables :**
- Navigation bar avec dropdown
- Cards de cours avec hover effects
- Modals et toasts de notifications
- Forms avec validation en temps réel
- Loading states et skeletons

**Technologies CSS :**
- CSS Modules pour isolation
- Flexbox & Grid Layout
- Transitions et animations CSS3
- Media queries pour responsive

---

## 🏗️ Architecture technique

### Vue d'ensemble

```
┌─────────────────────────────────────────────┐
│           Frontend (React + Vite)            │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐    │
│  │  Pages  │  │Components│  │ Context │    │
│  └────┬────┘  └────┬─────┘  └────┬────┘    │
│       │            │             │          │
│       └────────────┴─────────────┘          │
│                    │                        │
│              Axios HTTP Client               │
└────────────────────┼────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────┐
│          Backend (Node.js + Express)         │
│  ┌─────────┐  ┌──────────┐  ┌──────────┐  │
│  │ Routes  │  │Controllers│  │Middleware│  │
│  └────┬────┘  └────┬──────┘  └────┬─────┘  │
│       │            │              │         │
│       └────────────┴──────────────┘         │
│                    │                        │
│              Mongoose ORM                    │
└────────────────────┼────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────┐
│            MongoDB Database                  │
│  ┌────────┐ ┌────────┐ ┌────────┐          │
│  │ Users  │ │Courses │ │Reviews │          │
│  └────────┘ └────────┘ └────────┘          │
└─────────────────────────────────────────────┘

         External API
              │
              ▼
┌─────────────────────────┐
│   Google Gemini API     │
│   (AI Processing)       │
└─────────────────────────┘
```

---

### Stack détaillée

#### Frontend

```javascript
{
  "framework": "React 18.x",
  "bundler": "Vite 5.x",
  "routing": "React Router DOM 6.x",
  "http": "Axios",
  "state": "Context API + useReducer",
  "styling": "CSS Modules + CSS3"
}
```

#### Backend

```javascript
{
  "runtime": "Node.js 18+",
  "framework": "Express.js 4.x",
  "database": "MongoDB + Mongoose",
  "auth": "JWT (jsonwebtoken) + bcrypt",
  "ai": "Google Gemini API",
  "validation": "express-validator",
  "security": "helmet, cors"
}
```

---

## 🚀 Installation

### Prérequis système

Avant de commencer, assurez-vous d'avoir :

- ✅ **Node.js** ≥ 18.0.0
- ✅ **npm** ≥ 9.0.0 ou **yarn** ≥ 1.22.0
- ✅ **MongoDB** (local ou Atlas)
- ✅ **Clé API Google Gemini** ([Obtenir ici](https://ai.google.dev/))
- ✅ **Git** (pour cloner le projet)

---

### Installation pas-à-pas

#### 1️⃣ Cloner le repository

```bash
# Via HTTPS
git clone https://github.com/imenbenothmen/eduplatform.git

# Via SSH
git clone git@github.com:imenbenothmen/eduplatform.git

# Naviguer dans le dossier
cd eduplatform
```

---

#### 2️⃣ Configuration Backend

```bash
# Naviguer vers le backend
cd backend

# Installer les dépendances
npm install

# Créer le fichier .env
touch .env
```

**Contenu du fichier `.env` :**

```env
# Configuration Serveur
PORT=5000
NODE_ENV=development

# Configuration MongoDB
MONGO_URI=mongodb://localhost:27017/eduplatform
# Ou MongoDB Atlas :
# MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/eduplatform

# Configuration JWT
JWT_SECRET=votre_secret_jwt_minimum_32_caracteres_securise
JWT_EXPIRE=7d

# Configuration Google Gemini AI
GEMINI_API_KEY=votre_cle_api_gemini_ici

# Configuration CORS (Frontend URL)
FRONTEND_URL=http://localhost:5173
```

**Démarrer le serveur backend :**

```bash
# Mode développement avec nodemon
npm run dev

# Mode production
npm start
```

✅ **Backend actif sur** : `http://localhost:5000`

---

#### 3️⃣ Configuration Frontend

**Ouvrir un nouveau terminal :**

```bash
# Depuis la racine du projet
cd frontend

# Installer les dépendances
npm install

# Créer le fichier .env (optionnel)
touch .env
```

**Contenu du fichier `.env` (optionnel) :**

```env
VITE_API_URL=http://localhost:5000/api
```

**Démarrer le serveur frontend :**

```bash
npm run dev
```

✅ **Frontend actif sur** : `http://localhost:5173`

---

### Vérification de l'installation

#### Tester le backend

```bash
# Dans un nouveau terminal
curl http://localhost:5000/api/health

# Réponse attendue :
# { "status": "OK", "message": "Server is running" }
```

#### Tester le frontend

1. Ouvrir le navigateur : `http://localhost:5173`
2. Vous devriez voir la page d'accueil EduPlatform
3. Essayer de vous inscrire et vous connecter

---

## ⚙️ Configuration

### Configuration MongoDB

#### Option 1 : MongoDB Local

```bash
# Installer MongoDB
# macOS (Homebrew)
brew install mongodb-community

# Démarrer MongoDB
brew services start mongodb-community

# Vérifier le statut
brew services list
```

**URI de connexion :**
```
mongodb://localhost:27017/eduplatform
```

---

#### Option 2 : MongoDB Atlas (Cloud)

1. **Créer un compte** sur [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. **Créer un cluster** gratuit (M0)
3. **Créer un utilisateur** de base de données
4. **Whitelist IP** : Autoriser `0.0.0.0/0` (développement uniquement)
5. **Obtenir l'URI** : Cluster → Connect → Connect your application

**Format URI :**
```
mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/eduplatform?retryWrites=true&w=majority
```

---

### Configuration Google Gemini API

#### Obtenir une clé API

1. **Accéder** à [Google AI Studio](https://ai.google.dev/)
2. **Se connecter** avec votre compte Google
3. **Créer une clé API** : Get API Key → Create API Key
4. **Copier la clé** et la sauvegarder

**Ajouter au fichier `.env` :**
```env
GEMINI_API_KEY=AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

#### Quotas et limites

| Plan | Requêtes/minute | Requêtes/jour |
|------|----------------|---------------|
| **Gratuit** | 15 | 1,500 |
| **Payant** | Variable | Illimité |

---

### Configuration JWT

#### Générer un secret sécurisé

**Méthode 1 : Via Node.js**

```bash
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```

**Méthode 2 : Via OpenSSL**

```bash
openssl rand -base64 64
```

**Méthode 3 : Via site web**

Visitez : [randomkeygen.com](https://randomkeygen.com/)

**Important** : Le secret doit faire au moins **32 caractères** !

---

## 📖 Guide d'utilisation

### Pour les Étudiants

#### 1. Créer un compte

```
1. Accéder à http://localhost:5173
2. Cliquer sur "S'inscrire"
3. Remplir le formulaire :
   - Username : votre_pseudo
   - Email : votre@email.com (sans "admin" pour rôle étudiant)
   - Password : minimum 6 caractères
4. Cliquer sur "S'inscrire"
```

#### 2. Parcourir les cours

```
1. Page d'accueil → Section "Cours disponibles"
2. Utiliser la barre de recherche
3. Filtrer par instructeur ou note
4. Cliquer sur un cours pour voir les détails
```

#### 3. S'inscrire à un cours

```
1. Ouvrir la page détails d'un cours
2. Cliquer sur "S'inscrire à ce cours"
3. Le cours apparaîtra dans "Mes Cours"
```

#### 4. Laisser un avis

```
1. Aller dans "Mes Cours"
2. Sélectionner un cours suivi
3. Section "Laisser un avis"
4. Donner une note (1-5 étoiles)
5. Écrire un commentaire
6. Soumettre
```

#### 5. Utiliser le Chatbot

```
1. Cliquer sur l'icône de chat (coin inférieur droit)
2. Poser une question sur les cours
   Exemple : "Quel cours recommandes-tu pour apprendre React ?"
3. Recevoir une réponse instantanée de l'IA
```

#### 6. Générer un quiz

```
1. Ouvrir un cours
2. Cliquer sur "Générer Quiz IA"
3. Choisir :
   - Niveau de difficulté (Facile/Moyen/Difficile)
   - Nombre de questions (5-20)
4. Cliquer sur "Générer"
5. Passer le quiz et voir vos résultats
```

#### 7. Voir les recommandations

```
1. Navbar → "Cours Recommandés"
2. L'IA analyse votre profil
3. Affichage des 5 meilleurs cours pour vous
4. Cliquer sur un cours pour s'inscrire
```

---

### Pour les Administrateurs

#### Devenir administrateur

**Important** : Inscrivez-vous avec un email contenant **"admin"**

```
Exemples valides :
- admin@eduplatform.com
- superadmin@example.com
- imen.admin@gmail.com
```

#### Accéder au Dashboard Admin

```
1. Se connecter avec un compte admin
2. Navbar → "Dashboard"
3. Vue d'ensemble de la plateforme
```

#### Fonctionnalités du Dashboard

**Métriques affichées :**

```javascript
- Nombre total de cours
- Nombre total d'étudiants
- Nombre total d'avis
- Note moyenne globale
- Cours le plus populaire
- Tendances d'inscription
- Recommandations IA pour améliorer la plateforme
```

**Actions disponibles :**

```
1. Créer un nouveau cours
2. Modifier un cours existant
3. Supprimer un cours
4. Gérer les utilisateurs
5. Consulter les analytics détaillées
6. Générer des rapports
```

#### Créer un cours

```
1. Dashboard → "Créer un cours"
2. Remplir le formulaire :
   - Titre du cours
   - Description complète
   - Instructeur
   - Durée estimée
   - Objectifs pédagogiques
3. (Optionnel) Générer la description avec l'IA
4. Soumettre
```

---

## 📁 Structure du projet

```
eduplatform/
│
├── 📂 backend/
│   ├── 📂 config/
│   │   └── db.js                      # Configuration MongoDB
│   │
│   ├── 📂 controllers/
│   │   ├── authController.js          # Login, Register
│   │   ├── userController.js          # CRUD Users
│   │   ├── courseController.js        # CRUD Courses
│   │   ├── reviewController.js        # CRUD Reviews
│   │   └── aiController.js            # ⭐ Toutes les fonctionnalités IA
│   │       ├── generateQuiz()
│   │       ├── chatbotResponse()
│   │       ├── getRecommendations()
│   │       ├── generateBio()
│   │       └── getDashboardInsights()
│   │
│   ├── 📂 middleware/
│   │   ├── authMiddleware.js          # Protection JWT
│   │   └── errorMiddleware.js         # Gestion erreurs
│   │
│   ├── 📂 models/
│   │   ├── User.js                    # Schema utilisateur
│   │   ├── Course.js                  # Schema cours
│   │   └── Review.js                  # Schema avis
│   │
│   ├── 📂 routes/
│   │   ├── authRoutes.js              # /api/auth/*
│   │   ├── userRoutes.js              # /api/users/*
│   │   ├── courseRoutes.js            # /api/courses/*
│   │   ├── reviewRoutes.js            # /api/reviews/*
│   │   └── aiRoutes.js                # /api/ai/*
│   │
│   ├── .env                           # Variables d'environnement
│   ├── .gitignore
│   ├── package.json
│   └── server.js                      # Point d'entrée
│
├── 📂 frontend/
│   ├── 📂 public/
│   │   └── vite.svg
│   │
│   ├── 📂 src/
│   │   │
│   │   ├── 📂 api/
│   │   │   └── axios.js               # Configuration Axios
│   │   │
│   │   ├── 📂 components/
│   │   │   ├── Navbar.jsx             # Barre de navigation
│   │   │   ├── CourseCard.jsx         # Card de cours
│   │   │   ├── ReviewCard.jsx         # Card d'avis
│   │   │   ├── Chatbot.jsx            # ⭐ Widget chatbot
│   │   │   ├── QuizGenerator.jsx      # ⭐ Générateur quiz
│   │   │   ├── LoadingSpinner.jsx     # Loading state
│   │   │   └── Modal.jsx              # Composant modal
│   │   │
│   │   ├── 📂 context/
│   │   │   └── AuthContext.jsx        # Gestion authentification
│   │   │
│   │   ├── 📂 pages/
│   │   │   ├── Home.jsx               # Page d'accueil
│   │   │   ├── Login.jsx              # Page connexion
│   │   │   ├── Register.jsx           # Page inscription
│   │   │   ├── Courses.jsx            # Liste des cours
│   │   │   ├── CourseDetail.jsx       # Détails d'un cours
│   │   │   ├── MyCourses.jsx          # Mes cours suivis
│   │   │   ├── Profile.jsx            # Profil utilisateur
│   │   │   ├── Dashboard.jsx          # ⭐ Dashboard admin IA
│   │   │   ├── Recommendations.jsx    # ⭐ Cours recommandés IA
│   │   │   └── NotFound.jsx           # Page 404
│   │   │
│   │   ├── 📂 styles/
│   │   │   ├── App.css                # Styles globaux
│   │   │   ├── Navbar.css
│   │   │   ├── Courses.css
│   │   │   ├── Dashboard.css
│   │   │   └── Chatbot.css
│   │   │
│   │   ├── App.jsx                    # Composant principal
│   │   ├── main.jsx                   # Point d'entrée
│   │   └── index.css                  # CSS reset
│   │
│   ├── .env                           # Variables frontend (optionnel)
│   ├── .gitignore
│   ├── package.json
│   ├── vite.config.js
│   └── index.html
│
├── 📂 img/                            # Captures d'écran
│   ├── demo.gif
│   ├── dashboard-admin.png
│   ├── chatbot.png
│   ├── quiz-generator.png
│   ├── recommendations.png
│   └── courses-catalog.png
│
├── README.md                          # Ce fichier
├── .gitignore
└── package.json                       # Workspace (optionnel)
```

---

## 🔌 API Endpoints

### Authentification

| Méthode | Endpoint | Description | Auth |
|---------|----------|-------------|------|
| `POST` | `/api/auth/register` | Créer un compte | ❌ |
| `POST` | `/api/auth/login` | Se connecter | ❌ |

---

### Utilisateurs

| Méthode | Endpoint | Description | Auth |
|---------|----------|-------------|------|
| `GET` | `/api/users` | Liste utilisateurs | ✅ |
| `GET` | `/api/users/:id` | Détails utilisateur | ✅ |
| `PUT` | `/api/users/:id` | Modifier profil | ✅ |
| `GET` | `/api/users/:id/courses` | Cours de l'utilisateur | ✅ |

---

### Cours

| Méthode | Endpoint | Description | Auth |
|---------|----------|-------------|------|
| `GET` | `/api/courses` | Liste tous les cours | ❌ |
| `GET` | `/api/courses/:id` | Détails d'un cours | ❌ |
| `POST` | `/api/courses` | Créer un cours | ✅ Admin |
| `PUT` | `/api/courses/:id` | Modifier un cours | ✅ Admin |
| `DELETE` | `/api/courses/:id` | Supprimer un cours | ✅ Admin |
| `POST` | `/api/courses/:id/enroll` | S'inscrire au cours | ✅ |

---

### Avis (Reviews)

| Méthode | Endpoint | Description | Auth |
|---------|----------|-------------|------|
| `GET` | `/api/courses/:id/reviews` | Avis d'un cours | ❌ |
| `POST` | `/api/courses/:id/reviews` | Ajouter un avis | ✅ |
| `DELETE` | `/api/reviews/:id` | Supprimer un avis | ✅ |

---

### Intelligence Artificielle 🤖

| Méthode | Endpoint | Description | Auth |
|---------|----------|-------------|------|
| `POST` | `/api/ai/generate-quiz` | Générer un quiz | ✅ |
| `POST` | `/api/ai/chatbot` | Poser une question | ✅ |
| `GET` | `/api/ai/recommendations` | Cours recommandés | ✅ |
| `POST` | `/api/ai/generate-bio` | Générer une bio | ✅ |
| `GET` | `/api/ai/dashboard-insights` | Analytics admin | ✅ Admin |


## 🛠️ Technologies utilisées

### Frontend

| Technologie | Version | Utilisation |
|------------|---------|-------------|
| **React** | 18.2.0 | UI Library |
| **Vite** | 5.0.0 | Build Tool |
| **React Router** | 6.20.0 | Navigation |
| **Axios** | 1.6.0 | HTTP Client |
| **Context API** | Native | State Management |

### Backend

| Technologie | Version | Utilisation |
|------------|---------|-------------|
| **Node.js** | 18+ | Runtime |
| **Express** | 4.18.2 | Web Framework |
| **MongoDB** | 6.0+ | Database |
| **Mongoose** | 8.0.0 | ODM |
| **JWT** | 9.0.2 | Authentication |
| **bcrypt** | 5.1.1 | Password Hashing |

### Intelligence Artificielle

| Technologie | Version | Utilisation |
|------------|---------|-------------|
| **Google Gemini** | 2.0 Flash | Génération contenu |
| **@google/generative-ai** | Latest | SDK Node.js |

### Outils de développement

| Outil | Utilisation |
|-------|-------------|
| **Git** | Versioning |
| **Postman** | API Testing |
| **VS Code** | Code Editor |
| **ESLint** | Code Linting |
| **Prettier** | Code Formatting |

---

## 🔒 Sécurité

### Mesures de sécurité implémentées

#### Authentification

```javascript
// JWT avec expiration
const token = jwt.sign(
  { userId: user._id, role: user.role },
  process.env.JWT_SECRET,
  { expiresIn: '7d' }
);

// Hashage des mots de passe
const hashedPassword = await bcrypt.hash(password, 10);
```

#### Protection des routes

```javascript
// Middleware de protection
const protect = async (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1];
  
  if (!token) {
    return res.status(401).json({ message: 'Non autorisé' });
  }
  
  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (error) {
    return res.status(401).json({ message: 'Token invalide' });
  }
};
```

#### Validation des données

```javascript
// Express Validator
body('email').isEmail().normalizeEmail(),
body('password').isLength({ min: 6 })
```

#### Headers de sécurité

```javascript
// Helmet.js
app.use(helmet());

// CORS configuré
app.use(cors({
  origin: process.env.FRONTEND_URL,
  credentials: true
}));
```

#### Variables sensibles

```
✅ Toutes les clés dans .env
✅ .env dans .gitignore
✅ Pas de secrets en dur dans le code
✅ Rotation régulière des secrets
```

---

## 👩‍💻 Auteur

**Imen BEN OTHMEN BANANI**


### À propos de moi

Passionnée par le développement web et l'Intelligence Artificielle, je crée des applications modernes qui combinent technologie et innovation. EduPlatform représente la convergence de mes compétences en Full Stack Development et en Data Science.

**Compétences clés :**
- 🎯 Full Stack MERN (MongoDB, Express, React, Node.js)
- 🤖 Intégration IA (Google Gemini, OpenAI)
- 📊 Data Science & Machine Learning
- 🎨 UI/UX Design
- 🔐 Sécurité & Authentification

---

## 📅 Informations du projet

| Paramètre | Valeur |
|-----------|--------|
| **Nom** | EduPlatform - Plateforme Éducative IA |
| **Type** | TP10 - React & Intelligence Artificielle |
| **Formation** | MERN Stack Development |
| **Date de création** | Décembre 2024 |
| **Dernière mise à jour** | 16 Décembre 2024 |
| **Version** | 1.0.0 |
| **Statut** | ✅ Production Ready |

---

## 🙏 Remerciements

- 👨‍🏫 **Mes formateurs** pour leur accompagnement
- 🤝 **La communauté MERN** pour les ressources partagées
- 🤖 **Google AI Team** pour l'API Gemini
- 💡 **Tous les contributeurs** open-source

---

## 📚 Ressources complémentaires

### Documentation officielle

- 📘 [React Documentation](https://react.dev/)
- 📗 [Node.js Documentation](https://nodejs.org/docs/)
- 📕 [MongoDB Documentation](https://www.mongodb.com/docs/)
- 📙 [Google Gemini API](https://ai.google.dev/docs)
- 📓 [Express.js Guide](https://expressjs.com/)


---

## 🐛 Problèmes connus et solutions

### Problème : "Cannot connect to MongoDB"

**Solution :**
```bash
# Vérifier que MongoDB est démarré
brew services list  # macOS
sudo systemctl status mongod  # Linux

# Vérifier l'URI dans .env
MONGO_URI=mongodb://localhost:27017/eduplatform
```

---

### Problème : "GEMINI_API_KEY error"

**Solution :**
```bash
# Vérifier que la clé est dans .env
GEMINI_API_KEY=votre_cle_ici

# Redémarrer le serveur backend
npm run dev
```

---

### Problème : "JWT Token Invalid"

**Solution :**
```bash
# Se reconnecter pour obtenir un nouveau token
# Vérifier JWT_SECRET dans .env
# Vérifier l'expiration (7 jours par défaut)
```

---

## 🔮 Fonctionnalités futures

- [ ] 📱 Application mobile (React Native)
- [ ] 🎥 Support vidéos et streaming
- [ ] 💳 Système de paiement pour cours premium
- [ ] 🏆 Badges et certifications
- [ ] 📊 Analytics avancées pour étudiants
- [ ] 🌐 Support multilingue (i18n)
- [ ] 🔔 Notifications en temps réel
- [ ] 👥 Messagerie entre utilisateurs
- [ ] 📝 Éditeur de cours Markdown
- [ ] 🎨 Personnalisation de thème

---

## 📞 Contact et Support

### Besoin d'aide ?

- 📧 **Email** : imenbenothmenbanani@gmail.com


### Contribuer au projet

Les contributions sont les bienvenues ! Consultez [CONTRIBUTING.md](CONTRIBUTING.md) pour les guidelines.

---

<div align="center">

## ⭐ Si ce projet vous inspire, donnez-lui une étoile ! ⭐


</div>

---

**🎓 EduPlatform** • Made with 💜 in Tunisia • © 2024
