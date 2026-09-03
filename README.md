# Tutor — MCP server para Developer Docs de Z2H Academy

## Qué es

`tutor` es un harness/agente que expone los **Developer Docs** (MDs de los roadmaps)
a TUIs agentic (OpenCode hoy; Codex y Claude Code en el futuro) vía el protocolo MCP.

> **Nota de naming**: En Arq-1 (dev3, laboratorio interno) el MCP se llama `tutor-local`.
> En Arq-2 (dev4, producto para estudiantes) se llama `tutor` (nombre de marca).

Los MDs viven en un storage S3-compatible (**MinIO en la VPS de producción**,
`https://minio.z2h-academy.com`). El LLM de la TUI los consume directamente —
**no** las secciones TSX del web, que al contener componentes React consumen
más tokens y no son la fuente de verdad operativa.

## Por qué existe

La academia tiene dos representaciones del contenido:

| Representación | Consumidor | Fuente |
|---|---|---|
| Secciones TSX (`src/content/...`) | Estudiante en el web | Pipeline MD → TSX |
| MD fuente (`{roadmap}/{level}/{section}.md`) | LLM en TUIs agentic | Storage S3-compatible |

El estudiante ejecuta labs en local siguiendo al pie de la letra las instrucciones
del MD. `tutor` es el puente que le da al LLM acceso a ese contenido sin pasar por
el pipeline de renderizado.

## Estado actual

**v0.3.5 — harness de 6 skills embebidas.** Una sola tool MCP
(`tutor_get_section`), MinIO en la VPS (`https://minio.z2h-academy.com`, bucket
`roadmaps`), auth por estudiante con **device flow de GitHub** + Edge Function de
provisioning en Supabase (service account read-only por estudiante). El binario
se distribuye como paquete instalable (GitHub Releases). El registro del MCP en
OpenCode es **automático** (postinstall), y el postinstall además instala **6
skills de OpenCode** (harness) que guían al agente: leer secciones, descubrir
roadmaps, seguir el orden de estudio, explicar contenido, ejecutar labs en
local y diagnosticar errores. Flujo validado end-to-end en el entorno Sysbox
canónico con OpenCode real.

## Skills

El paquete instala 6 skills en `~/.config/opencode/skills/` automáticamente
(directorio por skill con `SKILL.md`, formato nativo de OpenCode):

| Skill | Para qué | Activación |
|---|---|---|
| `tutor-read-section` | Leer una sección del Developer Docs con `tutor_get_section` | "dame X", "primera sección", "lab" |
| `tutor-discover` | Listar roadmaps y niveles disponibles | "qué roadmaps hay", "por dónde empiezo" |
| `tutor-study-path` | Orden secuencial de estudio (nivel → nivel) | "estudiar desde cero", "siguiente sección" |
| `tutor-explain-section` | Explicar/resumir/responder sobre el MD cargado | "explicame X", "qué significa Y" |
| `tutor-run-local` | Ejecutar labs en local sin Codespaces (modo manual/automático, clona el repo en `/workspaces/`) | "ejecutar el lab en local", "sin Codespaces" |
| `tutor-debug` | Diagnosticar errores del MCP o de la tool | error de tutor, AccessDenied, MCP no conecta |

Las skills se instalan vía `postinstall` (y manualmente con
`tutor-install-skills`). Fuentes: `skills/student/` (se distribuyen) y
`skills/admin/tutor-reseed` (solo repo interno, no se publica).

## Seed masivo del bucket

`scripts/seed-bulk.ts` sube todas las secciones MD de los roadmaps al bucket:

```bash
source <(ssh z2h@62.238.103.174 'cat ~/tutor-minio/.env')
npx tsx scripts/seed-bulk.ts                    # data-engineering + ai-engineering (192)
npx tsx scripts/seed-bulk.ts --only ai-engineering
npx tsx scripts/seed-bulk.ts --dry-run
```

Para agregar un roadmap: sumar la entrada `{slug, source}` al array `ROADMAPS`.
Detalles en `docs/DEVELOPMENT.md`.

## Arquitectura

```
OpenCode / Codex / Claude Code
        │
        ▼  MCP (stdio)
      tutor-local
        │  @aws-sdk/client-s3 (S3-compatible, forcePathStyle)
        ▼
      MinIO (VPS producción, HTTPS vía Caddy)
        │
        ▼
  roadmaps/{roadmap}/{level}/{section}.md
```

