<p align="center">
  <img src="logo.svg" alt="TUTOR — Z2H Academy" width="520">
</p>

<p align="center">
  <strong>Deja de ver cursos. Construye con AI.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-0.8.0-ffd300?style=flat-square" alt="versión 0.8.0">
  <img src="https://img.shields.io/badge/license-Proprietary-0b0b10?style=flat-square" alt="licencia propietaria">
  <img src="https://img.shields.io/badge/node-%3E%3D22-2fe08a?style=flat-square" alt="node 22 o superior">
</p>

<p align="center">
  <a href="#qué-es">qué es</a> ·
  <a href="#el-flujo">flujo</a> ·
  <a href="#para-quién-es">acceso</a> ·
  <a href="#quick-start">quick start</a> ·
  <a href="#troubleshooting">troubleshooting</a>
</p>

**TUTOR** conecta tu agente de terminal —**OpenCode, Codex o Claude Code**— con los Roadmaps, Developer Docs y Labs de Z2H Academy. Tú construyes en tu entorno. El harness dirige y valida.

---

## Qué es

Tutor no es un chatbot. Es el harness que conecta al agente con Z2H Academy.

Un agente de IA sabe ejecutar comandos y resolver problemas, pero no conoce la estructura pedagógica de la academia. **Tutor es la pieza que conecta ambas cosas vía MCP.**

> El agente ejecuta.
> Tutor conecta y orquesta.
> El Harness dirige y valida.
> Los Developer Docs contienen el conocimiento.

El agente puede cambiar —OpenCode, Codex o Claude Code— sin que la lógica de aprendizaje dependa de un modelo específico.

## El flujo

`Roadmap → Agente → Tutor → Lab → Validación`

| Paso | Qué pasa |
|---|---|
| **1. Descubre** | El agente lista los roadmaps, niveles y secciones disponibles para tu cuenta. |
| **2. Consulta** | Lee el Developer Doc de la sección y te explica qué debe realizarse. |
| **3. Ejecuta** | Corre las acciones del lab en tu entorno; si algo falla, te ayuda a corregirlo. |
| **4. Valida** | El harness verifica el progreso. No es el agente quien decide si está bien. |
| **5. Avanza** | Con la sección validada, el agente continúa con el siguiente paso. |

## ¿Para quién es?

TUTOR es para **estudiantes activos de Z2H Academy**.

El acceso está controlado por whitelist: si el email de tu cuenta de GitHub está habilitado, puedes autenticarte y empezar. Si no, contacta al administrador.

## Requisitos

Antes de instalar Tutor se necesita:

