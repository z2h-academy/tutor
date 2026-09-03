# Tutor — El harness de laboratorios de Z2H Academy

**Tutor** es el **harness de Z2H Academy** para ejecutar y acompañar los labs de nuestros Roadmaps desde el entorno local del estudiante.

Tutor conecta los agentes de terminal —como OpenCode, Codex o Claude Code— con la infraestructura de aprendizaje de Z2H Academy, proporcionando el contexto, las herramientas y las capacidades necesarias para trabajar con nuestros Roadmaps, Developer Docs y labs.

Tutor **no es un chatbot ni el agente de IA**. El agente es quien conversa con el estudiante, razona y ejecuta acciones en su máquina.

**Tutor es el harness que conecta al agente con Z2H Academy.**

A través de MCP, Tutor permite al agente descubrir Roadmaps, consultar Developer Docs, seguir el flujo de estudio, ejecutar labs y utilizar las capacidades de validación disponibles en la plataforma.

La arquitectura separa las responsabilidades:

* **Agente:** conversa con el estudiante, razona y ejecuta acciones en su entorno.
* **Tutor:** conecta al agente con Z2H Academy y le proporciona las herramientas y el contexto necesarios.
* **Harness server-side:** dirige el flujo pedagógico, mantiene el estado y valida el progreso.
* **Developer Docs:** contienen el conocimiento, las instrucciones y los criterios específicos de cada sección y lab.
* **Entorno del estudiante:** es donde el agente ejecuta los labs y realiza el trabajo práctico.

En términos simples:

**El agente ejecuta.
Tutor conecta y orquesta.
El Harness dirige y valida.
Los Developer Docs contienen el conocimiento.**

---

## ¿Por qué un Harness?

Un agente de IA puede ejecutar comandos, modificar archivos y resolver problemas en una máquina, pero no conoce por sí mismo la estructura pedagógica de Z2H Academy.

Tampoco debería ser responsable de decidir qué Roadmap corresponde, qué sección sigue, cuál es el estado de un lab o si un paso fue completado correctamente.

Esa responsabilidad pertenece al **Harness**.

Tutor permite separar la inteligencia del agente de la lógica de aprendizaje de la plataforma:

* El **agente** se ocupa de conversar con el estudiante, razonar y trabajar en su entorno.
* El **Harness** conecta ese trabajo con la experiencia de aprendizaje de Z2H Academy.
* La **plataforma** mantiene la lógica pedagógica, el estado y la validación.

De esta manera, el agente puede ser reemplazado —OpenCode, Codex, Claude Code u otros clientes compatibles— sin que la lógica de aprendizaje tenga que depender de un modelo específico.

---

## Tutor + Harness server-side

Tutor forma parte de una arquitectura distribuida entre el entorno del estudiante y la infraestructura de Z2H Academy.

### Tutor: el Harness local

Tutor corre en el entorno del estudiante y expone las capacidades de Z2H Academy al agente mediante MCP.

Entre otras cosas, se encarga de:

* registrar y configurar el MCP server;
* gestionar la autenticación local;
* proporcionar las herramientas que utiliza el agente;
* obtener información de los Developer Docs;
* interactuar con los servicios de Z2H Academy;
* preparar y ejecutar los labs en el entorno local;
* conectar las acciones locales con el Harness server-side.

Tutor no necesita contener toda la lógica de la academia. Su función es proporcionar al agente una interfaz para acceder a ella.

### Harness server-side: dirección y validación

El Harness server-side vive en la infraestructura de Z2H Academy.

Es responsable de la lógica que no debería depender del modelo de IA ni de la máquina del estudiante.

El servidor:

* conoce los Roadmaps disponibles;
* conoce sus niveles y secciones;
* conoce los labs asociados;
* mantiene el estado de los labs;
* define el flujo pedagógico;
* controla qué pasos corresponden en cada momento;
* valida los pasos realizados;
* mantiene la lógica de progreso;
* proporciona una fuente de verdad independiente del agente.

Esto es especialmente importante para la validación.

