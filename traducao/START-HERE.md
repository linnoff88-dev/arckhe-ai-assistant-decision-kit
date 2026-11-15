> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`START-HERE.md`](../kit/START-HERE.md) — em caso de divergência, vale o original.

# Kit de Decisão de Assistente de IA

Você não precisa instalar nada para aproveitar este kit.

## 1. Abra a comparação interativa

Use o mapa visual completo aqui:

https://ai-assistant-house-map.markkashef.chatgpt.site/

Você também pode abrir `website/OPEN-THE-AI-ASSISTANT-MAP.html` nesta pasta.

O mapa inclui os cinco assistentes em destaque, cortes da arquitetura, visões do harness (arcabouço de execução), um quadro de tiers arrastável e um mapa de capacidades combinado.

## 2. Execute a auditoria de decisão baseada em pesquisa

A opção mais fácil é `prompts/PASTE-INTO-ANY-AI.md`. Copie todo o conteúdo desse arquivo no ChatGPT, Claude, Codex ou outro assistente capaz.

Se a sua ferramenta de IA suportar skills, instale a pasta completa:

```text
ai-assistant-system-advisor/
```

Locais comuns:

- Codex: `~/.codex/skills/ai-assistant-system-advisor/`
- Claude Code: `~/.claude/skills/ai-assistant-system-advisor/`

Depois, peça:

```text
Use the AI Assistant System Advisor to help me decide which setup fits my real work.
```

O advisor usará a interface nativa de perguntas quando a sua IA oferecer uma. No Claude Code ele chama `AskUserQuestion`. No Codex ele usa `request_user_input` quando disponível. No ChatGPT ou em outro chat, ele faz as mesmas perguntas em formato conversacional e aguarda as suas respostas.

Ele vai então pesquisar os produtos atuais em documentação de primeira parte e repositórios canônicos, pontuá-los de acordo com os seus requisitos, separar padrões de fábrica de tetos alcançáveis, explicar o runner-up (segundo colocado) e cada rejeição relevante, fazer o levantamento dos custos de troca e entregar a você tanto um teste reversível quanto um piloto de sete dias.

Você também pode pedir um destes modos mais específicos:

- `Audit whether I should leave my current setup for Hermes Agent.`
- `Give me a current harness-level deep dive on OpenClaw.`
- `Compare Claude Cowork and ChatGPT Work for my actual workflows.`
- `Turn my requirements into a model-agnostic DIY assistant blueprint.`

## Importante

O objetivo não é convencê-lo a trocar. Se o seu setup atual já dá conta do trabalho que importa, `stay put` é um resultado de primeira classe.

Os dossiês incluídos refletem pesquisa travada em 23 de agosto de 2026 e incluem releases atuais dos repositórios, arquitetura, execução, memória, ferramentas, orquestração, automação, permissões, manutenção e considerações de migração. Recursos, preços, limites e disponibilidade dos provedores mudam rapidamente, então o advisor verifica novamente as informações atuais de primeira parte sempre que houver navegação disponível.
