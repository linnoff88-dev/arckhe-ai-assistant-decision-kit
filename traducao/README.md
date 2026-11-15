# traducao/ — versão em português (pt-BR) do kit

Tradução **nossa, não-oficial** de toda a documentação do *The AI Assistant Decision Kit* (Mark Kashef, MIT). Feita em 2026-08-25 a partir dos originais intactos em `../kit/` e `../origem/`.

- Os originais em inglês **continuam sendo a referência válida**; esta pasta existe para leitura e estudo em português.
- **Cross-link nos dois sentidos:** todo arquivo traduzido traz no topo (ou logo após o frontmatter) um cabeçalho linkando o original em `kit/` — "🌐 Tradução não-oficial… em caso de divergência, vale o original". A tabela abaixo também mapeia cada par. Os originais permanecem intocáveis, então o link reverso vive só neste lado.
- A estrutura espelha exatamente a do kit (mesmos nomes de arquivo), então referências cruzadas internas (ex.: `references/interview-engine.md`) continuam fazendo sentido.
- **Não instale a skill a partir daqui** — instale o original (`../kit/ai-assistant-system-advisor/`); o frontmatter traduzido pode não disparar o mesmo comportamento nas ferramentas.

## Índice de traduções

| tradução | original |
|---|---|
| [`START-HERE.md`](START-HERE.md) | `kit/START-HERE.md` |
| [`WEBSITE.md`](WEBSITE.md) | `kit/WEBSITE.md` |
| [`LICENSE-NOTA.md`](LICENSE-NOTA.md) | resumo em pt-BR — o texto legal oficial segue em inglês em `kit/LICENSE.md` |
| [`prompts/PASTE-INTO-ANY-AI.md`](prompts/PASTE-INTO-ANY-AI.md) | `kit/prompts/PASTE-INTO-ANY-AI.md` |
| [`website/OPEN-THE-AI-ASSISTANT-MAP.html`](website/OPEN-THE-AI-ASSISTANT-MAP.html) | `kit/website/OPEN-THE-AI-ASSISTANT-MAP.html` (página-redirect) |
| [`ai-assistant-system-advisor/SKILL.md`](ai-assistant-system-advisor/SKILL.md) | `kit/ai-assistant-system-advisor/SKILL.md` |
| [`ai-assistant-system-advisor/agents/openai.yaml`](ai-assistant-system-advisor/agents/openai.yaml) | `.../agents/openai.yaml` |
| [`ai-assistant-system-advisor/references/interview-engine.md`](ai-assistant-system-advisor/references/interview-engine.md) | `references/interview-engine.md` |
| [`ai-assistant-system-advisor/references/decision-model.md`](ai-assistant-system-advisor/references/decision-model.md) | `references/decision-model.md` |
| [`ai-assistant-system-advisor/references/research-protocol.md`](ai-assistant-system-advisor/references/research-protocol.md) | `references/research-protocol.md` |
| [`ai-assistant-system-advisor/references/output-contract.md`](ai-assistant-system-advisor/references/output-contract.md) | `references/output-contract.md` |
| [`ai-assistant-system-advisor/references/providers/grok-bot.md`](ai-assistant-system-advisor/references/providers/grok-bot.md) | `references/providers/grok-bot.md` |
| [`ai-assistant-system-advisor/references/providers/hermes-agent.md`](ai-assistant-system-advisor/references/providers/hermes-agent.md) | `references/providers/hermes-agent.md` |
| [`ai-assistant-system-advisor/references/providers/claude-cowork.md`](ai-assistant-system-advisor/references/providers/claude-cowork.md) | `references/providers/claude-cowork.md` |
| [`ai-assistant-system-advisor/references/providers/chatgpt-work.md`](ai-assistant-system-advisor/references/providers/chatgpt-work.md) | `references/providers/chatgpt-work.md` |
| [`ai-assistant-system-advisor/references/providers/openclaw.md`](ai-assistant-system-advisor/references/providers/openclaw.md) | `references/providers/openclaw.md` |
| [`ai-assistant-system-advisor/references/providers/owned-diy.md`](ai-assistant-system-advisor/references/providers/owned-diy.md) | `references/providers/owned-diy.md` |
| [`origem/README-origem.md`](origem/README-origem.md) | `origem/README-origem.md` (página do produto no repo de origem) |

## O que ficou de fora (de propósito)

- `origem/meta.json` e `origem/content.md` — dados brutos de plataforma (metadados Gumroad e cópia de marketing da página de vendas), sem valor de documentação.
- Texto legal de `kit/LICENSE.md` — licenças só valem no idioma original; veja o resumo em [`LICENSE-NOTA.md`](LICENSE-NOTA.md).
- `zips/` — binários.

## Glossário adotado

Termos técnicos mantidos em inglês, com tradução na primeira ocorrência quando ajuda:

| termo no original | tradução adotada |
|---|---|
| harness | harness (arcabouço de execução) |
| stay put | ficar onde está |
| managed assistant | assistente gerenciado |
| open-source runtime | runtime open-source |
| owned system / DIY | sistema próprio (DIY) |
| defaults vs ceiling | padrões de fábrica vs. teto alcançável |
| decision packet | pacote de decisão |
| research lock | lock de pesquisa |
| dossier | dossiê |
| switching cost / ledger | custo de troca / inventário de troca |
| reversible test | teste reversível |
| runner-up | runner-up (segundo colocado) |
| tier board | quadro de tiers |
| capability map | mapa de capacidades |
| trust boundary | fronteira de confiança |
| operator burden | carga operacional |

Nomes próprios de produtos (Grok Bot, Hermes Agent, Claude Cowork, ChatGPT Work, OpenClaw), ferramentas (`AskUserQuestion`, `request_user_input`) e identificadores/caminhos/comandos permanecem inalterados.

### Decisões pontuais dos tradutores

- *AI Assistant System Advisor* (persona/título em prosa) → "Assessor de Sistemas de Assistente de IA"; o identificador da skill segue sempre em inglês.
- Code spans retóricos ficaram em inglês com glosa fora do span quando útil (`stay put`, `OpenClaw remembers`, `Do not switch unless`…).
- *switching ledger* → "inventário de troca"; *Ordinary default* (coluna) → "Padrão comum"/"Padrão típico"; *secret redaction* → "mascaramento de segredos"; *specialist lanes* → "trilhas de especialista"; *rollout* e empréstimos consagrados (gateway, cron, sandbox, workspace, dry run, allowlist…) mantidos.
