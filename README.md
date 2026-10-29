<div align="center">

# UEMF University Management

Plateforme web de gestion universitaire pour l'Université Euro-Méditerranéenne de Fès.<br />
Étudiants, enseignants, cours, notes, emplois du temps, examens, frais et annonces, avec un espace dédié à chaque rôle.

<br />

![React](https://img.shields.io/badge/React-19-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Express](https://img.shields.io/badge/Express-5-000000?style=flat-square&logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black)
![Telegram](https://img.shields.io/badge/Telegram_Bot-26A5E4?style=flat-square&logo=telegram&logoColor=white)

[**Démo en ligne**](http://5.189.141.148:3000/) &nbsp;·&nbsp; [Captures d'écran](#captures-décran) &nbsp;·&nbsp; [Installation](#installation-locale) &nbsp;·&nbsp; [Architecture](#architecture)

<br />

<img src="docs/screenshots/cover.png" alt="Tableau de bord administrateur" width="900" />

</div>

## Aperçu

Le système centralise la gestion académique et administrative d'une université dans une seule application web. Chaque utilisateur se connecte avec son rôle (administrateur, administration, enseignant ou étudiant) et ne voit que les pages et les données qui le concernent. Un bot Telegram, branché sur la même API, permet aux étudiants de consulter leur emploi du temps, leurs absences et leur progression sans ouvrir le site.

## Fonctionnalités

| Module | Admin | Administration | Enseignant | Étudiant |
|---|:---:|:---:|:---:|:---:|
| Tableau de bord avec statistiques et graphiques | ✅ | ✅ | ✅ personnel | ✅ personnel |
| Étudiants (liste, fiche détaillée, recherche) | ✅ | ✅ | ✅ ses étudiants | |
| Cours et inscriptions | ✅ | ✅ | ✅ ses cours | ✅ ses cours |
| Enseignants et départements | ✅ | ✅ | ✅ | |
| Notes | ✅ | ✅ | ✅ saisie, ses cours | ✅ ses notes |
| Emplois du temps et examens | ✅ | ✅ | ✅ | ✅ |
| Frais de scolarité | ✅ | ✅ | | ✅ ses frais |
| Annonces | ✅ | ✅ | ✅ | ✅ |

**Points techniques**

- **Contrôle d'accès par rôle** appliqué deux fois : par un middleware `requireRole` sur chaque route de l'API, et par des routes protégées dans l'interface.
- **Filtrage des données selon l'utilisateur** : un enseignant ne voit que les étudiants inscrits à ses cours, un étudiant uniquement ses propres cours, notes et frais (`scopeFilter.ts`).
- **Authentification JWT**, mots de passe hachés avec bcrypt.
- **API contract-first** : une spécification OpenAPI 3.0 génère les hooks React Query et les schémas Zod (Orval), partagés entre le client et le serveur.
- **Bot Telegram via OpenClaw** : liaison du compte par jeton à usage unique, puis commandes `/today`, `/week`, `/absence` et `/progress`.

## Captures d'écran

<sub>Captures réalisées sur une instance locale remplie avec les données de démonstration des scripts de seed.</sub>

### Connexion

<img src="docs/screenshots/login.png" alt="Page de connexion" width="100%" />

### Administration

<table>
  <tr>
    <td width="50%"><img src="docs/screenshots/students.png" alt="Liste des étudiants" /><p align="center"><b>Étudiants</b></p></td>
    <td width="50%"><img src="docs/screenshots/student-detail.png" alt="Fiche étudiant" /><p align="center"><b>Fiche étudiant</b></p></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/courses.png" alt="Cours" /><p align="center"><b>Cours</b></p></td>
    <td><img src="docs/screenshots/faculty.png" alt="Enseignants" /><p align="center"><b>Enseignants</b></p></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/departments.png" alt="Départements" /><p align="center"><b>Départements</b></p></td>
    <td><img src="docs/screenshots/enrollments.png" alt="Inscriptions" /><p align="center"><b>Inscriptions</b></p></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/grades.png" alt="Notes" /><p align="center"><b>Notes</b></p></td>
    <td><img src="docs/screenshots/schedules.png" alt="Emplois du temps" /><p align="center"><b>Emplois du temps</b></p></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/exams.png" alt="Examens" /><p align="center"><b>Examens</b></p></td>
    <td><img src="docs/screenshots/fees.png" alt="Frais de scolarité" /><p align="center"><b>Frais de scolarité</b></p></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/announcements.png" alt="Annonces" /><p align="center"><b>Annonces</b></p></td>
    <td><img src="docs/screenshots/admin-dashboard.png" alt="Tableau de bord" /><p align="center"><b>Tableau de bord</b></p></td>
  </tr>
</table>

### Espaces enseignant et étudiant

<table>
  <tr>
    <td width="50%"><img src="docs/screenshots/teacher-dashboard.png" alt="Tableau de bord enseignant" /><p align="center"><b>Tableau de bord enseignant</b></p></td>
    <td width="50%"><img src="docs/screenshots/student-dashboard.png" alt="Tableau de bord étudiant" /><p align="center"><b>Tableau de bord étudiant</b></p></td>
  </tr>
  <tr>
    <td colspan="2"><img src="docs/screenshots/student-schedule.png" alt="Emploi du temps étudiant" /><p align="center"><b>Emploi du temps de l'étudiant</b></p></td>
  </tr>
</table>

## Architecture

Monorepo pnpm organisé autour d'une spécification OpenAPI unique :

```
UEMF-University-Management/
├── artifacts/
│   ├── university-app/     # Frontend React + Vite (pages, layout, contexte d'authentification)
│   └── api-server/         # API Express 5 : routes par module, JWT, RBAC, routes Telegram
├── lib/
│   ├── api-spec/           # openapi.yaml + configuration Orval
│   ├── api-client-react/   # Hooks React Query générés
│   ├── api-zod/            # Schémas Zod générés
│   └── db/                 # Schéma Drizzle ORM et migration SQL
└── scripts/                # Migration, données de démonstration, skill OpenClaw du bot Telegram
```

```mermaid
flowchart LR
    A[Navigateur] -->|/| B[university-app<br/>React + Vite]
    B -->|/api, JWT| C[api-server<br/>Express 5]
    T[Telegram] --> O[OpenClaw<br/>uemf_skill.py] -->|/api/telegram| C
    C -->|Drizzle ORM| D[(PostgreSQL)]
```

## Stack technique

| Couche | Technologies |
|---|---|
| Frontend | React 19, Vite 7, TypeScript, Tailwind CSS 4, shadcn/ui, Recharts, TanStack Query, wouter, react-hook-form |
| Backend | Node.js, Express 5, JWT, bcrypt, pino |
| Données | PostgreSQL, Drizzle ORM, Zod |
| Contrat d'API | OpenAPI 3.0, Orval (génération des hooks et schémas) |
| Intégrations | Bot Telegram via OpenClaw |
| Déploiement | VPS, PM2, Nginx |

## Installation locale

**Prérequis** : Node.js 20+, pnpm, PostgreSQL.

```bash
# 1. Dépendances
pnpm install

# 2. Base de données et données de démonstration
createdb uemf
export DATABASE_URL=postgresql://postgres@localhost:5432/uemf
psql "$DATABASE_URL" -f lib/db/drizzle/0000_premium_norrin_radd.sql
node scripts/run-migration.mjs
node scripts/seed-data.mjs
node scripts/seed-users.mjs
node scripts/seed-telegram-data.mjs   # optionnel : absences et progression

# 3. API (port 8080)
PORT=8080 SESSION_SECRET=change-me pnpm --filter @workspace/api-server run dev

# 4. Frontend (port 22006, dans un autre terminal)
PORT=22006 BASE_PATH=/ pnpm --filter @workspace/university-app run dev
```

L'application est ensuite disponible sur http://localhost:22006 (le serveur Vite redirige `/api` vers le port 8080). Sous Windows, `start.ps1` lance PostgreSQL, l'API et le frontend en une commande après avoir adapté le chemin `$projectRoot`.

### Comptes de démonstration

| Rôle | Identifiant | Mot de passe |
|---|---|---|
| Administrateur | `admin` | `admin123` |
| Administration | `administration` | `admin456` |
| Enseignant | `teacher` | `teacher123` |
| Étudiant | `student` | `student123` |

## Déploiement

La version en ligne tourne sur un VPS : l'API et le frontend sont gérés par PM2, derrière Nginx, avec PostgreSQL sur la même machine. Le bot Telegram passe par OpenClaw, qui appelle les routes `/api/telegram/*` de l'API.

## Équipe

Projet de fin de semestre réalisé à l'EIDIA, Université Euro-Méditerranéenne de Fès, par :

- **Yassine Aitaouicha**
- **Haytam Hannoun**
- **Douaa Bahaja**
- **Hamza El Mourabit**
