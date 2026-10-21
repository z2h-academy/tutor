<p align="center">
  <img src="logo.svg" alt="TUTOR — Z2H Academy" width="520">
</p>

<p align="center">
  <strong>Deja de ver cursos. Construye con AI.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-0.10.0-ffd300?style=flat-square" alt="versión 0.10.0">
  <img src="https://img.shields.io/badge/license-Proprietary-0b0b10?style=flat-square" alt="licencia propietaria">
  <img src="https://img.shields.io/badge/node-%3E%3D22-2fe08a?style=flat-square" alt="node 22 o superior">
  <a href="https://discord.gg/ycy9zkUreX"><img src="https://img.shields.io/badge/discord-%C3%BAnete-5865F2?style=flat-square&amp;logo=discord&amp;logoColor=white" alt="únete al Discord de Z2H Academy"></a>
</p>

<p align="center">
  <a href="#qué-es">qué es</a> ·
  <a href="#por-qué-tutor">por qué</a> ·
  <a href="#el-flujo">flujo</a> ·
  <a href="#para-quién-es">acceso</a> ·
  <a href="#quick-start">quick start</a> ·
  <a href="#troubleshooting">troubleshooting</a> ·
  <a href="#comunidad">comunidad</a>
</p>

**TUTOR** conecta tu agente de terminal —**OpenCode, Codex o Claude Code**— con los Roadmaps, Developer Docs y Labs de Z2H Academy. Tú construyes en tu entorno. El harness dirige y valida.

---

## Qué es

Tutor no es un chatbot. Es el harness que conecta al agente con Z2H Academy.

Un agente de IA sabe ejecutar comandos y resolver problemas, pero no conoce la estructura pedagógica de la academia. **Tutor es la pieza que conecta ambas cosas.**

> El agente ejecuta.
> Tutor conecta y orquesta.
> El harness dirige y valida.
> Los Developer Docs contienen el conocimiento.

El agente puede cambiar —OpenCode, Codex o Claude Code— sin que la lógica de aprendizaje dependa de un modelo específico.

Los Roadmaps de la academia cubren data engineering, AI, DevOps, Python, PySpark y SQL, organizados en niveles y secciones que viven como documentación técnica real.

## Por qué Tutor

El modelo tradicional optimiza el consumo: videos, ejercicios guiados, certificados. Tutor entrena el criterio técnico que se necesita para construir sistemas reales.

| El modelo tradicional | Con Tutor |
|---|---|
| Videos grabados, idénticos para todos. | Developer Docs vivos, como documentación técnica real. |
| Labs que se copian sin entender. | Labs que ejecutas en tu propio entorno, con tu agente. |
| Nadie verifica si de verdad lo hiciste. | La academia valida cada paso: el agente no decide si está bien. |
| El progreso se pierde entre sesiones. | Tu agente recuerda dónde quedaste. |
| Terminas con un certificado. | Terminas con algo que puedes mostrar. |

## El flujo

`Roadmap → Teoría → Plan → Modo → Lab → Evidencia`

| Paso | Qué pasa |
|---|---|
| **1. Descubre** | El agente lista los roadmaps, niveles y secciones disponibles para tu cuenta. |
| **2. Entiende** | Te presenta la base teórica del nivel y un checkpoint para confirmar que la entendiste. |
| **3. Planifica** | Arma el plan del nivel: cada paso con su por qué, el comando, la salida esperada y la evidencia de cierre. |
| **4. Elige modo** | Te pregunta si prefieres el modo automático (el agente ejecuta) o manual (ejecutas tú). |
| **5. Ejecuta** | Corre el lab en tu entorno; si algo falla, te ayuda a corregirlo. |
| **6. Valida** | La academia valida cada paso con evidencia. No es el agente quien decide si está bien. |

## ¿Para quién es?

TUTOR es para **estudiantes activos de Z2H Academy**.

El acceso está controlado por whitelist: si el email de tu cuenta de GitHub está habilitado, puedes autenticarte y empezar. Si no, contacta al administrador.

## Requisitos

Antes de instalar Tutor se necesita:

