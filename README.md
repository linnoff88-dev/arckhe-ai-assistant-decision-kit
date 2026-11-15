# AI Assistant Decision Kit

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

Material de **terceiro**, baixado em 2026-08-24 para estudo. Ajuda a decidir **qual modelo de assistente de IA pessoal adotar** â€” ou a nÃ£o trocar de plataforma Ã  toa â€” em vez de reconstruir o mesmo assistente cada vez que sai um produto novo.

- **Autor:** Mark Kashef
- **Origem:** [`earlyaidopters/gumroad-resources`](https://github.com/earlyaidopters/gumroad-resources/tree/main/resources/the-ai-assistant-decision-kit)
- **Produto:** https://markkashef.gumroad.com/l/ai-assistant-decision-kit (CAD$ 0+)
- **VÃ­deo:** https://youtu.be/aBdMey9nqcM
- **Mapa interativo:** https://ai-assistant-house-map.markkashef.chatgpt.site/
- **LicenÃ§a:** MIT â€” ver `kit/LICENSE.md` (resumo em portuguÃªs: `traducao/LICENSE-NOTA.md`)

> **Regra deste repositÃ³rio:** o conteÃºdo de `kit/`, `origem/` e `zips/` Ã© cÃ³pia fiel do upstream e fica **intacto**. Nossas adiÃ§Ãµes (este README e toda a pasta `traducao/`) vivem fora dessas pastas. Ver `CLAUDE.md`.


## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/ai-assistant-decision-kit/guia/**

---

## Estrutura completa

```
README.md                      este arquivo
CLAUDE.md                      regras do projeto para agentes
kit/                           pacote completo, descompactado (upstream, intacto)
  START-HERE.md                por onde comeÃ§ar (em inglÃªs)
  WEBSITE.md                   instruÃ§Ãµes do mapa interativo
  prompts/PASTE-INTO-ANY-AI.md   o caminho sem instalar nada: cola em qualquer IA
  website/OPEN-THE-AI-ASSISTANT-MAP.html   redirect para o mapa online
  ai-assistant-system-advisor/   a skill instalÃ¡vel (SKILL.md + references/ + agents/)
  LICENSE.md Â· WEBSITE.md
origem/                        metadados da pÃ¡gina Gumroad (upstream, intacto)
  README-origem.md             descriÃ§Ã£o original do produto
  content.md                   cÃ³pia da pÃ¡gina de vendas
  meta.json                    metadados brutos (preÃ§o, arquivos, permalink)
zips/                          os dois .zip originais, intactos
traducao/                      NOSSA traduÃ§Ã£o completa em pt-BR (fora do upstream)
  README.md                    Ã­ndice das traduÃ§Ãµes + glossÃ¡rio adotado
  START-HERE.md Â· WEBSITE.md Â· LICENSE-NOTA.md
  prompts/ Â· website/ Â· origem/
  ai-assistant-system-advisor/   skill inteira traduzida (SKILL.md, agents/, references/, providers/)
```

## Os dois arquivos baixados

| zip | conteÃºdo |
|---|---|
| `AI-Assistant-Decision-Kit.zip` (42 KB) | o kit completo â€” Ã© o que estÃ¡ extraÃ­do em `kit/` |
| `AI-Assistant-System-Advisor-Skill.zip` (35 KB) | sÃ³ a skill |

**Os dois trazem a mesma skill** â€” conferido com `diff -rq`, byte a byte idÃªntica. Por isso extraÃ­mos sÃ³ o kit completo; os dois zips originais continuam preservados em `zips/`.

## Como usar

### 1. Sem instalar nada

Copie `kit/prompts/PASTE-INTO-ANY-AI.md` inteiro (ou a versÃ£o em portuguÃªs em `traducao/prompts/PASTE-INTO-ANY-AI.md`) e cole no Claude, ChatGPT ou Codex. A entrevista de decisÃ£o roda na conversa.

### 2. Como skill instalÃ¡vel

A pasta `kit/ai-assistant-system-advisor/` estÃ¡ no formato Agent Skill (frontmatter com `name` e `description`). Para instalar:

```bash
ln -s ~/projetos/ai-assistant-decision-kit/kit/ai-assistant-system-advisor \
      ~/.claude/skills/ai-assistant-system-advisor        # Claude Code
# Codex: ~/.codex/skills/ai-assistant-system-advisor
```

Depois peÃ§a: *"Use the AI Assistant System Advisor to help me decide which setup fits my real work."*

**Estado: NÃƒO instalada** â€” instalar Ã© decisÃ£o do usuÃ¡rio. Instale sempre o **original em inglÃªs**, nÃ£o a traduÃ§Ã£o (a traduÃ§Ã£o Ã© para leitura).

### 3. Mapa interativo

Abra https://ai-assistant-house-map.markkashef.chatgpt.site/ (ou o HTML de redirect em `kit/website/`). O arquivo local tem sÃ³ 1,3 KB â€” Ã© um redirect, nÃ£o a pÃ¡gina; o conteÃºdo real depende de internet. O mapa cobre os cinco assistentes destacados, cortes de arquitetura, quadro de tiers arrastÃ¡vel e mapa combinado de capacidades. Pesquisa travada em 21/08/2026 (`kit/WEBSITE.md`).

## O que a skill faz

Um consultor de sistemas orientado a evidÃªncia que **entrevista antes de recomendar** e trabalha em quatro modos:

| modo | pergunta que responde |
|---|---|
| Auditoria completa de decisÃ£o | "Qual caminho Ã© melhor para mim?" (padrÃ£o quando se pergunta qual assistente escolher) |
| Auditoria de troca | "Vale a pena sair do meu setup atual para o X?" |
| Mergulho no produto | "Como funciona por dentro o assistente X?" |
| Blueprint de sistema prÃ³prio | "Como seria uma arquitetura DIY para meus requisitos?" |

### MÃ©todo (cinco etapas, um arquivo por etapa em `references/`)

1. **Entrevista adaptativa** (`interview-engine.md`) â€” atÃ© 2 rodadas, mÃ¡x. 3 perguntas por rodada; usa `AskUserQuestion` no Claude Code, `request_user_input` no Codex ou conversa normal. Se o usuÃ¡rio nÃ£o aponta uma falha recorrente real, "ficar onde estÃ¡" vira a hipÃ³tese principal.
2. **Pesquisa** (`research-protocol.md`) â€” registra data/hora, URLs abertas, releases e commits inspecionados; sem navegaÃ§Ã£o, usa os dossiÃªs datados e avisa que fatos volÃ¡teis precisam reverificaÃ§Ã£o.
3. **Modelo de decisÃ£o** (`decision-model.md`) â€” escolhe o *caminho operacional* antes da marca: ficar onde estÃ¡ â†’ assistente gerenciado â†’ runtime open-source â†’ sistema prÃ³prio (DIY). Compara separadamente padrÃµes de fÃ¡brica vs. teto alcanÃ§Ã¡vel, sobre 10 camadas comuns (modelo/roteamento, runtime, arquivos, ferramentas/conectores, memÃ³ria, skills, rotinas/triggers, interfaces, permissÃµes/fronteira de confianÃ§a, manutenÃ§Ã£o/backup).
4. **DossiÃªs** (`references/providers/`) â€” lÃª apenas os relevantes ao modo; todos os seis na auditoria completa.
5. **Pacote de decisÃ£o** (`output-contract.md`) â€” 11 itens obrigatÃ³rios, entre eles: veredito direto nomeando o caminho antes do produto, diagnÃ³stico do que falha hoje, tabela de aderÃªncia ponderada com notas de evidÃªncia, runner-up e motivos das exclusÃµes, inventÃ¡rio do que se mantÃ©m/perde/reconstrÃ³i, **teste reversÃ­vel de 30â€“60 min** e **piloto de sete dias** com critÃ©rios de sucesso e saÃ­da.

Filosofia central: anti-hype. Trocar por novidade de rede social nÃ£o Ã© motivo; feature reproduzÃ­vel barata no setup atual Ã© candidato a teste, nÃ£o razÃ£o para migrar; nenhum movimento unidirecional sem ensaio prÃ©vio.

## DossiÃªs de provedores

Pesquisa travada em **23/08/2026** â€” features, preÃ§os, limites e disponibilidade mudam rÃ¡pido; a skill reverifica fontes de primeira parte quando hÃ¡ navegaÃ§Ã£o disponÃ­vel.

| dossiÃª | tipo | foco |
|---|---|---|
| `grok-bot.md` | gerenciado | bot da xAI/X, integraÃ§Ã£o com ecossistema X |
| `hermes-agent.md` | open-source | harness exposto (loop, memÃ³ria curada, skills, subagentes, cron), multi-modelo; repo canÃ´nico NousResearch/hermes-agent, release v0.20.5 / v2026.8.19 |
| `claude-cowork.md` | gerenciado | ambiente Anthropic de trabalho colaborativo |
| `chatgpt-work.md` | gerenciado | oferta OpenAI para trabalho/conectores corporativos |
| `openclaw.md` | open-source | runtime open-source self-hosted |
| `owned-diy.md` | rota DIY | arquitetura prÃ³pria model-agnostic |

## TraduÃ§Ã£o em portuguÃªs

Toda a documentaÃ§Ã£o foi traduzida para pt-BR em **[`traducao/`](traducao/README.md)**, espelhando a estrutura do kit (mesmos nomes de arquivo). LÃ¡ estÃ£o o Ã­ndice completo, o glossÃ¡rio adotado (harness, lock de pesquisa, pacote de decisÃ£oâ€¦) e as exceÃ§Ãµes documentadas: `meta.json`/`content.md` (dados brutos de plataforma) e o texto legal da licenÃ§a permanecem sem traduÃ§Ã£o.

## LicenÃ§a

MIT Â© 2026 Mark Kashef â€” guia, prompt e skill. Texto oficial em inglÃªs: `kit/LICENSE.md`. Resumo nÃ£o-oficial: `traducao/LICENSE-NOTA.md`.

---

Projeto adaptado da comunidade INEMA TDS - Marca Arckhe