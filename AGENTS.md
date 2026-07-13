## Contexto del proyecto

- **Qué es**: Sistema de gestión clínica y de historias clínicas enfocado en la normativa colombiana (Resolución 3100, Ley 23 de 1981 y Habeas Data), diseñado con arquitectura "Local-First" que escala a SaaS.
- **Stack principal**: Frontend con React.js y Tailwind CSS; Backend con Node.js (Express); Base de datos local con SQLite + SQLCipher, Base de datos en la nube con PostgreSQL; ORM con Prisma; y empaquetado de escritorio con Electron.
- **Audiencia / usuarios**: Psicólogos, profesionales de la salud mental y clínicas en Colombia (incluye roles como médicos, administradores y personal autorizado).

## Principios generales

- Prefiere cambios pequeños y fáciles de revisar sobre refactors grandes.
- No inventes frameworks, librerías o herramientas nuevas sin que se pida explícitamente.
- Mantén la consistencia con los patrones ya existentes en el repo, aunque no sean los que tú elegirías.
- Si una tarea es ambigua, haz la suposición más razonable y decláralo en tu respuesta, no te quedes bloqueado.

## Calidad de código

- Preserva el formato y las convenciones ya presentes (indentación, nombres, orden de imports).
- Agrega o actualiza tests solo si el repo ya tiene una suite de tests establecida.
- Explica brevemente los tradeoffs cuando tomes decisiones de arquitectura, en formato de nota tipo PR.
- Usa Prettier y ESLint siguiendo las configuraciones del repositorio. Asegura tipado estricto (TypeScript si aplica) para evitar errores críticos en entornos clínicos.

## Comandos y scripts del proyecto

- Usa los scripts/comandos ya definidos en `README.md` o `package.json`.
- No agregues nuevo tooling de build a menos que sea estrictamente necesario.
- Comandos clave (asumidos según el stack de Node/React):
    - Instalar dependencias: `npm install` o `npm ci`
    - Correr tests: `npm test`
    - Levantar entorno local: `npm run dev`
    - Build: `npm run build`
 

## Estilo de commits

Debes usar uno de los siguientes prefijos para cada commit:

- **`feat`**: Una nueva característica o funcionalidad para el usuario (ej. *nuevo módulo de agenda, nuevo endpoint de pacientes*).
- **`fix`**: Corrección de un error o bug (ej. *corrección de error al guardar historia clínica, validación de DIAN*).
- **`docs`**: Cambios exclusivos en la documentación (ej. *actualización del README, cambios en la Wiki, nuevos diagramas*).
- **`style`**: Cambios que no afectan el significado del código (espaciado, formato, comas, uso de Prettier/ESLint).
- **`refactor`**: Un cambio de código que no corrige un error ni añade una característica, pero mejora la estructura (ej. *simplificación de un controlador, extracción de un componente en React*).
- **`perf`**: Un cambio de código que mejora el rendimiento de la aplicación.
- **`test`**: Añadir pruebas faltantes o corregir pruebas existentes (Jest, Supertest, Playwright).
- **`build`**: Cambios que afectan el sistema de construcción o dependencias externas (ej. *npm, configuraciones de Prisma, empaquetado de Electron*).
- **`ci`**: Cambios en los archivos de configuración y scripts de Integración Continua (ej. *GitHub Actions*).
- **`chore`**: Otras tareas de mantenimiento que no modifican código fuente ni pruebas (ej. *actualizar dependencias menores, limpieza de archivos ignorados*).


## Archivos y estructura

- Coloca el código nuevo cerca del código relacionado; no reorganices directorios sin que se pida.
- Evita refactors grandes de estructura de carpetas a menos que se solicite explícitamente.
- Estructura de carpetas relevante (ejemplo sugerido en base al stack):
    - `src/frontend/` → Componentes de React, interfaces, Tailwind, hooks y vistas.
    - `src/backend/` → Controladores, rutas de Express, servicios de lógica de negocio.
    - `prisma/` → Modelos de base de datos (schema.prisma) y migraciones.

## Qué NO tocar

- No cambies el schema de la base de datos de Prisma sin generar y probar una migración (`npx prisma migrate`).
- No relajes reglas de seguridad, roles o validaciones en módulos críticos (Historia Clínica, RIPS, Facturación DIAN).
- No modifiques los algoritmos de encriptación y protección de datos sin aprobación explícita.

## Testing

- Framework de testing: Jest (recomendado para el ecosistema Node/React).
- Antes de dar por terminada una tarea, corre: `npm test`
- Cobertura mínima esperada: Alta cobertura en módulos de Historia Clínica, Facturación Electrónica y Control de Acceso.

## Seguridad y datos sensibles

- Nunca hardcodees credenciales, API keys o secretos — usa variables de entorno (`.env`).
- Cumplimiento normativo de salud (Res. 3100, Ley 1581): Todos los datos de historias clínicas deben encriptarse (AES-256 en base de datos local vía SQLCipher).
- Respeta estrictamente el Control de Acceso Basado en Roles (RBAC). El acceso a Historias Clínicas debe registrar un log de auditoría.
- Asegura la estructura JSON para la facturación (DIAN) y los reportes de salud (RIPS/HL7 FHIR).

## Estilo de respuesta esperado de Copilot

- Al recibir una tarea ambigua, resume tu interpretación antes de generar código.
- Prioriza soluciones simples y legibles sobre soluciones "inteligentes" pero difíciles de mantener.
- Si una tarea requiere tocar múltiples módulos (ej. Frontend, Backend, Prisma), propone el plan antes de implementar.
