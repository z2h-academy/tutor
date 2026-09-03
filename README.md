# Tutor — Tu agente de laboratorios en Z2H Academy

## Qué es

Tutor es el agente que ejecuta tus labs de ingeniería de datos en tu máquina sin Codespaces. Le da acceso a los Developer Docs (guías paso a paso de cada sección) para que el agente de tu TUI (OpenCode, Codex o Claude Code) pueda guiarte en la instalación de entornos, ejecución de scripts y resolución de errores, todo desde tu terminal.

## Para quién

Estudiantes activos de **Z2H Academy** que quieren correr los labs en local (PC, Codespace o container) de forma guiada. Si tenés tu email en la whitelist de la academia, ya tenés acceso.

## Requisitos

- **Node.js ≥ 20** (vía [nvm](https://github.com/nvm-sh/nvm) o instalación directa)
- **Una cuenta de GitHub** cuyo email esté en la whitelist de Z2H Academy
- **Un TUI agentic** con soporte MCP: [OpenCode](https://opencode.ai) es el oficialmente soportado

## Quick start

### 1. Instalar el binario

```bash
npm install -g @z2h-academy/tutor
```

El `postinstall` registra automáticamente el MCP server `tutor-local` en tu OpenCode (sin configuración manual).

### 2. Autenticarte (una vez)

```bash
tutor login
```

Te mostrará un código y una URL:

```
  Abre esta URL en tu navegador y autoriza el acceso:
    https://github.com/login/device

  Tu código de verificación: XXXX-XXXX
  (expira en 15 min)
```

1. Abrí la URL en el navegador
2. Ingresá el código
3. Autorizá **Z2H Academy** con tu cuenta de GitHub

La CLI valida que tu email esté en la whitelist (si no, responde 403) y crea una service account de MinIO **read-only** para ti. Las credenciales quedan en:

```
~/.config/z2h/tutor.env   (perms 600 — solo tuyo)
```

### 3. Verificar

Desde tu TUI (OpenCode), pedile que invoque la tool:

```
tutor_get_section(roadmap="data-engineering", level="nivel-0", section="1-section")
```

Deberías recibir el Markdown de esa sección del Developer Doc.

También podés verificar la conexión del MCP:

```bash
opencode mcp list
# → ●  ✓ tutor-local  connected
```

## Qué incluye

El paquete instala **6 skills** que guían al agente durante tu trabajo:

| Skill | Qué hace |
|---|---|
| `tutor-discover` | Lista roadmaps y niveles disponibles |
| `tutor-read-section` | Lee una sección del Developer Doc con `tutor_get_section` |
| `tutor-study-path` | Orden secuencial de estudio |
| `tutor-explain-section` | Explica/resumir el contenido cargado |
| `tutor-run-local` | Ejecuta labs en local (modo manual o automático, clona en `/workspaces/`) |
| `tutor-debug` | Diagnostica errores del MCP o del agente |

## Acceso

El acceso es por invitación. Si tu email no está en la whitelist, contactá al administrador de Z2H Academy para solicitar tu lugar.

## Troubleshooting

| Problema | Solución |
|---|---|
| `email not in pre_enrollment whitelist` | Tu email no está en la whitelist — contactá al admin |
| `grant user:email scope` | Asegurate de autorizar el scope `user:email` en el device flow |
| `AccessDenied` al leer | Tu service account fue revocada — corrí `tutor login` de nuevo |
| El MCP no aparece en el TUI | Verificá la ruta del binario y reiniciá el TUI |
| `no email available` | Tu cuenta GitHub no tiene email público — configurá uno en Settings → Emails |

## Soporte

Para consultas sobre acceso, whitelist o uso del agente, contactá al administrador de Z2H Academy.

---

**Licencia**: Uso exclusivo para estudiantes activos de Z2H Academy. Ver `LICENSE` para detalles.