Detalle completo en [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Stack

- Node 20 + TypeScript 5 (ESM)
- `@modelcontextprotocol/sdk` (protocolo MCP)
- `@aws-sdk/client-s3` (cliente S3-compatible para MinIO)
- `zod` (validación de input de tools)

## Estructura

```
tutor/
├── harness/             # Z2H Harness 🔒 — control plane (Arq-2, privado)
│   ├── src/             # Fastify server: MCP, WS protocol, labs, validators
│   ├── deploy/          # deploy-to-hetzner.sh (VPS)
│   └── tests/           # suite vitest (39 tests)
├── scripts/
│   ├── seed.ts          # crea bucket + sube un MD de prueba (contra VPS)
│   ├── smoke.ts         # test JSON-RPC end-to-end del server
│   └── sync-protocol.ts # copia protocol types desde harness (fuente única)
└── src/
    ├── index.ts         # entrypoint MCP (stdio transport)
    ├── server.ts        # instancia McpServer
    ├── storage.ts       # cliente S3/MinIO (lee ~/.config/z2h/tutor.env)
    ├── cli/
    │   ├── login.ts     # tutor login — device flow de GitHub
    │   └── setup.ts     # tutor setup — auto-registro del MCP en OpenCode
    ├── runtime/         # tutor-runtime daemon (OpenCode + proxy + WS al Harness)
    └── tools/
        └── get-section.ts  # tool: tutor_get_section
```

## Instalación (estudiante)

```bash
# 1. Instalar el binario (la última versión sale de GitHub Releases)
npm install -g https://github.com/z2h-academy/tutor/releases/download/v0.3.5/z2h-academy-tutor-0.3.5.tgz
# → postinstall registra el MCP en OpenCode automáticamente

# 2. Autenticación (device flow de GitHub, una vez)
tutor login
# → abre https://github.com/login/device, ingresa el código, autoriza
# → guarda credenciales en ~/.config/z2h/tutor.env (perms 600)

# 3. Verificar que el MCP conecta
opencode mcp list
# → ●  ✓ tutor-local  connected
```

> Si el postinstall se skipeó (instalación con `--ignore-scripts`, pnpm, etc.):
> correr `tutor setup` manualmente — idempotente, preserva otros MCPs.

Para probar el loop completo sin OpenCode (desarrollo):

```bash
npm install && npm run build && npm run smoke
```

> **Infraestructura**: MinIO corre en la VPS de producción
> (`~/tutor-minio/` en `62.238.103.174`, ver `docs/VPS.md`). No hay MinIO local.
> Para el estudiante, ver [docs/STUDENT-SETUP.md](docs/STUDENT-SETUP.md).

## Tools

| Tool | Input | Output |
|---|---|---|
| `tutor_get_section` | `{ roadmap, level, section }` | Contenido del MD de la sección |

Convención de paths en el bucket:

```
roadmaps/{roadmap}/{level}/{section}.md
```

Ejemplo: `roadmaps/data-engineering/nivel-0/1-section.md`

## Env vars

El MCP server lee las credenciales en orden de precedencia:
**env vars del proceso > `~/.config/z2h/tutor.env` (creado por `tutor login`) > defaults**.

| Var | Default | Nota |
|---|---|---|
| `MINIO_ENDPOINT` | `https://minio.z2h-academy.com` | Endpoint de producción (VPS) |
| `MINIO_ACCESS_KEY` | — | Se obtiene vía `tutor login` (device flow) |
| `MINIO_SECRET_KEY` | — | Se obtiene vía `tutor login` (device flow) |
| `TUTOR_BUCKET` | `roadmaps` | Bucket compartido |

## Próximos pasos

- Cómo extender el server: [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md)
- Decisiones tomadas, diferidas y riesgos: [docs/DECISIONS.md](docs/DECISIONS.md)
- Operación del MinIO en la VPS: [docs/VPS.md](docs/VPS.md)
- Setup del estudiante: [docs/STUDENT-SETUP.md](docs/STUDENT-SETUP.md)
- Releases: https://github.com/z2h-academy/tutor/releases