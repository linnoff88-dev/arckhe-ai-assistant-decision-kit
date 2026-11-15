# AI Assistant Decision Kit

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

Material de **terceros**, descargado en 2026-08-24 para su estudio. Ayuda a decidir **qué modelo de asistente personal de IA adoptar** — o a no cambiar de plataforma sin motivo — en lugar de reconstruir el mismo asistente cada vez que sale un producto nuevo.

- **Autor:** Mark Kashef
- **Origen:** [`earlyaidopters/gumroad-resources`](https://github.com/earlyaidopters/gumroad-resources/tree/main/resources/the-ai-assistant-decision-kit)
- **Producto:** https://markkashef.gumroad.com/l/ai-assistant-decision-kit (CAD$ 0+)
- **Video:** https://youtu.be/aBdMey9nqcM
- **Mapa interactivo:** https://ai-assistant-house-map.markkashef.chatgpt.site/
- **Licencia:** MIT — ver `kit/LICENSE.md` (resumen en portugués: `traducao/LICENSE-NOTA.md`)

> **Regla de este repositorio:** el contenido de `kit/`, `origem/` y `zips/` es una copia fiel del upstream y permanece **intacto**. Nuestras adiciones (este README y toda la carpeta `traducao/`) están fuera de esas carpetas. Ver `CLAUDE.md`.


## 📖 Guía de uso

Guía completa (landing + paso a paso): **https://inematds.github.io/ai-assistant-decision-kit/guia/es/**

---

## Estructura completa

```
README.md                      este archivo
CLAUDE.md                      reglas del proyecto para agentes
kit/                           paquete completo, descomprimido (upstream, intacto)
  START-HERE.md                por dónde empezar (en inglés)
  WEBSITE.md                   instrucciones del mapa interactivo
  prompts/PASTE-INTO-ANY-AI.md   la opción sin instalar nada: pégalo en cualquier IA
  website/OPEN-THE-AI-ASSISTANT-MAP.html   redirección al mapa en línea
  ai-assistant-system-advisor/   la skill instalable (SKILL.md + references/ + agents/)
  LICENSE.md · WEBSITE.md
origem/                        metadatos de la página de Gumroad (upstream, intactos)
  README-origem.md             descripción original del producto
  content.md                   copia de la página de ventas
  meta.json                    metadatos sin procesar (precio, archivos, permalink)
zips/                          los dos archivos .zip originales, intactos
traducao/                      NUESTRA traducción completa a pt-BR (fuera del upstream)
  README.md                    índice de las traducciones + glosario adoptado
  START-HERE.md · WEBSITE.md · LICENSE-NOTA.md
  prompts/ · website/ · origem/
  ai-assistant-system-advisor/   skill completa traducida (SKILL.md, agents/, references/, providers/)
```

## Los dos archivos descargados

| zip | contenido |
|---|---|
| `AI-Assistant-Decision-Kit.zip` (42 KB) | el kit completo — es el que está extraído en `kit/` |
| `AI-Assistant-System-Advisor-Skill.zip` (35 KB) | solo la skill |

**Ambos incluyen la misma skill** — verificado con `diff -rq`, idénticas byte a byte. Por eso extrajimos solo el kit completo; los dos archivos .zip originales siguen preservados en `zips/`.

## Cómo usarlo

### 1. Sin instalar nada

Copia el archivo completo `kit/prompts/PASTE-INTO-ANY-AI.md` (o la versión en portugués en `traducao/prompts/PASTE-INTO-ANY-AI.md`) y pégalo en Claude, ChatGPT o Codex. La entrevista de decisión se realiza en la conversación.

### 2. Como skill instalable

La carpeta `kit/ai-assistant-system-advisor/` tiene el formato Agent Skill (frontmatter con `name` y `description`). Para instalar:

```bash
ln -s ~/projetos/ai-assistant-decision-kit/kit/ai-assistant-system-advisor \
      ~/.claude/skills/ai-assistant-system-advisor        # Claude Code
# Codex: ~/.codex/skills/ai-assistant-system-advisor
```

Después, pide: *"Use the AI Assistant System Advisor to help me decide which setup fits my real work."*

**Estado: NO instalada** — instalarla es decisión del usuario. Instala siempre la **versión original en inglés**, no la traducción (la traducción es para lectura).

### 3. Mapa interactivo

Abre https://ai-assistant-house-map.markkashef.chatgpt.site/ (o el HTML de redirección en `kit/website/`). El archivo local tiene solo 1,3 KB — es una redirección, no la página; el contenido real depende de internet. El mapa cubre los cinco asistentes destacados, cortes de arquitectura, un cuadro de tiers arrastrable y un mapa combinado de capacidades. Investigación congelada el 21/08/2026 (`kit/WEBSITE.md`).

## Qué hace la skill

Un consultor de sistemas orientado a la evidencia que **hace una entrevista antes de recomendar** y trabaja en cuatro modos:

| modo | pregunta que responde |
|---|---|
| Auditoría completa de decisión | "¿Qué camino es mejor para mí?" (predeterminado cuando se pregunta qué asistente elegir) |
| Auditoría de cambio | "¿Vale la pena dejar mi configuración actual para pasar a X?" |
| Análisis del producto | "¿Cómo funciona internamente el asistente X?" |
| Blueprint de sistema propio | "¿Cómo sería una arquitectura DIY para mis requisitos?" |

### Método (cinco etapas, un archivo por etapa en `references/`)

1. **Entrevista adaptativa** (`interview-engine.md`) — hasta 2 rondas, máx. 3 preguntas por ronda; usa `AskUserQuestion` en Claude Code, `request_user_input` en Codex o una conversación normal. Si el usuario no señala un problema recurrente real, "quedarse donde está" se convierte en la hipótesis principal.
2. **Investigación** (`research-protocol.md`) — registra fecha y hora, URLs abiertas, releases y commits inspeccionados; sin navegación, usa los expedientes fechados y avisa que los datos volátiles deben volver a verificarse.
3. **Modelo de decisión** (`decision-model.md`) — elige el *camino operativo* antes que la marca: quedarse donde está → asistente administrado → runtime de código abierto → sistema propio (DIY). Compara por separado los valores predeterminados de fábrica con el potencial máximo, en 10 capas comunes (modelo/enrutamiento, runtime, archivos, herramientas/conectores, memoria, skills, rutinas/triggers, interfaces, permisos/límites de confianza, mantenimiento/respaldo).
4. **Expedientes** (`references/providers/`) — lee solo los pertinentes al modo; los seis en la auditoría completa.
5. **Paquete de decisión** (`output-contract.md`) — 11 elementos obligatorios, entre ellos: veredicto directo que nombra el camino antes que el producto, diagnóstico de lo que falla hoy, tabla de adecuación ponderada con notas de evidencia, segunda opción y motivos de exclusión, inventario de lo que se conserva/pierde/reconstruye, **prueba reversible de 30–60 min** y **piloto de siete días** con criterios de éxito y salida.

Filosofía central: anti-hype. Cambiar por una novedad de redes sociales no es motivo; una función reproducible y barata en la configuración actual es candidata a prueba, no una razón para migrar; ningún cambio unidireccional sin una prueba previa.

## Expedientes de proveedores

Investigación congelada el **23/08/2026** — las funciones, los precios, los límites y la disponibilidad cambian rápidamente; la skill vuelve a verificar fuentes primarias cuando hay navegación disponible.

| expediente | tipo | enfoque |
|---|---|---|
| `grok-bot.md` | administrado | bot de xAI/X, integración con el ecosistema X |
| `hermes-agent.md` | código abierto | harness expuesto (bucle, memoria curada, skills, subagentes, cron), multimodelo; repo canónico NousResearch/hermes-agent, release v0.20.5 / v2026.8.19 |
| `claude-cowork.md` | administrado | entorno de trabajo colaborativo de Anthropic |
| `chatgpt-work.md` | administrado | oferta de OpenAI para trabajo/conectores empresariales |
| `openclaw.md` | código abierto | runtime de código abierto autoalojado |
| `owned-diy.md` | ruta DIY | arquitectura propia independiente del modelo |

## Traducción al portugués

Toda la documentación se tradujo a pt-BR en **[`traducao/`](traducao/README.md)**, siguiendo la estructura del kit (mismos nombres de archivo). Allí están el índice completo, el glosario adoptado (harness, bloqueo de investigación, paquete de decisión…) y las excepciones documentadas: `meta.json`/`content.md` (datos sin procesar de la plataforma) y el texto legal de la licencia permanecen sin traducir.

## Licencia

MIT © 2026 Mark Kashef — guía, prompt y skill. Texto oficial en inglés: `kit/LICENSE.md`. Resumen no oficial: `traducao/LICENSE-NOTA.md`.
