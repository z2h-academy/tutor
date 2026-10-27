[English](README.md) | **Español**

<p align="center">
  <img src="logo.svg" alt="TUTOR — Z2H Academy" width="520">
</p>

<p align="center">
  <strong>Deja de ver cursos. Construye con AI.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/stable-0.10.0-ffd300?style=flat-square" alt="stable 0.10.0">
  <img src="https://img.shields.io/badge/pre--release-0.10.2--rc.2-2f81f7?style=flat-square" alt="pre-release 0.10.2-rc.2">
  <img src="https://img.shields.io/badge/license-Proprietary-0b0b10?style=flat-square" alt="licencia propietaria">
  <img src="https://img.shields.io/badge/node-%3E%3D22-2fe08a?style=flat-square" alt="node 22 o superior">
  <a href="https://discord.gg/ycy9zkUreX"><img src="https://img.shields.io/badge/discord-%C3%BAnete-5865F2?style=flat-square&amp;logo=discord&amp;logoColor=white" alt="únete al Discord de Z2H Academy"></a>
</p>

<p align="center">
  <a href="#qué-es">qué es</a> ·
  <a href="#por-qué-tutor">por qué</a> ·
  <a href="#el-flujo">flujo</a> ·
  <a href="#contenido-roadmaps-y-proyectos">contenido</a> ·
  <a href="#quick-start">quick start</a> ·
  <a href="#qué-puede-hacer-tu-agente">capacidades</a> ·
  <a href="#modos-de-ejecución">modos</a> ·
  <a href="#troubleshooting">troubleshooting</a>
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

Tutor tampoco es el agente de IA. **El agente es quien habla contigo, razona y actúa en tu máquina.**

Y una cosa más que Tutor no es: un lugar donde el modelo te califica. **La academia valida cada paso.** El agente no decide si lo hiciste bien.

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

La teoría no es opcional. No puedes saltar directo al lab: sin la base teórica y un checkpoint aprobado, no se ejecuta ningún comando.

## Contenido: roadmaps y proyectos

Z2H Academy publica dos tipos de contenido, y TUTOR maneja ambos.

| Tipo de contenido | Estructura | Ejemplo |
|---|---|---|
| **Roadmap** | Niveles, y secciones dentro de cada nivel | `data-engineering` → `nivel-0` → `1-section` |
| **Proyecto** | Un recorrido único hecho de fases | `analytics-starter` → `fase-0`, `fase-1`, … |

Ambos se leen como unidades completas, no como páginas sueltas:

* Un **nivel** o una **fase** se enseña en tres etapas: base teórica, plan del lab y ejecución.
* Cada etapa cierra con evidencia antes de avanzar.
* En los proyectos el nivel es opcional: el proyecto mismo es la unidad.

Los roadmaps cubren data engineering, AI, DevOps, Python, PySpark y SQL. Los proyectos te llevan por una construcción completa, de la primera fase a la última.

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

Los agentes soportados incluyen **OpenCode**, **Codex** y **Claude Code**.

OpenCode es el cliente oficialmente soportado. **Tutor 0.10.x requiere OpenCode 2**: si todavía usas OpenCode 1, quédate en Tutor 0.8.0.

---

## Quick Start

### 1. Instalar nvm + Node.js (Linux)

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

> **Versiones correctas:** Node.js **22 o 24** (24 LTS recomendado). npm viene incluido con Node.js y no se instala por separado. No uses Node.js 20 o inferior — Tutor requiere funciones modernas de JavaScript.

### 2. Instalar OpenCode

Instalar el agente OpenCode con el instalador oficial:

```bash
curl -fsSL https://opencode.ai/install | bash
```

Verificar la instalación (reinicia la terminal primero si es necesario):

```bash
opencode --version   # debe mostrar 2.x
```

> Si el comando no se encuentra, agrega `~/.opencode/bin` a tu `PATH` o reinicia la terminal.

> **Requisito de versión:** Tutor 0.10.x requiere OpenCode 2. Si todavía usas OpenCode 1, quédate en Tutor 0.8.0.

