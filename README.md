# HealthTrack – Offline-First Patient Management System

> Built as a take-home assignment for Medblocks in May 2025.

## Overview

**HealthTrack** is a modern offline-first patient management system built for healthcare providers. It enables efficient registration, tracking, and management of patient data, even in environments with unreliable internet connectivity.

Designed with a focus on user experience and data reliability, HealthTrack uses **PGlite**, a fully featured SQL database that runs entirely in the browser.

---

## Live Demo

🔗 [View Deployed App](https://healthtrack-navy.vercel.app/)

---


## Features

* **Patient Registration** – Collect and store comprehensive patient details
* **Patient List View** – Browse and search through registered patients
* **SQL Query Interface** – Execute custom SQL queries on patient data
* **Offline-First Architecture** – Full functionality without an internet connection
* **Responsive Design** – Optimized for desktop, tablet, and mobile
* **Dark/Light Mode** – Auto-detects system theme with manual toggle
* **Database Status Indicator** – Real-time feedback on database status

---

## Technology Stack

* **Frontend** – React 19, TypeScript
* **Database** – PGlite (PostgreSQL compiled to WebAssembly)
* **Build Tool** – Vite
* **Styling** – Tailwind CSS
* **Icons** – Lucide React
* **Routing** – React Router v7

---

## Installation

### Prerequisites

* Node.js 18
* npm / pnpm / yarn

### Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/aayxshkumar/healthtrack.git
   cd healthtrack
   ```

2. Install dependencies:

   ```bash
   npm install      # or pnpm install
                    # or yarn install
   ```

3. Start the development server:

   ```bash
   npm run dev      # or pnpm dev
                    # or yarn dev
   ```

4. Open your browser and navigate to `http://localhost:5173`

---

## Building for Production

```bash
npm run build       # or pnpm build
                    # or yarn build
```

The production build will be located in the `dist/` directory.

---

## Database Schema

HealthTrack uses a straightforward but comprehensive schema:

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

---

## Application Structure

```
healthtrack/
├── public/                  # Static assets and PGlite worker
│   └── pglite-worker.js     # Worker script for PGlite
├── src/
│   ├── components/          # Reusable UI components
│   │   ├── DatabaseStatus.tsx
│   │   ├── EmptyState.tsx
│   │   ├── Layout.tsx
│   │   ├── LoadingState.tsx
│   │   ├── Navbar.tsx
│   │   └── Sidebar.tsx
│   ├── context/             # React context providers
│   │   └── DatabaseContext.tsx
│   ├── pages/               # Page components
│   │   ├── Dashboard.tsx
│   │   ├── PatientList.tsx
│   │   ├── PatientQuery.tsx
│   │   └── PatientRegistration.tsx
│   ├── services/            # Business logic and API
│   │   └── DatabaseService.ts
│   ├── App.tsx              # Main application component
│   ├── index.css            # Global styles
│   └── main.tsx             # Entry point
├── package.json             # Dependencies and scripts
├── tsconfig.json            # TypeScript configuration
└── vite.config.ts           # Vite configuration
```

---

## Offline Functionality

HealthTrack is designed to function entirely offline after the initial load. It:

* Stores all patient data in the browser’s IndexedDB
* Allows patient registration without an internet connection
* Maintains full functionality offline
* Has no backend dependencies for core operations

---

## Usage Guide

### Dashboard

Provides access to key features and displays essential metrics.

### Patient Registration

Complete the form with all required fields (marked with `*`) and optional details. Built-in validation ensures accurate data entry.

### Patient List

Browse and search through registered patients. Data is displayed in a clean, tabular format.

### Query Interface

Run custom SQL queries directly on patient data. Includes sample queries for common operations.

---

## Contributing

1. Fork the repository

2. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature-name
   ```

3. Commit your changes:

   ```bash
   git commit -m "Describe your changes"
   ```

4. Push the branch:

   ```bash
   git push origin feature/your-feature-name
   ```

5. Open a Pull Request
