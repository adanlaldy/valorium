# Valorium - API Auctions & Users

Ce projet est une plateforme d’enchères en ligne composée de deux API :  
- **api-auctions** : gestion des enchères, fichiers, images, tags, états, etc.
- **api-users** : gestion des utilisateurs.

---

## Sommaire

- [Fonctionnalités](#fonctionnalités)
- [Prérequis](#prérequis)
- [Installation](#installation)
- [Lancement des serveurs](#lancement-des-serveurs)
- [Structure du projet](#structure-du-projet)
- [API principales](#api-principales)
- [Exemples de requêtes](#exemples-de-requêtes)
- [Développement & outils](#développement--outils)

---

## Fonctionnalités

- Création, modification, suppression et consultation d’enchères
- Gestion des fichiers associés aux enchères
- Ajout et gestion de photos pour chaque enchère
- Système de tags pour catégoriser les enchères
- États d’enchères (Open, Pending, Close, Canceled, Sold)
- API RESTful pour chaque ressource
- Gestion des utilisateurs (dans `api-users`)

---

## Prérequis

- Node.js (v18+ recommandé)
- npm ou yarn
- Une base de données compatible Prisma (ex : PostgreSQL, MySQL, SQLite)
- [Prisma CLI](https://www.prisma.io/docs/reference/api-reference/command-reference) (pour la gestion du schéma)

---

## Installation

1. **Clone le dépôt**  
   ```sh
   git clone <url-du-repo>
   cd valorium
   ```

2. **Installe les dépendances pour chaque API**  
   ```sh
   cd api-auctions
   npm install
   cd ../api-users
   npm install
   ```

3. **Configure les variables d’environnement**  
   - Copie le fichier `.env.example` en `.env` dans chaque dossier d’API et adapte la connexion à ta base de données.

4. **Mets à jour la base de données**  
   ```sh
   cd api-auctions
   npx prisma migrate dev --name init
   npx prisma generate
   ```

---

## Lancement des serveurs

Dans deux terminaux :

```sh
# API Auctions
cd api-auctions
node server.js
```

```sh

# API Users
cd ../api-users
node server.js
```

- **API Auctions** : http://localhost:3000
- **API Users** : http://localhost:3001

---

## Structure du projet

```
valorium/
│
├── api-auctions/
│   ├── controllers/
│   ├── routers/
│   ├── services/
│   ├── generated/prisma/
│   ├── server.js
│   └── app.js
│
├── api-users/
│   ├── controllers/
│   ├── routers/
│   ├── services/
│   ├── server.js
│   └── app.js
│
└── README.md
```

---

## API principales

### Enchères (`api-auctions`)
- `GET /auctions` : liste toutes les enchères
- `POST /auctions` : crée une nouvelle enchère
- `GET /auctions/:id` : détail d’une enchère
- `PUT /auctions/:id` : modifie une enchère
- `DELETE /auctions/:id` : supprime une enchère

### Fichiers
- `GET /files` : liste tous les fichiers
- `POST /files` : ajoute un fichier
- `GET /files/:id` : récupère un fichier
- `DELETE /files/:id` : supprime un fichier

### Images
- `GET /pictures` : liste toutes les images
- `POST /pictures` : ajoute une image à une enchère

### Tags
- `GET /tags` : liste tous les tags
- `POST /tags` : crée un tag

### États
- `GET /states` : liste tous les états possibles

### Utilisateurs (`api-users`)
- `GET /users` : liste tous les utilisateurs
- `POST /users` : crée un nouvel utilisateur
- `GET /users/:id` : détail d’un utilisateur
- `PUT /users/:id` : modifie un utilisateur
- `DELETE /users/:id` : supprime un utilisateur

#### Authentification
- `POST /login` : connexion d’un utilisateur
- `POST /register` : inscription d’un nouvel utilisateur

---

## Exemples de requêtes

### Créer une enchère

```http
POST /auctions
Content-Type: application/json

{
  "title": "Vélo de course",
  "description": "Vélo en bon état",
  "initialPrice": 100,
  "startBidDate": "2025-06-01T10:00:00Z",
  "endBidDate": "2025-06-07T10:00:00Z",
  "sellerId": 1
}
```

### Récupérer tous les états

```http
GET /states
```

---

## Développement & outils

- **Prisma** : ORM pour la gestion de la base de données
- **Express** : framework Node.js pour l’API
- **Nodemon** : rechargement automatique en développement
- **Prisma Studio** : interface graphique pour explorer la base
  ```sh
  npx prisma studio
  ```

---

## Auteurs

- Projet Valorium – Ynov B3