### 3. Instalar Tutor

Instala la CLI de Tutor globalmente desde el release estable:

```bash
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

No necesitas configurar nada a mano: el siguiente paso deja todo listo.

Para fijar una versión específica, reemplaza `latest` por el tag:

```bash
npm install -g https://github.com/z2h-academy/tutor/releases/download/v0.10.0/z2h-academy-tutor-0.10.0.tgz
```

> **Canal pre-release.** Para probar la pre-release 0.10.x, instala el build rc directamente. Ten en cuenta que su asset puede cambiar antes de promoverse a stable:
>
> ```bash
> npm install -g https://github.com/z2h-academy/tutor/releases/download/v0.10.2-rc.2/z2h-academy-tutor-0.10.2-rc.2.tgz
> ```

### 4. Autenticarse

La autenticación se realiza una única vez:

```bash
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

Las credenciales locales se almacenan en `~/.config/z2h/tutor.env` con permisos `600`, de modo que únicamente tú puedas acceder al archivo.

### 5. Verificar la instalación

Desde OpenCode, pídele al agente:

```text
dime a qué roadmaps tengo acceso
```

Si te devuelve los roadmaps, niveles y secciones habilitados para tu cuenta, la instalación está completa.

También puedes verificar que la conexión esté activa:

```bash
opencode mcp list
```

Debería aparecer la conexión de Tutor como conectada:

```
●  ✓ tutor  connected
```

### 6. Actualizar a la última versión

La actualización es en dos pasos. Primero, instala la nueva versión:

```bash
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

Después, aplica la configuración en tu agente:

```bash
tutor setup
```

Reinicia OpenCode al terminar.

> Reinstalar el paquete por sí solo no actualiza tu configuración local: `tutor setup` es el paso que la deja al día. Es idempotente y no toca tus otros servidores MCP.

---

## Tutor Memory

**Tu progreso no se pierde: se recuerda.**

Tutor incluye **Tutor Memory**, la memoria de tu aprendizaje. Viene activada desde la instalación: sin cuentas, sin pasos extra.

* **Tu agente recuerda.** Dónde quedaste, qué decidiste y los resúmenes de tus sesiones anteriores. Nunca empiezas de cero.
* **Cada proyecto recuerda lo suyo.** La memoria es de tu proyecto, no de tu persona: cada repo tiene su propio historial.
* **Viaja contigo.** Tu progreso puede viajar dentro de tu repositorio: llévalo de tu PC a tu Codespace (o al revés) y continúa donde estabas.
* **Privada por diseño.** Se guarda en tu entorno de trabajo y no se mezcla con la de nadie más. Nada se envía al harness.

Pídeselo así:

| Lo que quieres | Frase de ejemplo |
|---|---|
| Retomar donde quedaste | *"¿dónde quedamos la última sesión?"* |
| Guardar tu avance | *"recuerda que terminé la sección 2 del nivel 0"* |
| Guardar una decisión | *"recuerda que decidimos usar Docker para los labs y por qué"* |
| Recuperar algo del pasado | *"¿qué habíamos decidido sobre el modelo de datos?"* |
| Cerrar con contexto | *"dame un resumen de la sesión para continuar mañana"* |
| Llevar tu progreso a otra máquina | *"guarda mi progreso en el repo para continuar desde el Codespace"* |

¿Prefieres la terminal? La memoria también se gestiona con la CLI:

```bash
tutor-memory status
tutor-memory save --project mi-proyecto --type decision --title "Usar Docker" --content "Elegido para los labs."
tutor-memory search --query "modelo de datos"
tutor-memory export
tutor-memory import
```

> Están disponibles `init`, `status`, `doctor`, `save`, `search`, `repair`, `export`, `import` y `migrate`. `tutor-memory --help` muestra el uso completo. La base vive en tu máquina, en `~/.local/share/z2h/tutor/memory.db`, con permisos `600`, y las etiquetas `<private>…</private>` se eliminan antes de guardar nada.

## Qué puede hacer tu agente

Tutor le enseña a tu agente cómo trabajar con la academia. No es una lista de comandos: entiende en qué punto estás y adapta la respuesta. Puedes preguntarle con tus palabras y él descubre el contenido real antes de responder.

**Descubrir tu contenido.** Pregúntale qué hay disponible y te muestra los roadmaps y proyectos con su estructura en vivo, sin catálogos fijos.

```text
lista los roadmaps
```

**Conocer el proyecto antes de empezar.** Te da el panorama, qué vas a aprender y cómo está organizado, sin que tengas que abrir los archivos.

```text
vamos a desarrollar el proyecto analytics-starter.
dame un resumen de lo que aprenderé.
```

```text
dame un resumen estratégico de la fase-0 de analytics-starter
```

**Avanzar en orden.** Si le pides el siguiente paso, retoma dónde quedaste y te indica qué sigue dentro del roadmap o del proyecto.

```text
¿qué sigue después de la fase-0?
```

**Estudiar una unidad completa.** Una fase de proyecto o un nivel de roadmap se enseña en tres etapas: base teórica, plan del lab y ejecución. No puedes saltear la teoría para ir directo al lab.

```text
empieza la fase-1 de analytics-starter
```

**Ejecutar tus labs.** En local o en un Codespace, en modo manual o automático.

```text
ejecuta el lab de analytics-starter en Codespaces
```

**Validar cada paso.** Contra los criterios de la academia, no contra la opinión del modelo.

```text
¿está bien como cargué los datos?
```

**Profundizar.** Sobre cualquier tema ya visto, puedes pedir ejemplos, aclaraciones o que te lo explique de otra forma.

```text
explícame otra vez el grano de la tabla de hechos con un ejemplo
```

**Diagnosticar cuando algo falla.** Reporta el error tal como aparece y Tutor busca la causa en lugar de adivinar.

```text
me sale este error al cargar los datos: <pega el error>
```

> Tutor trabaja solo con el material del curso y el estado de tu sesión. Si algo no está en los docs, te lo dice en lugar de inventarlo.

## Modos de ejecución

El modo se elige una vez, dentro del plan, y no se cambia a mitad de la unidad salvo que lo pidas.

| Modo | Qué pasa |
|---|---|
| **Manual** | El agente prepara los comandos y los ejecutas tú. Verifica el resultado contigo. |
| **Automático** | El agente ejecuta los pasos uno por uno y verifica cada uno. Los comandos destructivos igual piden confirmación explícita. |
| **Solo comando** | Insistes en un comando sin la teoría. Recibes la acción, el por qué en dos líneas y la evidencia esperada. El checkpoint queda pendiente, la unidad no se cierra y no cuenta como avance. |

En el modo solo comando se permite una sola acción de lab por turno, más el posicionamiento en el workspace y la activación de un entorno que el material ya declare. La preparación, la inspección y la verificación no se permiten en el mismo turno.

## Export local de teoría

Desde el MCP local puedes exportar la teoría de una unidad como documento:

```text
exporta la teoría de esta unidad
```

* Una unidad por vez; no existe "exportar todo".
* El renderer es fijo y la salida pasa por un sanitizer que bloquea términos internos.
* El estado del export se rastrea, así que un export editado nunca se sobrescribe sin preguntarte.

> El export es **solo local**. No está disponible en el harness hosted, así que no lo esperes de la versión web.

## Dos formas de usarlo

* **Local** — en tu terminal: instala Tutor, autentícate y abre tu agente. Funciona en tu PC, en un Codespace o en un container.
* **Web** — en el navegador: entra a [tutor.z2h-academy.com](https://tutor.z2h-academy.com), inicia sesión con GitHub y usa OpenCode con tu propio entorno en la nube.

> `tutor runtime` levanta el daemon detrás del modo web: arranca OpenCode en local y lo conecta con la academia. Normalmente no lo ejecutas a mano.

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
| Usas OpenCode 1 | Tutor 0.10.x requiere OpenCode 2. Actualiza OpenCode o quédate en Tutor 0.8.0. |

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