* **Node.js 22 o 24** (recomendado: 24 LTS), instalado mediante nvm.
* **Una cuenta de GitHub** cuyo email esté incluido en la whitelist de Z2H Academy.
* **Un agente de terminal con soporte MCP**.
* **Git** (para clonar repos y trabajar con codespaces).
* **GitHub CLI (`gh`)** (solo para labs en Codespaces — ver https://cli.github.com).

Los agentes soportados incluyen:

* **OpenCode**
* **Codex**
* **Claude Code**

OpenCode es actualmente el cliente oficialmente soportado.

---

## Quick Start

<details>
<summary><strong>1. Instalar nvm + Node.js (Linux)</strong></summary>

Si aún no tienes Node.js, instálalo mediante nvm (Node Version Manager):

```bash
# Instalar nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

# Cargar nvm en la sesión actual (o reinicia la terminal)
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"

# Instalar y usar Node.js 24 LTS
nvm install 24
nvm use 24
nvm alias default 24
```

Verificar la instalación:

```bash
node --version   # debe mostrar v24.x.x
npm --version    # debe mostrar 10.x o 11.x
```

> **Versiones correctas:** Node.js **22 o 24** (24 LTS recomendado). npm viene incluido con Node.js (no se instala por separado). No uses Node.js 20 o inferior — Tutor requiere funciones modernas de JavaScript.

</details>

<details>
<summary><strong>2. Instalar OpenCode</strong></summary>

Instalar el agente OpenCode con el instalador oficial:

```bash
curl -fsSL https://opencode.ai/install | bash
```

Verificar la instalación (reinicia la terminal primero si es necesario):

```bash
opencode --version
```

> Si el comando no se encuentra, agrega `~/.opencode/bin` a tu `PATH` o reinicia la terminal.

</details>

<details>
<summary><strong>3. Instalar Tutor</strong></summary>

Instalar el paquete globalmente desde el último release:

```
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

Esto instala los comandos `tutor`, `tutor-mcp`, `tutor-setup` y `tutor-runtime`.
La configuración del MCP se realiza en el siguiente paso con `tutor login`
(no es necesario realizar una configuración manual del MCP).

> Para una versión específica: reemplaza `latest` por el tag (ej. `.../download/v0.8.0/z2h-academy-tutor-0.8.0.tgz`).
> Para actualizar a la última versión, repite el comando de instalación.

</details>

<details>
<summary><strong>4. Autenticarse</strong></summary>

La autenticación se realiza una única vez:

```
tutor login
```

Tutor iniciará el GitHub Device Flow y mostrará una URL y un código de verificación:

```
Abre esta URL en el navegador y autoriza el acceso:

  https://github.com/login/device

Tu código de verificación: XXXX-XXXX

(expira en 15 min)
```

Abrir la URL, ingresar el código y autorizar **Z2H Academy** con la cuenta de GitHub.

Durante este proceso, Tutor verifica que el email esté habilitado en la whitelist de la academia.

Una vez autorizado el acceso, Tutor obtiene las credenciales necesarias para comunicarse con los servicios de Z2H Academy.

Las credenciales locales se almacenan en:

```
~/.config/z2h/tutor.env
```

con permisos `600`, de modo que únicamente el usuario pueda acceder al archivo.

Al finalizar, `tutor login` configura automáticamente el MCP server en
OpenCode. Si necesitas reconfigurarlo manualmente (por ejemplo, después de
reinstalar OpenCode), ejecuta:

```
tutor setup
```

Esto registra el MCP y aplica el tema visual TUTOR. Reinicia OpenCode para
que detecte los cambios.

</details>

<details>
<summary><strong>5. Verificar la instalación</strong></summary>

Desde OpenCode se puede pedir al agente que consulte una sección:

```
tutor_get_section(
  roadmap="data-engineering",
  level="nivel-0",
  section="1-section"
)
```

Si la instalación y autenticación son correctas, el agente debería recibir el Markdown correspondiente al Developer Doc de esa sección.

También se puede verificar que el MCP esté conectado:

```
opencode mcp list
```

</details>

---

## Troubleshooting

| Problema | Solución |
|---|---|
| `cuenta no habilitada` | El email no está habilitado. Contactar al administrador de Z2H Academy. |
| `grant user:email scope` | Verificar que se haya autorizado el scope `user:email` durante el GitHub Device Flow. |
| `AccessDenied` al leer contenido | La service account asociada al usuario puede haber sido revocada. Ejecutar `tutor login` nuevamente. |
| El MCP no aparece en OpenCode | Verificar que Tutor esté instalado correctamente, comprobar la ruta del binario y reiniciar OpenCode. |
| `no email available` | GitHub no está proporcionando un email para la cuenta. Verificar la configuración de emails de la cuenta de GitHub. |
| `gh: command not found` | Instalar GitHub CLI desde https://cli.github.com (necesario para labs en Codespaces). |
| `You are not logged into any GitHub hosts` | Ejecutar `gh auth login` y completar el flujo de autenticación. |

---

## Soporte

Para problemas relacionados con acceso, autenticación, configuración de Tutor, conexión MCP, Roadmaps o labs, contactar al administrador de Z2H Academy.

---

## Licencia

Tutor está destinado exclusivamente al uso por parte de estudiantes activos de Z2H Academy.

Consultar el archivo `LICENSE` incluido en el proyecto para conocer los términos completos de uso.

---

<p align="center">
  <sub>El agente ejecuta · Tutor conecta y orquesta · el Harness dirige y valida</sub>
</p>