**El agente no decide por sí mismo si un paso fue completado correctamente.**

Cuando una acción requiere validación, esta se realiza utilizando la lógica definida por Z2H Academy en el Harness server-side.

---

## Developer Docs

Los **Developer Docs** son la fuente de conocimiento técnico de cada sección del Roadmap.

Contienen la información necesaria para entender y ejecutar los labs:

* contexto;
* conceptos;
* instrucciones;
* pasos;
* comandos;
* configuración;
* criterios;
* información específica del entorno;
* instrucciones para resolver problemas.

Tutor permite que el agente consulte esta información cuando la necesita.

Esto establece una separación clara entre **conocimiento, orquestación, ejecución y validación**:

* **Developer Docs:** contienen el conocimiento y las instrucciones.
* **Tutor:** expone ese conocimiento y las capacidades de la plataforma al agente.
* **Harness server-side:** dirige el flujo y valida el progreso.
* **Agente:** utiliza la información, conversa con el estudiante y ejecuta acciones.
* **Entorno del estudiante:** contiene el trabajo práctico y los labs.

---

## La experiencia AI-First

El objetivo de Tutor no es simplemente agregar un MCP server.

La intención es cambiar la forma en que el estudiante interactúa con Z2H Academy.

Tradicionalmente, el flujo podía ser:

**Roadmap → Developer Docs → Terminal → Lab → Documentación → Terminal**

Con Tutor, el flujo se convierte en:

**Roadmap → Agente → Tutor → Lab → Validación**

La experiencia ocurre desde la terminal del estudiante, mientras Tutor conecta al agente con la infraestructura de aprendizaje.

El flujo puede ser:

1. El estudiante selecciona un Roadmap.
2. El agente descubre el contenido disponible mediante Tutor.
3. Consulta el Developer Doc correspondiente.
4. Explica qué debe realizarse.
5. Ejecuta las acciones necesarias en el entorno.
6. Si algo falla, analiza el problema y ayuda a corregirlo.
7. Tutor comunica las acciones relevantes con la plataforma.
8. El Harness server-side valida el progreso cuando corresponde.
9. El agente continúa con el siguiente paso.

El resultado es una experiencia en la que **el agente se convierte en la interfaz de aprendizaje**, mientras que la estructura pedagógica y la validación continúan bajo el control de Z2H Academy.

---

## ¿Para quién es?

Tutor está disponible para **estudiantes activos de Z2H Academy** que quieran ejecutar los labs de los Roadmaps de forma guiada mediante un agente de terminal.

Puede utilizarse en:

* una PC;
* un Codespace;
* un container;
* cualquier entorno compatible con los requisitos de Tutor.

El acceso está controlado mediante la whitelist de Z2H Academy.

Si el email asociado a la cuenta de GitHub está habilitado, el estudiante puede autenticarse y comenzar a utilizar Tutor.

---

## Requisitos

Antes de instalar Tutor se necesita:

* **Node.js ≥ 20**, instalado mediante nvm o directamente.
* **Una cuenta de GitHub** cuyo email esté incluido en la whitelist de Z2H Academy.
* **Un agente de terminal con soporte MCP**.

Los agentes soportados incluyen:

* **OpenCode**
* **Codex**
* **Claude Code**

OpenCode es actualmente el cliente oficialmente soportado.

---

## Quick Start

### 1. Instalar Tutor

Instalar el paquete globalmente:

```
npm install -g @z2h-academy/tutor
```

Durante la instalación, el `postinstall` registra automáticamente el MCP server `tutor-local` en OpenCode.

No es necesario realizar una configuración manual del MCP.

---

### 2. Autenticarse

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

---

### 3. Verificar la instalación

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

Debería aparecer algo similar a:

```
● ✓ tutor-local connected
```

---

## Skills incluidos

Tutor instala una serie de **skills** que ayudan al agente a utilizar correctamente sus capacidades:

| Skill                   | Función                                                                                         |
| ----------------------- | ----------------------------------------------------------------------------------------------- |
| `tutor-discover`        | Descubre y lista los Roadmaps y niveles disponibles.                                            |
| `tutor-read-section`    | Consulta el Developer Doc de una sección mediante `tutor_get_section`.                          |
| `tutor-study-path`      | Ayuda a seguir el orden secuencial de estudio recomendado.                                      |
| `tutor-explain-section` | Ayuda al agente a explicar y resumir el contenido de una sección cargada.                       |
| `tutor-run-local`       | Permite trabajar con los labs en local, en modo manual o automático, utilizando `/workspaces/`. |
| `tutor-debug`           | Ayuda a diagnosticar problemas relacionados con Tutor, MCP o el entorno del agente.             |

Las skills **no contienen la lógica completa de la academia**.

Su función es ayudar al agente a utilizar correctamente las capacidades de Tutor.

El conocimiento específico de cada Roadmap permanece en los Developer Docs, mientras que la lógica pedagógica, el estado y la validación permanecen en la infraestructura de Z2H Academy.

---

## Arquitectura

La arquitectura completa puede resumirse así:

```
Z2H Academy

     │
     ├───────────────────────┐
     │                       │
Developer Docs         Harness Server
     │                       │
     │                dirige · mantiene
     │                 estado · valida
     │                       │
     └───────────┬───────────┘
                 │
            Tutor Harness
                 │
                MCP
                 │
      ┌──────────▼──────────┐
      │       Agente        │
      │ OpenCode / Codex /  │
      │    Claude Code      │
      └──────────┬──────────┘
                 │
            ejecuta en
                 │
      ┌──────────▼──────────┐
      │    Entorno local    │
      │   PC / Codespace /  │
      │      Container      │
      └──────────┬──────────┘
                 │
            ┌────▼────┐
            │   Labs  │
            └─────────┘
```

La idea fundamental es mantener una separación clara:

**El agente razona y ejecuta.**

**Tutor conecta y orquesta.**

**El Harness server-side dirige y valida.**

**Los Developer Docs contienen el conocimiento.**

---

## Troubleshooting

| Problema                                | Solución                                                                                                            |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `email not in pre_enrollment whitelist` | El email no está habilitado. Contactar al administrador de Z2H Academy.                                             |
| `grant user:email scope`                | Verificar que se haya autorizado el scope `user:email` durante el GitHub Device Flow.                               |
| `AccessDenied` al leer contenido        | La service account asociada al usuario puede haber sido revocada. Ejecutar `tutor login` nuevamente.                |
| El MCP no aparece en OpenCode           | Verificar que Tutor esté instalado correctamente, comprobar la ruta del binario y reiniciar OpenCode.               |
| `no email available`                    | GitHub no está proporcionando un email para la cuenta. Verificar la configuración de emails de la cuenta de GitHub. |

---

## Acceso

Tutor es una funcionalidad de acceso restringido para **estudiantes activos de Z2H Academy**.

Si el email no está incluido en la whitelist, la autenticación será rechazada.

En ese caso, contactar al administrador de Z2H Academy para solicitar acceso.

---

## Soporte

Para problemas relacionados con:

* acceso;
* whitelist;
* autenticación;
* configuración de Tutor;
* conexión MCP;
* Roadmaps;
* labs;
* funcionamiento del Harness;

contactar al administrador de Z2H Academy.

---

## Licencia

Tutor está destinado exclusivamente al uso por parte de estudiantes activos de Z2H Academy.

Consultar el archivo `LICENSE` incluido en el proyecto para conocer los términos completos de uso.

---

## Z2H Academy AI-First

Tutor es una pieza fundamental de la experiencia **AI-First de Z2H Academy**.

Los **Developer Docs** contienen el conocimiento.

El **Harness server-side** mantiene la lógica pedagógica, el estado y la validación.

**Tutor** conecta esa infraestructura con el agente.

El **agente** conversa con el estudiante, razona y ejecuta el trabajo en su entorno.

Y el estudiante aprende haciendo.

**El agente ejecuta.**

**Tutor conecta y orquesta.**

**El Harness dirige y valida.**

**Y el estudiante aprende haciendo.**