* **Node.js 22 o 24** (recomendado: 24 LTS), instalado mediante nvm.
* **Una cuenta de GitHub** cuyo email esté incluido en la whitelist de Z2H Academy.
* **Un agente de terminal con soporte MCP**.
* **Git** (para clonar repos y trabajar con codespaces).
* **Docker** (para los labs que levantan servicios en tu máquina; si falta, el agente te guía para instalarlo).
* **GitHub CLI (`gh`)** (solo para labs en Codespaces — ver https://cli.github.com).

Los agentes soportados incluyen:

* **OpenCode**
* **Codex**
* **Claude Code**

OpenCode es el cliente oficialmente soportado. **Tutor 0.10.0 requiere OpenCode 2**: si todavía usas OpenCode 1, quédate en Tutor 0.8.0.

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
opencode --version   # debe mostrar 2.x
```

> Si el comando no se encuentra, agrega `~/.opencode/bin` a tu `PATH` o reinicia la terminal.

> **Requisito de versión:** Tutor 0.10.0 requiere OpenCode 2. Si todavía usas OpenCode 1, quédate en Tutor 0.8.0.

</details>

<details>
<summary><strong>3. Instalar Tutor</strong></summary>

Instala la CLI de Tutor globalmente desde el último release:

```
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

No necesitas configurar nada a mano: el siguiente paso deja todo listo.

> Para una versión específica: reemplaza `latest` por el tag (ej. `.../download/v0.10.0/z2h-academy-tutor-0.10.0.tgz`).
> Para actualizar una instalación existente, consulta el paso 6.

</details>

<details>
<summary><strong>4. Autenticarse</strong></summary>

La autenticación se realiza una única vez:

```
tutor login
```

Tutor iniciará el login con GitHub y mostrará una URL y un código de verificación:

```
Abre esta URL en el navegador y autoriza el acceso:

  https://github.com/login/device

Tu código de verificación: XXXX-XXXX

(expira en 15 min)
```

Abre la URL, ingresa el código y autoriza **Z2H Academy** con tu cuenta de GitHub.

Durante este proceso, Tutor verifica que tu email esté habilitado en la whitelist de la academia.

Una vez autorizado, Tutor deja tu agente conectado y listo para usar: la conexión con la academia, el tema visual TUTOR y **Tutor Memory**, tu memoria entre sesiones.

Las credenciales locales se almacenan en:

```
~/.config/z2h/tutor.env
```

con permisos `600`, de modo que únicamente tú puedas acceder al archivo.

Si necesitas reconfigurar tu agente (por ejemplo, después de reinstalar OpenCode), ejecuta:

```
tutor setup
```

Reinicia OpenCode para que detecte los cambios.

</details>

<details>
<summary><strong>5. Verificar la instalación</strong></summary>

Desde OpenCode, pídele al agente:

```
dime a qué roadmaps tengo acceso
```

Si te devuelve los roadmaps, niveles y secciones habilitados para tu cuenta, la instalación está completa.

También puedes verificar que la conexión esté activa:

```
opencode mcp list
```

Debería aparecer la conexión de Tutor como conectada:

```
●  ✓ tutor  connected
```

</details>

<details>
<summary><strong>6. Actualizar a la última versión</strong></summary>

La actualización es en dos pasos. Primero, instala la nueva versión:

```
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

Después, aplica la configuración en tu agente:

```
tutor setup
```

Reinicia OpenCode al terminar.

> Reinstalar el paquete por sí solo no actualiza tu configuración local: `tutor setup` es el paso que la deja al día.

</details>

---

## Tutor Memory

**Tu progreso no se pierde: se recuerda.**

Tutor incluye **Tutor Memory**, la memoria de tu aprendizaje. Viene activada desde la instalación: sin cuentas, sin pasos extra.

* **Tu agente recuerda.** Dónde quedaste, qué decidiste y los resúmenes de tus sesiones anteriores. Nunca empiezas de cero.
* **Cada proyecto recuerda lo suyo.** La memoria es de tu proyecto, no de tu persona: cada repo tiene su propio historial.
* **Viaja contigo.** Tu progreso puede viajar dentro de tu repositorio: llévalo de tu PC a tu Codespace (o al revés) y continúa donde estabas.
* **Privada por diseño.** Se guarda en tu entorno de trabajo y no se mezcla con la de nadie más.

Pídeselo así:

| Lo que quieres | Frase de ejemplo |
|---|---|
| Retomar donde quedaste | *"¿dónde quedamos la última sesión?"* |
| Guardar tu avance | *"recuerda que terminé la sección 2 del nivel 0"* |
| Guardar una decisión | *"recuerda que decidimos usar Docker para los labs y por qué"* |
| Recuperar algo del pasado | *"¿qué habíamos decidido sobre el modelo de datos?"* |
| Cerrar con contexto | *"dame un resumen de la sesión para continuar mañana"* |
| Llevar tu progreso a otra máquina | *"guarda mi progreso en el repo para continuar desde el Codespace"* |

> ¿Prefieres la terminal? La memoria también se gestiona con la CLI: `tutor memory` (`save`, `search`, `status`, `export`, `import`).

## Tu agente ya viene listo

Tutor le enseña a tu agente cómo trabajar con la academia:

* **Descubrir tu contenido** — roadmaps, niveles y secciones disponibles para tu cuenta.
* **Guiarte en el orden correcto** — sabe qué paso sigue según tu roadmap.
* **Explicarte cada tema** — resume y aclara el contenido antes de ejecutar, con tablas, diagramas y ejemplos cuando hacen falta.
* **Ejecutar tus labs** — en local o en un Codespace, en modo manual o automático.
* **Validar cada paso** — contra los criterios de la academia, no contra la opinión del modelo.
* **Diagnosticar cuando algo falla** — te ayuda a encontrar la causa en lugar de adivinar.

## Dos formas de usarlo

* **Local** — en tu terminal: instala Tutor, autentícate y abre tu agente. Funciona en tu PC, en un Codespace o en un container.
* **Web** — en el navegador: entra a [tutor.z2h-academy.com](https://tutor.z2h-academy.com), inicia sesión con GitHub y usa OpenCode con tu propio entorno en la nube.

---

## Troubleshooting

| Problema | Solución |
|---|---|
| `email not in pre_enrollment whitelist` | Tu email no está habilitado. Contacta al administrador de Z2H Academy. |
| `grant user:email scope` | Verifica que hayas autorizado el scope `user:email` durante el login con GitHub. |
| `AccessDenied` al leer contenido | Tu acceso al contenido expiró o fue revocado. Ejecuta `tutor login` nuevamente. |
| Después de actualizar, no se ven los cambios | Ejecuta `tutor setup` y reinicia OpenCode. |
| El login dice que el comando es interactivo | Ejecuta `tutor login` tú mismo en tu terminal, con el navegador a mano. No lo lances desde el agente. |
| No aparece un roadmap que debería estar habilitado | Ejecuta `tutor login` nuevamente para actualizar tu acceso. |
| La conexión de Tutor no aparece en OpenCode | Verifica que Tutor esté instalado, ejecuta `tutor setup` y reinicia OpenCode. |
| `no email available` | GitHub no está proporcionando un email para tu cuenta. Revisa la configuración de emails de tu cuenta de GitHub. |
| `gh: command not found` | Instala GitHub CLI desde https://cli.github.com (necesario para labs en Codespaces). |
| `You are not logged into any GitHub hosts` | Ejecuta `gh auth login` y completa el flujo de autenticación. |
| Usas OpenCode 1 | Tutor 0.10.0 requiere OpenCode 2. Actualiza OpenCode o quédate en Tutor 0.8.0. |

---

## Comunidad

**Construir es mejor acompañado.**

El Discord de Z2H Academy reúne a los estudiantes de todos los roadmaps:

* **Resuelve bloqueos.** Cuando un lab no avanza o algo no queda claro, pregunta en el canal correspondiente.
* **Comparte tu avance.** Muestra lo que construiste, pide feedback y mira lo que están construyendo los demás.
* **Entérate primero.** Roadmaps nuevos, labs y actualizaciones de Tutor se anuncian en Discord.

<p align="center">
  <a href="https://discord.gg/ycy9zkUreX"><strong>→ Unirse al Discord de Z2H Academy</strong></a>
</p>

---

## Soporte

Para problemas relacionados con acceso, autenticación, configuración de Tutor, conexión con tu agente, Roadmaps o labs, contacta al administrador de Z2H Academy.

---

## Licencia

Tutor está destinado exclusivamente al uso por parte de estudiantes activos de Z2H Academy.

Consulta el archivo `LICENSE` incluido en el proyecto para conocer los términos completos de uso.

---

<p align="center">
  <sub>El agente ejecuta · Tutor conecta y orquesta · el harness dirige y valida</sub>
</p>

<p align="center">
  <a href="https://discord.gg/ycy9zkUreX"><img src="https://cdn.simpleicons.org/discord/5865F2" alt="Discord" width="20" height="20"> Únete a la comunidad en Discord</a>
</p>
