# 🚀 JetFlo Project Setup & Execution Guide

This document provides complete, step-by-step instructions for cloning, setting up, running, and building the **JetFlo** project on any computer (Windows, macOS, or Linux).

---

## 📋 1. System Requirements & Prerequisites

Before starting, ensure you have the following installed on your machine:

1. **Git**: [Download Git](https://git-scm.com/downloads)
2. **Node.js**: **v20.x or v22.x (LTS recommended)** — [Download Node.js](https://nodejs.org/)
   - Alternatively, you can use **Bun** (v1.1+): [Download Bun](https://bun.sh/)
3. **Package Manager**: `npm` (comes bundled with Node.js) or `bun`
4. **Code Editor**: VS Code, Cursor, or any editor of your choice

> 💡 **Verify installations** in your terminal:
> ```bash
> git --version
> node --version    # should be v20.x or higher
> npm --version
> ```

---

## 📥 2. Clone the Repository

Open your terminal or command prompt and clone the repository:

```bash
# Clone the repository
git clone https://github.com/davidtechone5-dev/jetflo-v1.git

# Navigate into the project folder
cd jetflo-v1
```

---

## ⚙️ 3. Environment Variables Configuration

Create a `.env` file in the root directory of the project (if it does not already exist):

```bash
# Windows (PowerShell)
New-Item -ItemType File -Name .env -Force

# macOS / Linux
touch .env
```

Open `.env` and paste the following configuration:

```env
# Supabase Configuration
VITE_SUPABASE_URL=https://ukfwmioymiuxctigfpwd.supabase.co
VITE_SUPABASE_ANON_KEY=sb_publishable_-5aZCjbOLH3HzVnDOXXxFw_LLgzsBGT
NEXT_PUBLIC_SUPABASE_URL=https://ukfwmioymiuxctigfpwd.supabase.co
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=sb_publishable_-5aZCjbOLH3HzVnDOXXxFw_LLgzsBGT
```

> 🔒 *Note: The Supabase client in `src/lib/supabase.ts` also contains safe default fallbacks for convenience.*

---

## 📦 4. Install Dependencies

Install all project dependencies using your preferred package manager:

### Using NPM (Recommended):
```bash
npm install
```

*(Optional fallback if peer dependency conflicts arise on older npm versions)*:
```bash
npm install --legacy-peer-deps
```

### Using Bun (Fast alternative):
```bash
bun install
```

---

## 💻 5. Run the Local Development Server

To start the local development server with hot module reloading:

### Using NPM:
```bash
npm run dev
```

### Using Bun:
```bash
bun run dev
```

Once started, open your web browser and navigate to:
```
http://localhost:3000
```
*(Or the local port displayed in your terminal, e.g. `http://localhost:5173`)*

---

## 🏗️ 6. Build and Production Preview

To test the production build locally:

```bash
# 1. Create a production build
npm run build

# 2. Preview the production build locally
npm run preview
```

---

## 🛠️ 7. Available Scripts Reference

| Command | Description |
| :--- | :--- |
| `npm run dev` | Starts the Vite / TanStack Start development server |
| `npm run build` | Builds the application for production deployment |
| `npm run build:dev` | Builds the app with development mode flags |
| `npm run preview` | Serves the production build locally for verification |
| `npm run lint` | Runs ESLint to check for code quality and syntax issues |
| `npm run format` | Runs Prettier to auto-format code across the project |

---

## 🗂️ 8. Project Structure Overview

```text
jetflo-v1/
├── public/                 # Static assets, logos, and images
├── src/
│   ├── assets/             # Brand assets and graphics
│   ├── components/         # Reusable React UI components
│   │   ├── site/           # App-specific components (Header, Footer, LeadForm, CityGate, etc.)
│   │   └── ui/             # Radix UI + Tailwind design system components
│   ├── hooks/              # Custom React hooks (mobile detection, toast, etc.)
│   ├── lib/                # Utilities, catalog data, city selector, and Supabase client
│   ├── routes/             # TanStack Start file-based routing
│   │   ├── __root.tsx      # Root layout and global providers
│   │   ├── index.tsx       # Homepage
│   │   ├── enquiry.tsx     # Enquiry page
│   │   ├── contact.tsx     # Contact page
│   │   └── ...             # Other route pages
│   ├── router.tsx          # Router configuration
│   ├── server.ts           # Server entry point
│   ├── start.ts            # Client bootstrap entry
│   └── styles.css          # Global CSS & Tailwind v4 styling
├── .env                    # Environment variables
├── package.json            # Project dependencies and npm scripts
├── tsconfig.json           # TypeScript configuration
└── vite.config.ts          # Vite & TanStack Start bundler configuration
```

---

## 🧩 9. Tech Stack Summary

- **Framework**: TanStack Start (SSR / Fullstack React)
- **UI Library**: React 19
- **Routing**: TanStack Router
- **Styling**: Tailwind CSS v4 + Radix UI primitives
- **Database / Backend**: Supabase
- **Icons**: Lucide React
- **Build Tool**: Vite 8 + Nitro

---

## ❓ 10. Troubleshooting & FAQs

### Q1: `npm install` fails or throws peer dependency warnings
- **Fix**: Run `npm install --legacy-peer-deps` or ensure your Node.js version is **20.x or 22.x LTS**.

### Q2: Port is already in use
- **Fix**: Vite will automatically try the next available port (e.g. `3001` or `5174`), or you can terminate any process occupying port 3000.

### Q3: TypeScript or Route Tree errors during dev
- **Fix**: TanStack Router automatically generates `src/routeTree.gen.ts` when running `npm run dev`. If you see router errors, restart `npm run dev`.

### Q4: Important Note for Lovable Git Sync
- This repository is connected to Lovable. Avoid force pushing (`git push --force`) or rebasing/squashing already published commits to keep history cleanly synchronized.
