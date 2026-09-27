# Portfolio — Ariel Díaz Naso

Portfolio personal con panel de administración, construido con React + Vite + TypeScript y desplegado en Vercel con base de datos Turso (libSQL).

## Stack

- **Frontend:** React 18, TypeScript, Tailwind CSS, Framer Motion
- **Backend:** Vercel Serverless Functions (Node.js)
- **Base de datos:** Turso (libSQL / SQLite edge)
- **Auth:** JWT + bcryptjs
- **Deploy:** Vercel

## Variables de entorno

Crear un archivo `.env` en la raíz basado en `.env.example`:

```env
TURSO_DATABASE_URL=libsql://...
TURSO_AUTH_TOKEN=...
ADMIN_PASSWORD=...
JWT_SECRET=...
```

En Vercel, configurar las mismas variables en el dashboard del proyecto.

## Desarrollo local

```bash
npm install
vercel dev   # levanta el frontend + las API serverless juntas
```

> ⚠️ `npm run dev` (solo Vite) funciona como fallback con datos locales estáticos, pero las rutas `/api/*` requieren `vercel dev`.

## Build y deploy

```bash
npm run build   # compila TypeScript + Vite
```

El deploy se hace automáticamente al hacer push a `main` si el proyecto está conectado a Vercel.

## Estructura

```
├── api/                  # Vercel Serverless Functions
│   ├── db.ts             # Cliente Turso
│   ├── portfolio.ts      # GET /api/portfolio
│   ├── auth_helper.ts    # Verificación JWT
│   ├── auth/
│   │   └── login.ts      # POST /api/auth/login
│   └── admin/
│       ├── profile.ts    # PUT /api/admin/profile
│       ├── experience.ts # POST/PUT/DELETE /api/admin/experience
│       └── projects.ts   # POST/PUT/DELETE /api/admin/projects
├── src/
│   ├── components/       # Componentes React
│   ├── hooks/            # Custom hooks
│   ├── lib/              # Servicios y utilidades
│   ├── types/            # Tipos TypeScript
│   └── data/             # Datos fallback locales
└── public/               # Assets estáticos
```
