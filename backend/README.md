# 🔐 API REST MERN - Authentification JWT & Gestion de Cours

> **"Sécurité, simplicité et performance : Une API moderne pour l'éducation en ligne"**

[![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white)](https://mongodb.com/)
[![JWT](https://img.shields.io/badge/JWT-000000?logo=jsonwebtokens&logoColor=white)](https://jwt.io/)

---

## 📋 Table des Matières

1. [À propos du projet](#-à-propos-du-projet)
2. [Fonctionnalités principales](#-fonctionnalités-principales)
3. [Architecture et technologies](#-architecture-et-technologies)
4. [Installation rapide](#-installation-rapide)
5. [Configuration](#-configuration)
6. [Compte de test](#-compte-de-test)
7. [Documentation API](#-documentation-api)
8. [Modèles de données](#-modèles-de-données)
9. [Sécurité JWT](#-sécurité-jwt)
10. [Tests avec Postman](#-tests-avec-postman)
11. [Structure du projet](#-structure-du-projet)
12. [Gestion des erreurs](#-gestion-des-erreurs)
13. [Auteur](#-auteur)

---

## 🎯 À propos du projet

Ce projet est une **API REST complète** développée avec la stack MERN, implémentant une authentification sécurisée par **JSON Web Token (JWT)** pour gérer une plateforme d'apprentissage en ligne.

### Contexte

Réalisé dans le cadre de ma formation en **4ème année Data Science**, ce projet démontre la maîtrise de :
- L'architecture REST API
- L'authentification et sécurité JWT
- Les relations MongoDB complexes
- Les bonnes pratiques backend Node.js

### Objectifs pédagogiques

✅ Implémenter une authentification JWT complète  
✅ Gérer des relations MongoDB (1-to-1, 1-to-Many, Many-to-Many)  
✅ Créer des routes protégées et publiques  
✅ Structurer une API REST professionnelle  
✅ Appliquer les principes de sécurité backend

---

## ✨ Fonctionnalités principales

### 🔐 Authentification & Autorisation

- **Inscription utilisateur** avec hashage bcrypt
- **Connexion sécurisée** avec génération de JWT
- **Protection des routes** via middleware JWT
- **Expiration automatique** des tokens (7 jours)

### 👤 Gestion des Utilisateurs

- Création et consultation de profils
- Mise à jour des informations personnelles
- Liste des cours suivis par utilisateur
- Historique des avis donnés

### 📚 Système de Cours

- Création de cours par les instructeurs
- Consultation publique du catalogue
- Inscription aux cours (enrollment)
- Gestion des étudiants inscrits

### ⭐ Système de Reviews

- Avis et notes (1-5 étoiles)
- Commentaires détaillés
- Consultation publique des avis
- Lien utilisateur-cours-avis

---

## 🛠️ Architecture et technologies

### Stack technique

```
Backend Architecture
│
├── 🟢 Node.js v18+          → Runtime JavaScript
├── ⚡ Express.js 4.x        → Framework web
├── 🍃 MongoDB 6+            → Base de données NoSQL
├── 🔗 Mongoose 8.x          → ODM MongoDB
├── 🔒 JWT (jsonwebtoken)    → Authentification
├── 🛡️ bcryptjs             → Hashage passwords
└── 🌍 dotenv                → Variables d'environnement
```

### Design patterns utilisés

- **MVC Pattern** : Séparation Controller/Model/Routes
- **Middleware Pattern** : Protection JWT centralisée
- **Repository Pattern** : Accès données via Mongoose
- **Error Handling** : Gestion centralisée des erreurs

---

## 🚀 Installation rapide

### Prérequis

- **Node.js** ≥ 18.x
- **MongoDB** ≥ 6.x (local ou Atlas)
- **npm** ≥ 9.x
- **Postman** (pour tester l'API)

### Étapes d'installation

```bash
# 1. Cloner le repository
git clone https://github.com/imenbenothmen/mern-jwt-api.git
cd mern-jwt-api

# 2. Installer les dépendances
npm install

# 3. Créer le fichier de configuration
cp .env.example .env

# 4. Configurer les variables d'environnement
# Éditer le fichier .env avec vos paramètres

# 5. Démarrer MongoDB (si local)
mongod --dbpath /data/db

# 6. Lancer le serveur
npm run dev
```

✅ **Serveur actif sur** : `http://localhost:3000`

---

## ⚙️ Configuration

### Fichier `.env`

Créez un fichier `.env` à la racine avec ces variables :

```env
# Configuration Serveur
PORT=3000
NODE_ENV=development

# Configuration MongoDB
MONGODB_URI=mongodb://localhost:27017/mern-courses-db

# Configuration JWT
JWT_SECRET=votre_secret_jwt_super_securise_minimum_32_caracteres
JWT_EXPIRE=7d

# Configuration Email (optionnel)
EMAIL_USER=votre.email@gmail.com
EMAIL_PASS=votre_mot_de_passe_app
```

### Générer un JWT_SECRET sécurisé

```bash
# Méthode 1 : Via Node.js
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"

# Méthode 2 : Via terminal
openssl rand -base64 64
```

**Important** : Utilisez un secret d'au moins 32 caractères !

---

## 🔑 Compte de test

### Accès administrateur pré-configuré

Pour tester l'API immédiatement, utilisez ce compte :

```json
{
  "email": "imen@gmail.com",
  "password": "ibob"
}
```

**Informations du compte :**

| Paramètre | Valeur |
|-----------|--------|
| **Username** | imenbenothmenbanani |
| **Email** | imen@gmail.com |
| **Mot de passe** | ibob |
| **Rôle** | Administrateur |

### Connexion rapide

```bash
# Requête cURL
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "imen@gmail.com",
    "password": "ibob"
  }'
```

**Réponse attendue :**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "6940838843085ec2d8589999",
    "username": "imenbenothmenbanani",
    "email": "imen@gmail.com",
    "role": "admin"
  }
}
```

---

## 📚 Documentation API

### Routes publiques (sans authentification)

#### 📖 Catalogue de cours

```http
GET /api/courses
```

Liste tous les cours disponibles sur la plateforme.

**Exemple de réponse :**

```json
[
  {
    "_id": "6925c30ed0a9549bbf516cbf",
    "title": "React Hooks Avancés",
    "description": "Maîtrisez useState, useEffect et useReducer",
    "instructor": "Imen Ben Othmen",
    "students": ["user_id_1", "user_id_2"],
    "createdAt": "2024-12-15T10:00:00.000Z"
  }
]
```

---

#### 📄 Détails d'un cours

```http
GET /api/courses/:id
```

Récupère les informations complètes d'un cours spécifique.

---

#### ⭐ Avis sur un cours

```http
GET /api/courses/:courseId/reviews
```

Liste tous les avis et notes d'un cours.

**Exemple de réponse :**

```json
[
  {
    "_id": "review_id_123",
    "userId": {
      "username": "student_react",
      "email": "student@example.com"
    },
    "rating": 5,
    "comment": "Excellent cours ! Les explications sont claires.",
    "createdAt": "2024-12-14T15:30:00.000Z"
  }
]
```

---

#### 👥 Étudiants inscrits

```http
GET /api/courses/:courseId/students
```

Liste des étudiants ayant rejoint un cours.

---

### Routes protégées (JWT requis)

> **⚠️ Toutes ces routes nécessitent un token JWT valide**

#### 🔐 Authentification

##### Inscription

```http
POST /api/auth/register
Content-Type: application/json

{
  "username": "nouveau_user",
  "email": "user@example.com",
  "password": "SecurePass123",
  "confirmPassword": "SecurePass123"
}
```

**Réponse (201) :**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "6925c30ed0a9549bbf516cbf",
    "username": "nouveau_user",
    "email": "user@example.com"
  }
}
```

---

##### Connexion

```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "imen@gmail.com",
  "password": "ibob"
}
```

---

#### 👤 Gestion des utilisateurs

##### Liste de tous les utilisateurs 🔒

```http
GET /api/users
Authorization: Bearer <votre_token_jwt>
```

---

##### Détails d'un utilisateur 🔒

```http
GET /api/users/:id
Authorization: Bearer <votre_token_jwt>
```

---

##### Cours suivis par un utilisateur 🔒

```http
GET /api/users/:userId/courses
Authorization: Bearer <votre_token_jwt>
```

---

#### 📝 Gestion des profils

##### Créer un profil 🔒

```http
POST /api/users/:userId/profile
Authorization: Bearer <votre_token_jwt>
Content-Type: application/json

{
  "bio": "Étudiante en Data Science passionnée par le développement web",
  "website": "https://imen-portfolio.dev",
  "socialLinks": {
    "linkedin": "https://linkedin.com/in/imenbenothmenbanani",
    "github": "https://github.com/imenbenothmen"
  }
}
```

---

##### Consulter un profil 🔒

```http
GET /api/users/:userId/profile
Authorization: Bearer <votre_token_jwt>
```

---

##### Mettre à jour un profil 🔒

```http
PUT /api/users/:userId/profile
Authorization: Bearer <votre_token_jwt>
Content-Type: application/json

{
  "bio": "Senior Full Stack Developer | MERN Specialist",
  "website": "https://nouveausite.com"
}
```

---

#### 📚 Gestion des cours

##### Créer un cours 🔒

```http
POST /api/courses
Authorization: Bearer <votre_token_jwt>
Content-Type: application/json

{
  "title": "Node.js Avancé",
  "description": "Maîtrisez Express, MongoDB et les API REST",
  "instructor": "Imen Ben Othmen"
}
```

---

##### S'inscrire à un cours 🔒

```http
POST /api/courses/:courseId/enroll
Authorization: Bearer <votre_token_jwt>
Content-Type: application/json

{
  "userId": "6925c30ed0a9549bbf516cbf"
}
```

---

#### ⭐ Gestion des avis

##### Ajouter un avis 🔒

```http
POST /api/courses/:courseId/reviews
Authorization: Bearer <votre_token_jwt>
Content-Type: application/json

{
  "rating": 5,
  "comment": "Cours excellent ! Les exemples pratiques sont parfaits.",
  "userId": "6925c30ed0a9549bbf516cbf"
}
```

---

##### Mes avis 🔒

```http
GET /api/users/:userId/reviews
Authorization: Bearer <votre_token_jwt>
```

---

## 🗄️ Modèles de données

### Schema User

```javascript
{
  username: {
    type: String,
    required: true,
    unique: true,
    trim: true
  },
  email: {
    type: String,
    required: true,
    unique: true,
    lowercase: true
  },
  password: {
    type: String,
    required: true,
    minlength: 6
    // Hashé avec bcrypt (10 rounds)
  },
  courses: [{
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Course'
  }],
  createdAt: {
    type: Date,
    default: Date.now
  }
}
```

---

### Schema Profile (1-to-1 avec User)

```javascript
{
  user: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
    unique: true
  },
  bio: {
    type: String,
    maxlength: 500
  },
  website: {
    type: String,
    validate: {
      validator: function(v) {
        return /^https?:\/\/.+/.test(v);
      }
    }
  },
  socialLinks: {
    linkedin: String,
    github: String,
    twitter: String
  },
  createdAt: {
    type: Date,
    default: Date.now
  },
  updatedAt: {
    type: Date,
    default: Date.now
  }
}
```

---

### Schema Course

```javascript
{
  title: {
    type: String,
    required: true,
    trim: true
  },
  description: {
    type: String,
    required: true
  },
  instructor: {
    type: String,
    required: true
  },
  students: [{
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User'
  }],
  createdAt: {
    type: Date,
    default: Date.now
  }
}
```

---

### Schema Review (1-to-Many avec Course et User)

```javascript
{
  rating: {
    type: Number,
    required: true,
    min: 1,
    max: 5
  },
  comment: {
    type: String,
    required: true,
    maxlength: 1000
  },
  course: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Course',
    required: true
  },
  user: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true
  },
  createdAt: {
    type: Date,
    default: Date.now
  }
}
```

---

### Relations MongoDB

```
User (1) ←→ (1) Profile          [One-to-One]
User (N) ←→ (M) Course           [Many-to-Many]
Course (1) → (N) Review          [One-to-Many]
User (1) → (N) Review            [One-to-Many]
```

---

## 🛡️ Sécurité JWT

### Middleware de protection

**Fichier** : `middleware/authMiddleware.js`

```javascript
const jwt = require('jsonwebtoken');

const protect = (req, res, next) => {
  // 1. Vérifier la présence du header Authorization
  let token;
  
  if (
    req.headers.authorization &&
    req.headers.authorization.startsWith('Bearer')
  ) {
    // 2. Extraire le token
    token = req.headers.authorization.split(' ')[1];
    
    try {
      // 3. Vérifier et décoder le token
      const decoded = jwt.verify(token, process.env.JWT_SECRET);
      
      // 4. Ajouter l'ID utilisateur à la requête
      req.userId = decoded.userId;
      
      // 5. Passer au middleware suivant
      return next();
    } catch (error) {
      return res.status(401).json({ 
        message: 'Token invalide ou expiré' 
      });
    }
  }
  
  // Pas de token trouvé
  return res.status(401).json({ 
    message: 'Pas de token, accès refusé' 
  });
};

module.exports = { protect };
```

### Génération de token

```javascript
const jwt = require('jsonwebtoken');

const generateToken = (userId) => {
  return jwt.sign(
    { userId },                    // Payload
    process.env.JWT_SECRET,        // Secret
    { expiresIn: '7d' }           // Options (expire dans 7 jours)
  );
};
```

### Hashage des mots de passe

```javascript
const bcrypt = require('bcryptjs');

// Lors de l'inscription
const hashedPassword = await bcrypt.hash(password, 10);

// Lors de la connexion
const isMatch = await bcrypt.compare(password, user.password);
```

---

## 🧪 Tests avec Postman

### Configuration de l'environnement

**Créer un environnement** : `MERN API - Development`

**Variables** :

| Variable | Initial Value | Current Value |
|----------|---------------|---------------|
| `base_url` | `http://localhost:3000/api` | `http://localhost:3000/api` |
| `jwt_token` | *(vide)* | *(auto-rempli)* |
| `user_id` | *(vide)* | *(auto-rempli)* |
| `course_id` | *(vide)* | *(auto-rempli)* |

---

### Scripts automatiques Postman

#### Script Login/Register (Tests tab)

```javascript
// Sauvegarder automatiquement le token
if (pm.response.code === 200 || pm.response.code === 201) {
    const jsonData = pm.response.json();
    pm.environment.set("jwt_token", jsonData.token);
    pm.environment.set("user_id", jsonData.user.id);
    console.log("✅ Token et User ID sauvegardés");
}
```

---

#### Script Create Course (Tests tab)

```javascript
// Sauvegarder l'ID du cours créé
if (pm.response.code === 201) {
    const course = pm.response.json();
    pm.environment.set("course_id", course._id);
    console.log("✅ Course ID sauvegardé : " + course._id);
}
```

---

### Scénario de test complet

```javascript
// 1. S'inscrire
POST {{base_url}}/auth/register
Body: {
  "username": "test_user",
  "email": "test@example.com",
  "password": "Test123",
  "confirmPassword": "Test123"
}
// → Token sauvegardé automatiquement

// 2. Se connecter (optionnel si déjà inscrit)
POST {{base_url}}/auth/login
Body: {
  "email": "imen@gmail.com",
  "password": "ibob"
}

// 3. Créer un profil
POST {{base_url}}/users/{{user_id}}/profile
Authorization: Bearer {{jwt_token}}
Body: {
  "bio": "Développeuse Full Stack",
  "website": "https://monsite.dev"
}

// 4. Créer un cours
POST {{base_url}}/courses
Authorization: Bearer {{jwt_token}}
Body: {
  "title": "MongoDB Essentials",
  "description": "Apprenez MongoDB",
  "instructor": "Imen Ben Othmen"
}
// → course_id sauvegardé

// 5. S'inscrire au cours
POST {{base_url}}/courses/{{course_id}}/enroll
Authorization: Bearer {{jwt_token}}
Body: {
  "userId": "{{user_id}}"
}

// 6. Ajouter un avis
POST {{base_url}}/courses/{{course_id}}/reviews
Authorization: Bearer {{jwt_token}}
Body: {
  "rating": 5,
  "comment": "Cours excellent !",
  "userId": "{{user_id}}"
}

// 7. Consulter mes cours
GET {{base_url}}/users/{{user_id}}/courses
Authorization: Bearer {{jwt_token}}

// 8. Consulter mes avis
GET {{base_url}}/users/{{user_id}}/reviews
Authorization: Bearer {{jwt_token}}
```

---

## 📁 Structure du projet

```
mern-jwt-api/
│
├── 📂 config/
│   └── db.js                    # Configuration MongoDB
│
├── 📂 controllers/
│   ├── authController.js        # Register, Login
│   ├── userController.js        # CRUD utilisateurs
│   ├── profileController.js     # CRUD profils
│   ├── courseController.js      # CRUD cours
│   └── reviewController.js      # CRUD avis
│
├── 📂 middleware/
│   └── authMiddleware.js        # Protection JWT
│
├── 📂 models/
│   ├── User.js                  # Schema utilisateur
│   ├── Profile.js               # Schema profil
│   ├── Course.js                # Schema cours
│   └── Review.js                # Schema avis
│
├── 📂 routes/
│   ├── authRoutes.js            # Routes authentification
│   ├── userRoutes.js            # Routes utilisateurs
│   └── courseRoutes.js          # Routes cours
│
├── 📂 utils/
│   └── generateToken.js         # Utilitaire JWT
│
├── 📂 img/                      # Captures d'écran
│   ├── register-route.png
│   ├── login-route.png
│   ├── get-users.png
│   └── get-user.png
│
├── .env                         # Variables d'environnement
├── .env.example                 # Template .env
├── .gitignore
├── package.json
├── server.js                    # Point d'entrée
└── README.md                    # Documentation
```

---

## ⚠️ Gestion des erreurs

### Codes de statut HTTP

| Code | Signification | Usage |
|------|--------------|-------|
| **200** | OK | Requête réussie (GET, PUT) |
| **201** | Created | Ressource créée (POST) |
| **400** | Bad Request | Données invalides ou manquantes |
| **401** | Unauthorized | Token manquant, invalide ou expiré |
| **403** | Forbidden | Accès interdit (permissions) |
| **404** | Not Found | Ressource non trouvée |
| **409** | Conflict | Conflit (email déjà utilisé) |
| **500** | Internal Server Error | Erreur serveur |

---

### Erreurs courantes et solutions

#### ❌ 401 Unauthorized - "Pas de token, accès refusé"

**Problème** : Header Authorization manquant

**Solution** :
```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

---

#### ❌ 401 Unauthorized - "Token invalide ou expiré"

**Causes possibles** :
- Token expiré (> 7 jours)
- Token malformé
- JWT_SECRET incorrect

**Solution** : Se reconnecter pour obtenir un nouveau token

```bash
POST /api/auth/login
```

---

#### ❌ 409 Conflict - "Email déjà utilisé"

**Problème** : L'email existe déjà dans la base

**Solution** : Utiliser un autre email ou se connecter

---

#### ❌ 404 Not Found - "Cours non trouvé"

**Problème** : ID de cours invalide ou inexistant

**Solution** : Vérifier l'ID via `GET /api/courses`

---

#### ❌ 500 Internal Server Error

**Causes possibles** :
- MongoDB non démarré
- Erreur de connexion DB
- Variables d'environnement manquantes

**Solution** : Vérifier les logs serveur et le fichier `.env`

---

## 📊 Statistiques du projet

```
Total Endpoints    : 15+
Routes protégées   : 11
Routes publiques   : 4
Modèles MongoDB    : 4
Middleware         : 1
Technologies       : 7
```

---

## 👩‍💻 Auteur

**Imen BEN OTHMEN BANANI**

- 🎓 Étudiante en 4ème année **Data Science**
- 💻 Spécialisation : **MERN Stack Development**
- 📧 Email : **imen@gmail.com**
- 🌐 Portfolio : [À venir]
- 💼 LinkedIn : [À venir]
- 🐙 GitHub : [@imenbenothmen](https://github.com/imenbenothmen)

---

## 📅 Informations du projet

- **Projet** : TP5 - Authentification JWT & API REST
- **Formation** : MERN Stack - Poly Project
- **Date de création** : Décembre 2024
- **Dernière mise à jour** : 15 Décembre 2024
- **Version** : 1.0.0

---

## 📝 Licence

Ce projet est un travail académique réalisé dans le cadre de ma formation en Data Science.

**Usage** : Éducatif et Portfolio uniquement

---

## 📚 Ressources et documentation

### Documentation officielle

- 📘 [Node.js Documentation](https://nodejs.org/docs/)
- 📗 [Express.js Guide](https://expressjs.com/)
- 📕 [Mongoose Documentation](https://mongoosejs.com/docs/)
- 📙 [JWT.io](https://jwt.io/)
- 📓 [bcrypt Documentation](https://www.npmjs.com/package/bcryptjs)

### Tutoriels utilisés

- [Building RESTful APIs with Node.js and Express](https://www.youtube.com/watch?v=fgTGADljAeg)
- [JWT Authentication Tutorial](https://www.youtube.com/watch?v=mbsmsi7l3r4)
- [MongoDB Relationships Guide](https://mongoosejs.com/docs/populate.html)

---

## 🙏 Remerciements

Merci à mes formateurs et à la communauté open-source pour les ressources partagées.

---

<div align="center">

### ⭐ Si ce projet vous aide, n'hésitez pas à lui donner une étoile ! ⭐

**Made with ❤️ by Imen BEN OTHMEN BANANI**

*"Code, Learn, Grow."*

</div>