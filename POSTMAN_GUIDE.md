# 🎯 Guide Complet - Test API MERN avec Postman

> **"De l'authentification à l'IA : Testez votre API comme un pro"**

[![Postman](https://img.shields.io/badge/Postman-FF6C37?logo=postman&logoColor=white)](https://www.postman.com/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white)](https://mongodb.com/)

---

## 📑 Table des Matières

1. [Vue d'ensemble](#-vue-densemble)
2. [Configuration initiale](#-configuration-initiale)
3. [Données de test fournies](#-données-de-test-fournies)
4. [Routes publiques](#-routes-publiques)
5. [Routes protégées](#-routes-protégées)
6. [Fonctionnalités IA](#-fonctionnalités-ia)
7. [Scénarios de test complets](#-scénarios-de-test-complets)
8. [Gestion des erreurs](#-gestion-des-erreurs)
9. [Astuces Postman avancées](#-astuces-postman-avancées)

---

## 🌟 Vue d'ensemble

### Architecture de l'API

```
API MERN TP9
│
├── 🔓 Routes Publiques
│   ├── Consultation des cours
│   ├── Détails d'un cours
│   ├── Avis sur un cours
│   └── Liste des étudiants
│
├── 🔐 Routes Protégées (JWT)
│   ├── Authentification (register/login)
│   ├── Gestion des cours (CRUD)
│   ├── Inscription aux cours
│   ├── Gestion des avis
│   └── Profils utilisateurs
│
└── 🤖 Routes IA (Gemini API)
    ├── Analyse de sentiments
    ├── Génération de descriptions
    ├── Recommandations de cours
    ├── Génération de biographies
    └── Insights de plateforme
```

### Technologies utilisées

| Techno | Version | Rôle |
|--------|---------|------|
| Node.js | 18+ | Runtime backend |
| Express | 4.x | Framework web |
| MongoDB | 6+ | Base de données |
| JWT | - | Authentification |
| Gemini AI | 2.0 | Fonctionnalités IA |
| Postman | Latest | Tests API |

---

## ⚙️ Configuration initiale

### Étape 1 : Préparer l'environnement backend

```bash
# 1. Cloner le projet
git clone <repository-url>
cd backend

# 2. Installer les dépendances
npm install

# 3. Configurer les variables d'environnement
cp .env.example .env
```

**Fichier `.env` requis :**

```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/mern_tp9
JWT_SECRET=votre_secret_jwt_super_securise
GEMINI_API_KEY=votre_cle_api_gemini
NODE_ENV=development
```

```bash
# 4. Démarrer le serveur
npm start

# ✅ Serveur actif sur http://localhost:3000
```

---

### Étape 2 : Configuration Postman

#### Importer la collection

1. **Télécharger** : `MERN_TP9_COMPLETE.postman_collection.json`
2. **Ouvrir Postman** → Bouton **Import**
3. **Glisser-déposer** le fichier ou le sélectionner
4. ✅ Collection importée !

#### Créer l'environnement

**Menu** : Environments → Create Environment

**Nom** : `MERN TP9 - Development`

**Variables à créer :**

| Variable | Initial Value | Current Value |
|----------|---------------|---------------|
| `base_url` | `http://localhost:3000/api` | `http://localhost:3000/api` |
| `jwt_token` | *(vide)* | *(sera auto-rempli)* |
| `user_id` | *(vide)* | *(sera auto-rempli)* |
| `courseId` | *(vide)* | *(sera auto-rempli)* |

**Sélectionner** cet environnement dans le dropdown en haut à droite.

---

## 🔑 Données de test fournies

### Compte administrateur pré-configuré

**Utilisez ces identifiants pour un accès immédiat :**

```json
{
  "email": "admin1000@example.com",
  "password": "admin1000"
}
```

**Token JWT fourni (valide jusqu'au 16 juin 2025) :**

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiI2OTQwODM4ODQzMDg1ZWMyZDg1ODk4NTciLCJlbWFpbCI6ImFkbWluMTAwMEBleGFtcGxlLmNvbSIsInJvbGUiOiJhZG1pbiIsImlhdCI6MTc2NTgzNTY1NiwiZXhwIjoxNzY2NDQwNDU2fQ.LYAWg0OhckvpCvQUGhVKoBNWlcgMszmMQH_lJua33MY
```

**Informations utilisateur :**

```json
{
  "id": "6940838843085ec2d8589857",
  "username": "admin1000",
  "email": "admin1000@example.com",
  "role": "admin"
}
```

#### 🚀 Utilisation directe

**Option A : Configuration manuelle**

1. Dans Postman → Environment variables
2. Coller le token dans `jwt_token`
3. Coller l'ID dans `user_id`
4. Tester directement les routes protégées

**Option B : Login automatique**

Utilisez la route **POST /api/auth/login** avec :

```json
{
  "email": "admin1000@example.com",
  "password": "admin1000"
}
```

Le token sera automatiquement sauvegardé.

---

### Utilisateurs de test supplémentaires

```javascript
// Étudiant 1
{
  "username": "student_react",
  "email": "react.student@example.com",
  "password": "ReactPass123",
  "role": "student"
}

// Étudiant 2
{
  "username": "student_node",
  "email": "node.student@example.com",
  "password": "NodePass123",
  "role": "student"
}

// Instructeur
{
  "username": "prof_javascript",
  "email": "prof.js@example.com",
  "password": "TeachJS2024",
  "role": "instructor"
}
```

---

## 🔓 Routes publiques

> Aucune authentification requise pour ces endpoints

### 1. Liste de tous les cours

```http
GET {{base_url}}/courses
```

**Réponse attendue (200 OK) :**

```json
[
  {
    "_id": "507f1f77bcf86cd799439011",
    "title": "Introduction à React",
    "description": "Apprenez les bases de React",
    "instructor": "John Doe",
    "students": [],
    "reviews": [],
    "createdAt": "2024-12-15T10:30:00.000Z"
  }
]
```

---

### 2. Détails d'un cours spécifique

```http
GET {{base_url}}/courses/:id
```

**Exemple :**
```
GET {{base_url}}/courses/507f1f77bcf86cd799439011
```

**Réponse (200 OK) :**

```json
{
  "_id": "507f1f77bcf86cd799439011",
  "title": "Introduction à React",
  "description": "Cours complet sur React",
  "instructor": "John Doe",
  "students": [
    {
      "_id": "608f1f77bcf86cd799439012",
      "username": "student1",
      "email": "student1@example.com"
    }
  ],
  "reviews": [
    {
      "userId": "608f1f77bcf86cd799439012",
      "rating": 5,
      "comment": "Excellent cours!",
      "createdAt": "2024-12-10T14:20:00.000Z"
    }
  ]
}
```

---

### 3. Avis d'un cours

```http
GET {{base_url}}/courses/:id/reviews
```

**Réponse (200 OK) :**

```json
[
  {
    "userId": {
      "_id": "608f1f77bcf86cd799439012",
      "username": "student1"
    },
    "rating": 5,
    "comment": "Très bon cours, bien expliqué!",
    "createdAt": "2024-12-10T14:20:00.000Z"
  },
  {
    "userId": {
      "_id": "608f1f77bcf86cd799439013",
      "username": "student2"
    },
    "rating": 4,
    "comment": "Intéressant mais pourrait avoir plus d'exemples",
    "createdAt": "2024-12-11T09:15:00.000Z"
  }
]
```

---

### 4. Liste des étudiants inscrits

```http
GET {{base_url}}/courses/:id/students
```

**Réponse (200 OK) :**

```json
[
  {
    "_id": "608f1f77bcf86cd799439012",
    "username": "student_react",
    "email": "react.student@example.com",
    "enrolledAt": "2024-12-08T10:00:00.000Z"
  },
  {
    "_id": "608f1f77bcf86cd799439013",
    "username": "student_node",
    "email": "node.student@example.com",
    "enrolledAt": "2024-12-09T11:30:00.000Z"
  }
]
```

---

## 🔐 Routes protégées

> Nécessitent un token JWT dans le header Authorization

### Configuration du header

**Toutes les routes protégées nécessitent :**

```
Authorization: Bearer {{jwt_token}}
```

Dans Postman :
- **Tab Authorization** → Type: **Bearer Token**
- Token: `{{jwt_token}}`

---

### 🔑 Authentification

#### A. Créer un compte

```http
POST {{base_url}}/auth/register
Content-Type: application/json
```

**Body :**

```json
{
  "username": "nouveau_user",
  "email": "nouveau@example.com",
  "password": "SecurePass123",
  "confirmPassword": "SecurePass123"
}
```

**Réponse (201 Created) :**

```json
{
  "message": "Utilisateur créé avec succès",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "6940838843085ec2d8589999",
    "username": "nouveau_user",
    "email": "nouveau@example.com",
    "role": "student"
  }
}
```

**Script Postman (Tests tab) :**

```javascript
if (pm.response.code === 201) {
    const response = pm.response.json();
    pm.environment.set("jwt_token", response.token);
    pm.environment.set("user_id", response.user.id);
    console.log("✅ Token sauvegardé automatiquement");
}
```

---

#### B. Se connecter

```http
POST {{base_url}}/auth/login
Content-Type: application/json
```

**Body (avec compte admin fourni) :**

```json
{
  "email": "admin1000@example.com",
  "password": "admin1000"
}
```

**Réponse (200 OK) :**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "6940838843085ec2d8589857",
    "username": "admin1000",
    "email": "admin1000@example.com",
    "role": "admin"
  }
}
```

---

### 📚 Gestion des cours

#### C. Créer un cours

```http
POST {{base_url}}/courses
Authorization: Bearer {{jwt_token}}
Content-Type: application/json
```

**Body :**

```json
{
  "title": "React Hooks Avancés",
  "description": "Maîtrisez useState, useEffect et useReducer",
  "instructor": "Imen Ben Othmen"
}
```

**Réponse (201 Created) :**

```json
{
  "_id": "507f1f77bcf86cd799439099",
  "title": "React Hooks Avancés",
  "description": "Maîtrisez useState, useEffect et useReducer",
  "instructor": "Imen Ben Othmen",
  "students": [],
  "reviews": [],
  "createdAt": "2024-12-15T15:45:00.000Z"
}
```

**Script Postman (Tests tab) :**

```javascript
if (pm.response.code === 201) {
    const response = pm.response.json();
    pm.environment.set("courseId", response._id);
    console.log("✅ Course ID sauvegardé: " + response._id);
}
```

---

#### D. S'inscrire à un cours

```http
POST {{base_url}}/courses/:id/enroll
Authorization: Bearer {{jwt_token}}
```

**Exemple :**
```
POST {{base_url}}/courses/{{courseId}}/enroll
```

**Réponse (200 OK) :**

```json
{
  "message": "Inscription réussie au cours",
  "course": {
    "_id": "507f1f77bcf86cd799439099",
    "title": "React Hooks Avancés",
    "students": ["6940838843085ec2d8589857"]
  }
}
```

---

### ⭐ Gestion des avis

#### E. Ajouter un avis

```http
POST {{base_url}}/courses/:id/reviews
Authorization: Bearer {{jwt_token}}
Content-Type: application/json
```

**Body :**

```json
{
  "rating": 5,
  "comment": "Excellent cours ! J'ai beaucoup appris sur les hooks React."
}
```

**Réponse (201 Created) :**

```json
{
  "message": "Avis ajouté avec succès",
  "review": {
    "userId": "6940838843085ec2d8589857",
    "rating": 5,
    "comment": "Excellent cours ! J'ai beaucoup appris sur les hooks React.",
    "createdAt": "2024-12-15T16:00:00.000Z"
  }
}
```

---

#### F. Mes avis

```http
GET {{base_url}}/users/:userId/reviews
Authorization: Bearer {{jwt_token}}
```

**Exemple :**
```
GET {{base_url}}/users/{{user_id}}/reviews
```

**Réponse (200 OK) :**

```json
[
  {
    "courseId": {
      "_id": "507f1f77bcf86cd799439099",
      "title": "React Hooks Avancés"
    },
    "rating": 5,
    "comment": "Excellent cours !",
    "createdAt": "2024-12-15T16:00:00.000Z"
  }
]
```

---

### 👤 Gestion du profil

#### G. Créer mon profil

```http
POST {{base_url}}/users/:userId/profile
Authorization: Bearer {{jwt_token}}
Content-Type: application/json
```

**Body :**

```json
{
  "bio": "Développeuse Full Stack passionnée par React et Node.js. Étudiante en Data Science.",
  "website": "https://imen-portfolio.dev",
  "socialLinks": {
    "linkedin": "https://linkedin.com/in/imen-dev",
    "github": "https://github.com/imendev"
  }
}
```

**Réponse (201 Created) :**

```json
{
  "message": "Profil créé avec succès",
  "profile": {
    "userId": "6940838843085ec2d8589857",
    "bio": "Développeuse Full Stack passionnée...",
    "website": "https://imen-portfolio.dev",
    "socialLinks": {
      "linkedin": "https://linkedin.com/in/imen-dev",
      "github": "https://github.com/imendev"
    },
    "createdAt": "2024-12-15T16:10:00.000Z"
  }
}
```

---

#### H. Consulter mon profil

```http
GET {{base_url}}/users/:userId/profile
Authorization: Bearer {{jwt_token}}
```

---

#### I. Mettre à jour mon profil

```http
PUT {{base_url}}/users/:userId/profile
Authorization: Bearer {{jwt_token}}
Content-Type: application/json
```

**Body :**

```json
{
  "bio": "Développeuse Full Stack | React & Node.js Expert | Data Science Student",
  "website": "https://imen-benothmen.dev"
}
```

---

## 🤖 Fonctionnalités IA

> Propulsé par Gemini AI pour des fonctionnalités intelligentes

### 1. Générer une description de cours

```http
POST {{base_url}}/ai/generate-description
Content-Type: application/json
```

**Body :**

```json
{
  "title": "Python pour Data Science",
  "instructor": "Dr. Marie Laurent",
  "keywords": ["Python", "Machine Learning", "Pandas", "NumPy", "Scikit-learn"]
}
```

**Réponse (200 OK) :**

```json
{
  "description": "Plongez dans l'univers de la Data Science avec Python ! Ce cours complet vous guidera à travers les bibliothèques essentielles comme Pandas pour la manipulation de données, NumPy pour le calcul numérique, et Scikit-learn pour le Machine Learning. Apprenez à analyser, visualiser et modéliser vos données avec des cas pratiques concrets. Idéal pour débutants et professionnels souhaitant maîtriser l'écosystème Python Data Science."
}
```

**⏱️ Temps de réponse** : 2-4 secondes

---

### 2. Analyser les avis d'un cours

```http
POST {{base_url}}/ai/analyze-reviews/:id
Authorization: Bearer {{jwt_token}}
```

**Prérequis** : Le cours doit avoir au moins 1 avis.

**Exemple :**
```
POST {{base_url}}/ai/analyze-reviews/{{courseId}}
```

**Réponse (200 OK) :**

```json
{
  "analysis": {
    "overallSentiment": "Très positif",
    "strengths": [
      "Explications claires et structurées",
      "Exercices pratiques pertinents",
      "Bon rythme de progression"
    ],
    "improvements": [
      "Ajouter plus d'exemples de projets réels",
      "Inclure des quiz intermédiaires"
    ],
    "averageRating": 4.6,
    "totalReviews": 8,
    "recommendation": "Ce cours est fortement recommandé pour les débutants souhaitant maîtriser React Hooks."
  }
}
```

**⏱️ Temps de réponse** : 3-5 secondes

---

### 3. Trouver des cours similaires

```http
POST {{base_url}}/ai/similar-courses/:id
```

**Exemple :**
```
POST {{base_url}}/ai/similar-courses/507f1f77bcf86cd799439099
```

**Réponse (200 OK) :**

```json
{
  "similarCourses": [
    {
      "_id": "507f1f77bcf86cd799439088",
      "title": "React Context API & Redux",
      "instructor": "Jane Smith",
      "similarity": 0.87
    },
    {
      "_id": "507f1f77bcf86cd799439077",
      "title": "React Performance Optimization",
      "instructor": "Bob Johnson",
      "similarity": 0.79
    }
  ],
  "reason": "Ces cours partagent des concepts similaires autour de React et la gestion d'état."
}
```

---

### 4. Générer une bio professionnelle

```http
POST {{base_url}}/ai/generate-bio
Content-Type: application/json
```

**Body :**

```json
{
  "interests": "Full-stack development, React, Node.js, Data Science",
  "experience": "4 ans d'études en Data Science, projets MERN Stack",
  "goals": "Devenir développeuse Full Stack senior et contribuer à des projets open-source"
}
```

**Réponse (200 OK) :**

```json
{
  "bio": "Étudiante passionnée en Data Science avec une spécialisation en développement Full Stack. Experte en React et Node.js, je crée des applications web modernes et performantes. Mon objectif : devenir développeuse Full Stack senior et apporter ma contribution à la communauté open-source. Toujours curieuse d'apprendre de nouvelles technologies et de relever des défis techniques complexes."
}
```

---

### 5. Insights de la plateforme

```http
GET {{base_url}}/ai/platform-insights
Authorization: Bearer {{jwt_token}}
```

**Réponse (200 OK) :**

```json
{
  "insights": {
    "totalCourses": 47,
    "totalStudents": 234,
    "averageRating": 4.3,
    "mostPopularCourse": {
      "title": "React Hooks Avancés",
      "students": 89,
      "rating": 4.8
    },
    "trends": [
      "Forte demande pour les cours de React et Vue.js",
      "Les cours avec projets pratiques ont 40% plus d'inscriptions",
      "Les étudiants privilégient les cours courts (< 10h)"
    ],
    "recommendations": [
      "Créer plus de contenus sur TypeScript et Next.js",
      "Ajouter des certifications pour augmenter l'engagement",
      "Développer des parcours d'apprentissage structurés"
    ]
  }
}
```

**⏱️ Temps de réponse** : 5-7 secondes

---

## 🎬 Scénarios de test complets

### Scénario 1 : Parcours étudiant complet

**Objectif** : Simuler un nouvel étudiant qui s'inscrit, explore, et s'engage sur la plateforme.

```javascript
// Étape 1 : Créer un compte
POST /api/auth/register
Body: {
  "username": "marie_dupont",
  "email": "marie.dupont@example.com",
  "password": "SecurePass123",
  "confirmPassword": "SecurePass123"
}
// ✅ Token sauvegardé automatiquement

// Étape 2 : Parcourir les cours disponibles
GET /api/courses
// ✅ Récupérer la liste complète

// Étape 3 : Consulter les détails d'un cours
GET /api/courses/{{courseId}}
// ✅ Voir description, instructeur, avis

// Étape 4 : Lire les avis du cours
GET /api/courses/{{courseId}}/reviews
// ✅ Analyser les retours d'expérience

// Étape 5 : S'inscrire au cours
POST /api/courses/{{courseId}}/enroll
// ✅ Inscription confirmée

// Étape 6 : Ajouter un avis après avoir "suivi" le cours
POST /api/courses/{{courseId}}/reviews
Body: {
  "rating": 5,
  "comment": "Cours exceptionnel ! Les exemples pratiques m'ont vraiment aidée."
}
// ✅ Avis publié

// Étape 7 : Créer son profil professionnel
POST /api/users/{{user_id}}/profile
Body: {
  "bio": "Étudiante en Data Science passionnée par le développement web",
  "website": "https://marie-portfolio.com"
}
// ✅ Profil créé

// Étape 8 : Consulter mes cours
GET /api/users/{{user_id}}/courses
// ✅ Liste de mes inscriptions

// Étape 9 : Consulter tous mes avis
GET /api/users/{{user_id}}/reviews
// ✅ Historique complet
```

**✅ Résultat attendu** : Parcours fluide sans erreur, toutes les données sont persistées.

---

### Scénario 2 : Test complet des fonctionnalités IA

**Objectif** : Explorer toutes les capacités IA de la plateforme.

```javascript
// Étape 1 : Générer une description de cours IA
POST /api/ai/generate-description
Body: {
  "title": "TypeScript pour React",
  "instructor": "Alexandre Martin",
  "keywords": ["TypeScript", "React", "Types", "Interfaces"]
}
// ✅ Description professionnelle générée

// Étape 2 : Créer le cours avec la description IA
POST /api/courses
Body: {
  "title": "TypeScript pour React",
  "description": "<utiliser la description générée>",
  "instructor": "Alexandre Martin"
}
// ✅ Cours créé avec courseId sauvegardé

// Étape 3 : Ajouter plusieurs avis au cours
POST /api/courses/{{courseId}}/reviews (répéter 5 fois)
Bodies variés: ratings 4-5, commentaires différents
// ✅ 5 avis ajoutés

// Étape 4 : Analyser les avis avec l'IA
POST /api/ai/analyze-reviews/{{courseId}}
// ✅ Analyse de sentiment complète

// Étape 5 : Trouver des cours similaires
POST /api/ai/similar-courses/{{courseId}}
// ✅ Recommandations intelligentes

// Étape 6 : Générer une bio professionnelle
POST /api/ai/generate-bio
Body: {
  "interests": "TypeScript, React, Architecture logicielle",
  "experience": "5 ans développement frontend",
  "goals": "Devenir architecte solutions"
}
// ✅ Bio professionnelle créée

// Étape 7 : Obtenir les insights de plateforme
GET /api/ai/platform-insights
// ✅ Analyse complète des tendances

// Étape 8 : Mettre à jour le profil avec la bio IA
PUT /api/users/{{user_id}}/profile
Body: {
  "bio": "<utiliser la bio générée>"
}
// ✅ Profil enrichi avec IA
```

**⏱️ Temps total** : ~30-40 secondes (appels IA inclus)

---

### Scénario 3 : Création de contenu en masse

**Objectif** : Peupler la base de données rapidement pour tester l'échelle.

```javascript
// Créer 10 cours différents (copier-coller rapide)

// Cours 1
POST /api/courses
Body: {"title":"React Fundamentals","description":"Basics of React","instructor":"John Doe"}

// Cours 2
POST /api/courses
Body: {"title":"Node.js Advanced","description":"Master Node.js","instructor":"Jane Smith"}

// Cours 3
POST /api/courses
Body: {"title":"MongoDB Guide","description":"NoSQL databases","instructor":"Bob Johnson"}

// Cours 4
POST /api/courses
Body: {"title":"Express.js Essentials","description":"Backend with Express","instructor":"Alice Brown"}

// Cours 5
POST /api/courses
Body: {"title":"TypeScript Basics","description":"Static typing in JS","instructor":"Charlie Wilson"}

// ... répéter pour 10 cours

// Pour chaque cours créé, ajouter 3-5 avis
POST /api/courses/{{courseId}}/reviews
// Varier les ratings et commentaires

// Résultat : 10 cours avec 30-50 avis au total
```

---

## ⚠️ Gestion des erreurs

### Erreurs courantes et solutions

#### 1. **401 Unauthorized**

**Erreur :**
```json
{
  "error": "Token manquant ou invalide"
}
```

**Causes possibles :**
- Token JWT absent du header
- Token expiré
- Format du token incorrect

**Solutions :**
1. Vérifier que `Authorization: Bearer {{jwt_token}}` est dans le header
2. Re-login pour obtenir un token frais
3. Vérifier que le token dans l'environnement est correct

---

#### 2. **404 Not Found**

**Erreur :**
```json
{
  "error": "Cours non trouvé"
}
```

**Causes :**
- ID de cours invalide
- Cours supprimé
- Erreur de typo dans l'ID

**Solutions :**
1. Utiliser `GET /api/courses` pour obtenir des IDs valides
2. Vérifier que `{{courseId}}` est bien défini dans l'environnement
3. Copier-coller l'ID depuis la réponse de création

---

#### 3. **500 Internal Server Error (Routes IA)**

**Erreur