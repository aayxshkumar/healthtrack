# HealthTrack – Offline-First Patient Management System

![CI](https://github.com/aayxshkumar/healthtrack/actions/workflows/ci.yml/badge.svg)

> Built as a take-home assignment for Medblocks in May 2025.

HealthTrack is a browser-only patient management app. It registers patients, lists and searches them, and lets you run SQL against the patient table. Data lives in [PGlite](https://pglite.dev/) (PostgreSQL compiled to WebAssembly) running in a Web Worker and persisted to IndexedDB, so there is no backend and patient data never leaves the browser.

Live demo: https://healthtrack-navy.vercel.app/

## Features

- Patient registration form with required-field validation
- Patient list with search by name
- SQL query page with example queries
- Dashboard with the total patient count and shortcuts to each page
- Database status indicator
- Light and dark themes, following the system setting with a manual toggle

## Tech stack

- React 19, TypeScript, React Router 7
- PGlite (`@electric-sql/pglite`) in a Web Worker, stored at `idb://healthtrack-db`
- Vite 6
- Tailwind CSS 3, Lucide icons
- ESLint 9 with `typescript-eslint`

## Getting started

Requires Node.js 20 or newer (CI runs on Node 22). No environment variables are needed.

```bash
git clone https://github.com/aayxshkumar/healthtrack.git
cd healthtrack
npm ci
npm run dev       # http://localhost:5173
```

Other scripts:

```bash
npm run lint      # ESLint
npm run build     # type-check (tsc -b) and production build into dist/
npm run preview   # serve the production build
```

## Database schema

```sql
CREATE TABLE patients (
  id SERIAL PRIMARY KEY,
  first_name TEXT NOT NULL,
  last_name TEXT NOT NULL,
  date_of_birth TEXT NOT NULL,
  gender TEXT NOT NULL,
  email TEXT,
  phone TEXT,
  address TEXT,
  medical_notes TEXT,
  insurance_provider TEXT,
  insurance_id TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Project structure

```
public/pglite-worker.js   PGlite worker script
src/
  components/             layout, navbar, sidebar, status and empty/loading states
  context/                database and theme providers
  pages/                  Dashboard, PatientList, PatientQuery, PatientRegistration
  services/               DatabaseService.ts (schema setup and queries)
  App.tsx, main.tsx
Notes.md                  development notes and challenges
```
