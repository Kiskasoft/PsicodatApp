# PsicodatApp

PsicodatApp es una base de proyecto para un sistema de gestión clínica y de historias clínicas orientado al entorno de salud mental en Colombia. El repositorio está organizado como una app local-first con tres piezas principales:

- Frontend en React + Vite
- Backend en Node.js + Express
- Escritorio con Electron

## Estado actual

El proyecto ya tiene la estructura base montada y puede ejecutarse en desarrollo, pero todavía es un scaffold inicial.

- El frontend vive en `src/frontend`
- El backend vive en `src/backend`
- Electron vive en `src/electron`
- Prisma vive en `src/prisma`

Por ahora, el backend expone una ruta de salud en `/api/health`, y Electron carga el frontend desde `http://localhost:5173`.

## Requisitos

- Node.js instalado
- npm instalado

## Instalación

La app está separada por carpetas, así que instala dependencias en cada paquete:

```bash
cd src
npm install

cd frontend
npm install

cd ../backend
npm install
```

## Cómo iniciar el proyecto

Desde la carpeta `src`, ejecuta:

```bash
npm run dev
```

Ese comando levanta en paralelo:

- el backend con `nodemon`
- el frontend con Vite
- Electron, que espera a que Vite responda en el puerto `5173`

## Comandos disponibles

Desde `src`:

- `npm run start:frontend` inicia Vite en `src/frontend`
- `npm run start:backend` inicia el backend en `src/backend`
- `npm run start:electron` abre Electron cuando el frontend está listo
- `npm run dev` levanta frontend, backend y Electron al mismo tiempo

## Verificación rápida

Si todo quedó bien, deberías poder:

1. Abrir el frontend en `http://localhost:5173`
2. Probar el backend en `http://localhost:5000/api/health`
3. Ver la ventana de Electron cargando el frontend

## Estructura principal

```text
PsicodatApp/
├── README.md
├── src/
│   ├── package.json
│   ├── backend/
│   ├── electron/
│   ├── frontend/
│   └── prisma/
└── docs/
```

## Notas

- El backend usa `PORT=5000` por defecto si no se define una variable de entorno.
- El frontend aún conserva una base visual inicial, por lo que la UI puede cambiar cuando se incorpore Tailwind u otros estilos.
- La carpeta `src/prisma` ya existe, pero el esquema todavía está en una etapa temprana.
