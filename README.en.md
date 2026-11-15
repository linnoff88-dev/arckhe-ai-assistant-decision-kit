# AI Assistant Decision Kit

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

**Third-party** material, downloaded on 2026-08-24 for study. Helps you decide **which personal AI assistant model to adopt** — or whether to avoid switching platforms unnecessarily — instead of rebuilding the same assistant every time a new product comes out.

- **Author:** Mark Kashef
- **Source:** [`earlyaidopters/gumroad-resources`](https://github.com/earlyaidopters/gumroad-resources/tree/main/resources/the-ai-assistant-decision-kit)
- **Product:** https://markkashef.gumroad.com/l/ai-assistant-decision-kit (CAD$ 0+)
- **Video:** https://youtu.be/aBdMey9nqcM
- **Interactive map:** https://ai-assistant-house-map.markkashef.chatgpt.site/
- **License:** MIT — see `kit/LICENSE.md` (Portuguese summary: `traducao/LICENSE-NOTA.md`)

> **Rule for this repository:** the contents of `kit/`, `origem/`, and `zips/` are faithful copies of upstream and remain **untouched**. Our additions (this README and the entire `traducao/` folder) live outside those folders. See `CLAUDE.md`.


## 📖 User guide

Complete guide (landing page + walkthrough): **https://inematds.github.io/ai-assistant-decision-kit/guia/en/**

---

## Complete structure

```
README.md                      this file
CLAUDE.md                      project rules for agents
kit/                           complete unpacked package (upstream, untouched)
  START-HERE.md                where to start (in English)
  WEBSITE.md                   interactive map instructions
  prompts/PASTE-INTO-ANY-AI.md   the path that requires no installation: paste into any AI
  website/OPEN-THE-AI-ASSISTANT-MAP.html   redirect to the online map
  ai-assistant-system-advisor/   the installable skill (SKILL.md + references/ + agents/)
  LICENSE.md · WEBSITE.md
origem/                        Gumroad page metadata (upstream, untouched)
  README-origem.md             original product description
  content.md                   copy of the sales page
  meta.json                    raw metadata (price, files, permalink)
zips/                          the two original .zip files, untouched
traducao/                      OUR complete pt-BR translation (outside upstream)
  README.md                    translation index + adopted glossary
  START-HERE.md · WEBSITE.md · LICENSE-NOTA.md
  prompts/ · website/ · origem/
  ai-assistant-system-advisor/   fully translated skill (SKILL.md, agents/, references/, providers/)
```

## The two downloaded files

| zip | contents |
|---|---|
| `AI-Assistant-Decision-Kit.zip` (42 KB) | the complete kit — extracted into `kit/` |
| `AI-Assistant-System-Advisor-Skill.zip` (35 KB) | just the skill |

**Both include the same skill** — verified with `diff -rq`, byte-for-byte identical. That’s why we extracted only the complete kit; both original zip files are preserved in `zips/`.

## How to use

### 1. Without installing anything

Copy all of `kit/prompts/PASTE-INTO-ANY-AI.md` (or the Portuguese version in `traducao/prompts/PASTE-INTO-ANY-AI.md`) and paste it into Claude, ChatGPT, or Codex. The decision interview runs in the conversation.

### 2. As an installable skill

The `kit/ai-assistant-system-advisor/` folder is in Agent Skill format (frontmatter with `name` and `description`). To install:

```bash
ln -s ~/projetos/ai-assistant-decision-kit/kit/ai-assistant-system-advisor \
      ~/.claude/skills/ai-assistant-system-advisor        # Claude Code
# Codex: ~/.codex/skills/ai-assistant-system-advisor
```

Then ask: *"Use the AI Assistant System Advisor to help me decide which setup fits my real work."*

**Status: NOT installed** — installation is the user’s decision. Always install the **original in English**, not the translation (the translation is for reading).

### 3. Interactive map

Open https://ai-assistant-house-map.markkashef.chatgpt.site/ (or the redirect HTML in `kit/website/`). The local file is only 1,3 KB — it’s a redirect, not the page; the actual content requires internet access. The map covers the five highlighted assistants, architecture cuts, a draggable tier chart, and a combined capability map. Research frozen on 21/08/2026 (`kit/WEBSITE.md`).

## What the skill does

An evidence-oriented systems advisor that **interviews before recommending** and works in four modes:

| mode | question it answers |
|---|---|
| Full decision audit | "Which path is best for me?" (default when asked which assistant to choose) |
| Switching audit | "Is it worth moving from my current setup to X?" |
| Product deep dive | "How does assistant X work under the hood?" |
| Custom system blueprint | "What would a DIY architecture for my requirements look like?" |

### Method (five stages, one file per stage in `references/`)

1. **Adaptive interview** (`interview-engine.md`) — up to 2 rounds, max. 3 questions per round; uses `AskUserQuestion` in Claude Code, `request_user_input` in Codex, or a normal conversation. If the user doesn’t point to a real recurring failure, "stay where you are" becomes the leading hypothesis.
2. **Research** (`research-protocol.md`) — records date/time, opened URLs, releases, and inspected commits; without browsing, uses dated dossiers and warns that volatile facts need to be reverified.
3. **Decision model** (`decision-model.md`) — chooses the *operational path* before the brand: stay where you are → managed assistant → open-source runtime → custom system (DIY). Separately compares out-of-the-box defaults vs. achievable ceiling across 10 common layers (model/routing, runtime, files, tools/connectors, memory, skills, routines/triggers, interfaces, permissions/trust boundary, maintenance/backup).
4. **Dossiers** (`references/providers/`) — reads only those relevant to the mode; all six in the full audit.
5. **Decision package** (`output-contract.md`) — 11 required items, including: a direct verdict naming the path before the product, a diagnosis of what is failing today, a weighted fit table with evidence ratings, runner-up and reasons for exclusions, an inventory of what is kept/lost/rebuilt, a **reversible 30–60 minute test**, and a **seven-day pilot** with success and exit criteria.

Core philosophy: anti-hype. Switching because of social media buzz isn’t a reason; a cheap, reproducible feature in the current setup is a candidate for testing, not a reason to migrate; no one-way moves without a prior trial.

## Provider dossiers

Research frozen on **23/08/2026** — features, prices, limits, and availability change quickly; the skill rechecks first-party sources when browsing is available.

| dossier | type | focus |
|---|---|---|
| `grok-bot.md` | managed | xAI/X bot, integration with the X ecosystem |
| `hermes-agent.md` | open-source | exposed harness (loop, curated memory, skills, subagents, cron), multi-model; canonical repo NousResearch/hermes-agent, release v0.20.5 / v2026.8.19 |
| `claude-cowork.md` | managed | Anthropic collaborative work environment |
| `chatgpt-work.md` | managed | OpenAI offering for work/business connectors |
| `openclaw.md` | open-source | self-hosted open-source runtime |
| `owned-diy.md` | DIY route | model-agnostic custom architecture |

## Portuguese translation

All documentation has been translated into pt-BR in **[`traducao/`](traducao/README.md)**, mirroring the kit’s structure (same file names). It contains the complete index, adopted glossary (harness, research lock, decision package…) and documented exceptions: `meta.json`/`content.md` (raw platform data) and the license legal text remain untranslated.

## License

MIT © 2026 Mark Kashef — guide, prompt, and skill. Official English text: `kit/LICENSE.md`. Unofficial summary: `traducao/LICENSE-NOTA.md`.
