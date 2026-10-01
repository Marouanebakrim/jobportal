
# 💼 JobPortal – Plateforme Web de Recrutement et de Recherche d'Emploi

<p align="center">
  <img src="https://img.shields.io/badge/.NET%2010-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt=".NET 10" />
  <img src="https://img.shields.io/badge/React%2019-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React 19" />
  <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/SQL%20Server-CC292B?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" alt="SQL Server" />
  <img src="https://img.shields.io/badge/Bootstrap%205-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white" alt="Bootstrap 5" />
  <img src="https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens" alt="JWT" />
</p>

Application Web Full Stack moderne basée sur une architecture client-serveur découplée (**ASP.NET Core .NET 10 & React 19**) pour la centralisation, la publication et la gestion automatisée des offres d'emploi et des candidatures.

---

## 📚 Sommaire
- [🚀 À propos du projet](#-à-propos-du-projet)
- [🧱 Stack technique](#-stack-technique)
- [📁 Structure des dossiers](#-structure-des-dossiers)
- [🧩 Description des responsabilités](#-description-des-responsabilités)
- [👥 Gestion des utilisateurs & profils](#-gestion-des-utilisateurs--profils)
- [💼 Gestion des offres d'emploi](#-gestion-des-offres-demploi)
- [📝 Cycle de vie et traitement des candidatures](#-cycle-de-vie-et-traitement-des-candidatures)
- [🌐 Services et fonctionnalités avancées](#-services-et-fonctionnalités-avancées)
- [🔐 Authentification et sécurité](#-authentification-et-sécurité)
- [⚙️ Paramétrages & Auto-Seeding](#️-paramétrages--auto-seeding)
- [🧑‍💻 Auteur](#-auteur)
- [📂 Clonage et exécution](#-clonage-et-exécution)

---

## 🚀 À propos du projet

**JobPortal** est un système complet de gestion de recrutement (Job Board) conçu pour automatiser les interactions entre chercheurs d'emploi, entreprises recruteuses et administrateurs de la plateforme.

### 🌟 Fonctionnalités principales :
- 👤 **Espaces multi-rôles sécurisés** : Candidats, Recruteurs et Administrateurs avec interfaces dédiées et droits d'accès distincts (**RBAC**).
- 🔍 **Moteur de recherche multicritère** : Filtrage dynamique par mot-clé, ville/pays, type de contrat et fourchette de rémunération.
- 📄 **Gestion documentaire (CV)** : Téléversement sécurisé de CVs (PDF/Word), génération de liens uniques et consultation directe.
- 📬 **Workflow de candidature & suivi en direct** : Postulation en un clic, historique des demandes et mise à jour en temps réel des statuts (*En attente, Accepté, Rejeté*).
- 📧 **Système de notification par email** : Accusé de réception automatique et notification instantanée lors de la décision du recruteur.
- 📊 **Tableau de bord décisionnel (Analytics)** : Statistiques globales en temps réel, indicateurs clés (KPIs) et graphiques interactifs pour l'administrateur.

---

## 🧱 Stack technique

| Composant | Technologie | Description |
| :--- | :--- | :--- |
| **Backend Framework** | **ASP.NET Core Web API (.NET 10)** | API RESTful haute performance, découplée et typée en C# |
| **ORM & Persistance** | **Entity Framework Core 10** | Mapping objet-relationnel (ORM), requêtes LINQ et migrations automatiques |
| **Base de données** | **Microsoft SQL Server** | Stockage relationnel transactionnel avec contraintes d'intégrité |
| **Sécurité & Hash** | **BCrypt.Net-Next** | Hachage sécurisé et salage des mots de passe |
| **Authentification** | **JWT Bearer (JSON Web Tokens)** | Gestion de session sans état (stateless) basée sur les claims et rôles |
| **Frontend Framework** | **React 19** | Interface utilisateur réactive basée sur les composants et Hooks |
| **Outil de Build** | **Vite 8** | Environnement de développement et bundler ultra-rapide avec HMR |
| **Navigation & Routage** | **React Router DOM v7** | Navigation Single Page Application (SPA) et routes protégées par rôle |
| **Design & UI** | **Bootstrap 5.3 + CSS3 Custom** | Design moderne, grille fluide et composants responsives (Mobile/Desktop) |
| **Animations & Effets** | **Framer Motion** | Micro-interactions et transitions de pages fluides |
| **Data Visualization** | **Recharts** | Graphiques dynamiques (Camemberts, Barres) pour le tableau de bord Admin |
| **Communication HTTP** | **Axios** | Client HTTP avec intercepteurs pour l'injection automatique du Bearer Token |

---

## 📁 Structure des dossiers

```text
JobPortal/
├── backend/
│   └── JobPortal.API/                 # 🖥️ API Backend (ASP.NET Core .NET 10)
│       ├── Controllers/               # Contrôleurs REST (Auth, Jobs, Applications, Profile, Admin)
│       ├── DTOs/                      # Objets de transfert de données (Request / Response)
│       ├── Data/                      # Contexte de base de données (AppDbContext) & DataSeeder
│       ├── Middleware/                # Gestion centralisée des exceptions (ExceptionMiddleware)
│       ├── Migrations/                # Historique des migrations Entity Framework Core
│       ├── Models/                    # Entités de domaine (User, Job, Application, Profiles, Enums)
│       ├── Services/                  # Couche métier et interfaces (IAuth, IJob, IApplication, etc.)
│       ├── wwwroot/uploads/cvs/       # Répertoire de stockage physique des CVs téléversés
│       ├── appsettings.json           # Configurations de la base SQL et des clés secrètes JWT
│       └── Program.cs                 # Configuration de l'application, DI, JWT, CORS & Pipeline
│
└── frontend/                          # 🎨 Application Frontend (React 19 + Vite)
    ├── src/
    │   ├── api/                       # Instance Axios & modules d'appels API (auth, jobs, etc.)
    │   ├── components/                # Composants partagés (Navbar, Footer, JobCard, Spinner)
    │   ├── context/                   # Contexte d'authentification global (AuthContext)
    │   ├── pages/
    │   │   ├── public/                # IHM publique (HomePage, JobListPage, JobDetailPage, Login, Register)
    │   │   ├── candidate/             # IHM Candidat (CandidateProfilePage, MyApplicationsPage)
    │   │   ├── recruiter/             # IHM Recruteur (ManageJobsPage, CreateJobPage, EditJobPage, ViewApplicationsPage)
    │   │   └── admin/                 # IHM Administrateur (StatsPage, ManageUsersPage, AdminJobsPage)
    │   ├── routes/                    # Protection des routes selon les rôles (ProtectedRoute)
    │   ├── App.jsx                    # Arbre des routes de l'application
    │   └── main.jsx                   # Point d'entrée de l'application React
    ├── package.json                   # Dépendances du projet Frontend
    └── vite.config.js                 # Configuration du serveur de développement Vite
```

---

## 🧩 Description des responsabilités

| Couche | Rôle & Responsabilité |
| :--- | :--- |
| **Frontend UI (React 19)** | Gère l'expérience utilisateur, valide les formulaires côté client, maintient l'état d'authentification et communique via requêtes HTTP asynchrones. |
| **Controllers (API REST)** | Réceptionne les requêtes HTTP, valide les modèles d'entrée (DTOs), extrait l'identité de l'utilisateur connecté via les Claims JWT et renvoie les codes de statut HTTP standardisés. |
| **Business Services (BLL)** | Contient l'ensemble des règles métier (éligibilité des candidatures, règles d'unicité, gestion des statuts, calculs de KPIs, envoi d'emails). |
| **Entity Framework Core (DAL)** | Gère la communication avec SQL Server, traduit les requêtes LINQ en SQL optimisé et assure la gestion des transactions. |
| **SQL Server (Database)** | Stocke de manière sécurisée et intègre les données (utilisateurs, profils, offres, candidatures) avec contraintes de clés étrangères et index. |

---

## 👥 Gestion des utilisateurs & profils

### 👤 Module Candidat (Candidate Profile)
- **Fiche profil détaillée** : Coordonnées téléphoniques, niveau de formation / diplômes et liste des compétences clés.
- **Gestionnaire de CV** : Téléversement de CV au format PDF/Word avec renommage automatique unique (GUID) et mise à disposition sécurisée.

### 🏢 Module Recruteur (Recruiter Profile)
- **Fiche entreprise** : Nom de l'entreprise, description de l'activité et lien vers le site web officiel.
- **Rattachement des offres** : Chaque annonce d'emploi est automatiquement liée au profil de l'entreprise émettrice.

### 🛡️ Module Administrateur (Admin)
- **Supervision des comptes** : Consultation de la liste globale des utilisateurs (Candidats et Recruteurs).
- **Modération & Suppression** : Possibilité de révoquer un utilisateur et supprimer en cascade les données associées.

---

## 💼 Gestion des offres d'emploi

Toute offre d'emploi suit un cycle de gestion complet administré par le recruteur :

- 📝 **Création d'offre** : Saisie du titre, type de contrat (*FullTime, PartTime, Internship, Remote*), localisation, niveau de salaire, description et prérequis.
- 🔄 **Mise à jour & Suspension** : Modification des critères ou passage en statut inactif pour masquer temporairement l'annonce du portail public.
- 🗑️ **Suppression sécurisée** : Retrait définitif de l'offre (autorisé uniquement pour le recruteur propriétaire ou l'administrateur).
- 📊 **Compteur de candidatures** : Visualisation instantanée du nombre de candidats ayant postulé à chaque offre.

---

## 📝 Cycle de vie et traitement des candidatures

L'application intègre un flux séquentiel pour chaque postulation :

```text
[ 🌐 Candidat consulte une offre active ]
                  │
                  ▼
[ 📝 Soumission de la candidature ] ────(Vérification doublon)────► [ 🚫 Candidature déjà existante ]
                  │
                  ▼ (Succès)
[ ⏳ Statut : Pending (En attente) ] ──► [ 📧 Email de confirmation envoyé au candidat ]
                  │
                  ▼
[ 🏢 Examen par le Recruteur (Lecture lettre de motivation + Téléchargement du CV) ]
                  │
                  ├───────────────────────────────┐
                  ▼                               ▼
[ ✅ Décision : Accepté ]            [ ❌ Décision : Rejeté ]
                  │                               │
                  ▼                               ▼
[ 📧 Notification email d'acceptation ]   [ 📧 Notification email de refus ]
```

- **Contrôle d'unicité** : Impossibilité pour un même candidat de postuler plusieurs fois à la même annonce.
- **Traçabilité des statuts** : Historisation de la date d'envoi et du statut de la demande.

---

## 🌐 Services et fonctionnalités avancées

### 📈 1. Tableau de bord décisionnel (Admin Dashboard)
- **Métriques en temps réel** : Nombre total d'utilisateurs, répartition des rôles (Candidats vs Recruteurs), total des offres publiées vs offres actives.
- **Graphiques interactifs (Recharts)** : Visualisation du taux de conversion et du ratio des candidatures (*Pending, Accepted, Rejected*).

### 📧 2. Service de notification par email (`IEmailService`)
- Notification automatique lors du dépôt d'une candidature.
- Notification en direct au candidat lors du changement de décision par le recruteur.

### 📁 3. Gestionnaire de fichiers statiques
- Stockage organisé dans `/wwwroot/uploads/cvs/`.
- Accès public sécurisé via URL relative pour la consultation et le téléchargement des documents.

---

## 🔐 Authentification et sécurité

- 🔑 **Authentification sans état (Stateless JWT)** : Émission d'un token sécurisé contenant l'identifiant, l'email et le rôle (`UserRole`) lors de la connexion.
- 🛡️ **Contrôle d'accès basé sur les rôles (RBAC)** :
  - **Backend** : Protection stricte des endpoints via l'attribut `[Authorize(Roles = "Admin, Recruiter, Candidate")]`.
  - **Frontend** : Protection des écrans via le composant `<ProtectedRoute allowedRoles={[...]} />`.
- 🔒 **Chiffrement des mots de passe** : Hachage avec **BCrypt** et salage automatique pour garantir la confidentialité des identifiants.
- 🌐 **Politique CORS maîtrisée** : Autorisation sélective des origines pour les requêtes provenant du client React.

---

## ⚙️ Paramétrages & Auto-Seeding

L'application intègre un **mécanisme de génération automatique de données de démonstration (`DataSeeder`)** qui s'exécute dès le premier lancement si la base est vierge :

- Création automatique du compte Administrateur par défaut.
- Génération de **20 profils Recruteurs** avec entreprises associées.
- Génération de **20 profils Candidats** avec compétences et diplômes.
- Publication de **20 offres d'emploi** variées.
- Création de **40 candidatures** réparties avec statuts diversifiés.

---

## 🧑‍💻 Auteur

👨‍💻 **Marouane BAKRIM**  
📧 Email : [maroaunebakrim538@gmail.com](mailto:maroaunebakrim538@gmail.com)  

---

## 📂 Clonage et exécution

### 1. Cloner le dépôt
```bash
git clone https://github.com/Marouanebakrim/JobPortal.git
cd JobPortal
```

### 2. Démarrer le Backend (.NET 10 API)
```bash
cd backend/JobPortal.API

# Vérifier la chaîne de connexion dans appsettings.json si nécessaire
dotnet run
```
> L'API s'exécute sur `http://localhost:5069` et génère automatiquement la base de données SQL Server avec les données de test.

### 3. Démarrer le Frontend (React 19 + Vite)
```bash
# Dans un nouveau terminal :
cd frontend

# Installer les packages
npm install

# Lancer l'application web
npm run dev
```
> L'application est accessible sur `http://localhost:5173`.

---

### 🔑 Identifiants de test pré-configurés

| Espace | Email | Mot de passe |
| :--- | :--- | :--- |
| **🛡️ Administrateur** | `admin@jobportal.com` | `Admin@123` |
| **🏢 Recruteur** | `recruiter1@example.com` | `Recruiter@123` |
| **👤 Candidat** | `candidate1@example.com` | `Candidate@123` |
