# 💼 JobPortal — Plateforme de Recrutement & Recherche d'Emploi
<p align="center">
  <img src="https://img.shields.io/badge/.NET%2010-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt=".NET 10" />
  <img src="https://img.shields.io/badge/React%2019-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React 19" />
  <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/SQL%20Server-CC292B?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" alt="SQL Server" />
  <img src="https://img.shields.io/badge/Bootstrap%205-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white" alt="Bootstrap 5" />
  <img src="https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens" alt="JWT" />
</p>
---
## 📖 À propos du projet
**JobPortal** est une application web moderne (Full Stack) de mise en relation entre **Candidats**, **Recruteurs** et **Administrateurs**. Elle offre une solution clé en main pour la gestion du cycle de recrutement : publication d'annonces, recherche multicritère avancée, soumission et suivi des candidatures en temps réel avec upload de CV, ainsi qu'un tableau de bord analytique.
---
## ✨ Fonctionnalités Principales
### 👤 Espace Candidat
- 🔍 **Recherche et filtres avancés** : recherche par mot-clé, localisation, type de contrat (*FullTime, PartTime, Remote, Internship*) et salaire minimum.
- 📝 **Postulation simplifiée** : soumission de candidature avec lettre de motivation et CV (PDF/Word).
- 📊 **Suivi des candidatures** : tableau de bord personnel affichant l'état des candidatures en temps réel (*En attente*, *Acceptée*, *Refusée*).
- ⚙️ **Gestion du profil** : mise à jour des compétences, expériences, informations de contact et CV.
### 🏢 Espace Recruteur
- 📢 **Gestion des offres** : création, modification, désactivation et suppression des offres d'emploi.
- 👥 **Gestion des candidats** : consultation des profils des postulants, lecture des lettres de motivation et téléchargement direct des CVs.
- ⚡ **Prise de décision** : acceptation ou rejet des candidatures avec envoi de notification par email.
### 🛡️ Espace Administrateur
- 📈 **Tableau de bord statistique (KPIs)** : graphiques interactifs (Recharts) sur les utilisateurs, offres actives et taux d'acceptation.
- 👥 **Gestion des utilisateurs** : administration et modération des comptes (Candidats et Recruteurs).
- 🛡️ **Modération du contenu** : supervision et suppression des annonces non conformes.
---
## 🛠️ Stack Technologique
### Backend
- **Framework** : ASP.NET Core Web API (.NET 10)
- **ORM** : Entity Framework Core 10 (Code-First)
- **Base de données** : Microsoft SQL Server
- **Sécurité** : Hachage des mots de passe avec `BCrypt.Net-Next` & Authentification sans état `JWT Bearer`
- **Architecture** : Clean Separation (Controllers, Services Métier, DTOs, Data Seeding, Middleware d'exceptions)
### Frontend
- **Framework** : React 19 (Hooks, Context API)
- **Build Tool** : Vite 8
- **Routage & Sécurité** : React Router DOM v7 avec `ProtectedRoute` (RBAC)
- **Client HTTP** : Axios (Intercepteurs automatiques de token JWT)
- **Design & UI** : Bootstrap 5.3, React Icons, Framer Motion (animations fluides)
- **Visualisation de données** : Recharts
---
## 🏛️ Architecture & Modèle de Données
```text
JobPortal/
├── backend/JobPortal.API/     # API REST ASP.NET Core (.NET 10)
│   ├── Controllers/           # Points d'entrée REST (Auth, Jobs, Applications, Profile, Admin)
│   ├── Services/              # Logique métier et interfaces
│   ├── Models/                # Entités EF Core (User, Job, Application, Profiles)
│   ├── Data/                  # DbContext, Migrations et Seeder automatique
│   └── Middleware/            # Gestion globale des erreurs
└── frontend/                  # Single Page Application React 19
    ├── src/pages/             # Vues organisées par rôles (public, candidate, recruiter, admin)
    ├── src/components/        # Composants réutilisables (Navbar, Footer, JobCard, etc.)
    ├── src/context/           # AuthContext (gestion globale de l'état JWT)
    └── src/api/               # Configuration Axios et appels API
🚀 Installation et Démarrage
Prérequis
.NET 10 SDK
Node.js (v18+)
SQL Server ou SQL Server Express / LocalDB
1️⃣ Lancement du Backend (API)
Rendez-vous dans le dossier backend :

bash
cd backend/JobPortal.API
Configurez votre chaîne de connexion dans appsettings.json :

json
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=JobPortalDb;Trusted_Connection=True;TrustServerCertificate=True;"
}
Exécutez l'API (les migrations et les données de démo s'appliquent automatiquement au premier lancement) :

bash
dotnet run
L'API démarre par défaut sur http://localhost:5069.

2️⃣ Lancement du Frontend (React)
Rendez-vous dans le dossier frontend :

bash
cd frontend
Installez les dépendances :

bash
npm install
Lancez le serveur de développement :

bash
npm run dev
L'application est accessible sur http://localhost:5173.

🔑 Comptes de Test Pré-configurés (Demo Data)
Le projet intègre un système d'auto-seeding qui génère automatiquement les comptes suivants :

Rôle	Email	Mot de passe
Administrateur	admin@jobportal.com	Admin@123
Recruteur	recruiter1@example.com	Recruiter@123
Candidat	candidate1@example.com	Candidate@123
