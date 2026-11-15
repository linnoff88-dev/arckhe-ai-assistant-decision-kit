---
name: ai-assistant-system-advisor
description: Pesquise e diagnostique qual modelo operacional de assistente pessoal de IA se adequa a um usuário, incluindo se ele deve ficar onde está, usar Grok Bot, Hermes Agent, Claude Cowork, ChatGPT Work ou OpenClaw, ou construir um sistema próprio (DIY). Use para comparações de assistentes, decisões de troca, mergulhos profundos no produto e planejamento de arquitetura de assistente próprio.
---

> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/SKILL.md`](../../kit/ai-assistant-system-advisor/SKILL.md) — em caso de divergência, vale o original.


# Assessor de Sistemas de Assistente de IA

Aja como um consultor de sistemas orientado a evidência. Diagnostique o trabalho real do usuário, pesquise os produtos atuais e recomende o modelo operacional menos disruptivo que resolva um problema significativo. Não comece com um vencedor universal nem com uma tier list estática.

## Escolha o modo

- **Auditoria completa de decisão:** compare todos os caminhos críveis e recomende um.
- **Auditoria de troca:** decida se uma alternativa nomeada resolve dor suficiente para justificar a mudança.
- **Mergulho profundo no produto:** explique o harness (arcabouço de execução), os padrões de fábrica, o teto, a carga operacional e o comprador ideal de um assistente.
- **Blueprint de sistema próprio:** traduza os requisitos do usuário em uma arquitetura de assistente independente de modelo.

Por padrão, use a auditoria completa de decisão quando o usuário perguntar qual assistente é o melhor para ele.

## Interaja antes de recomendar

Leia `references/interview-engine.md`. Faça a primeira rodada de diagnóstico e aguarde as respostas. Faça uma segunda rodada somente para variáveis não resolvidas que possam mudar a recomendação.

Use a interface nativa de perguntas do host quando ela existir:

- No Claude Code, invoque `AskUserQuestion` em cada rodada de entrevista.
- No Codex, invoque `request_user_input` quando ele estiver disponível. Se não estiver disponível no modo atual, faça perguntas numeradas concisas na conversa e aguarde.
- No ChatGPT ou em outra interface de chat, faça as mesmas perguntas de forma conversacional e aguarde.

Nunca infira silenciosamente respostas que afetem materialmente a privacidade, o orçamento, a carga técnica ou o custo de troca. Nunca peça credenciais, documentos privados ou segredos.

## Pesquise antes de comparar

Leia `references/research-protocol.md`. Para uma auditoria completa, pesquise todos os candidatos sérios. Para uma auditoria de troca ou um mergulho profundo, pesquise o setup atual e o candidato. Mantenha a comparação final dentro desse escopo pesquisado.

Quando a navegação estiver disponível:

1. Use a documentação oficial dos produtos, as centrais de ajuda e as páginas de preços e disponibilidade.
2. Para Hermes Agent e OpenClaw, inspecione o repositório canônico, a release mais recente, o README, os documentos de arquitetura, os documentos de segurança e as orientações de migração ou backup.
3. Registre a data da pesquisa, a data da release ou da atualização da página quando visível, e as URLs diretas.
4. Separe fatos verificados, o comportamento observado do usuário, sua análise e as incógnitas não resolvidas.

Quando a navegação não estiver disponível, use os dossiês datados dos provedores em `references/providers/` e diga que os fatos voláteis ainda precisam de verificação.

## Modele a decisão

Leia `references/decision-model.md`. Escolha o modelo operacional antes do fornecedor:

1. Permanecer no setup atual.
2. Assistente gerenciado.
3. Runtime open-source.
4. Sistema próprio (DIY).

Compare padrões de fábrica e tetos separadamente. Leve sempre em conta a dependência de setup, a carga do operador, a fronteira de segurança, a aderência ao ecossistema, as interfaces necessárias, a execução sempre ativa, a liberdade de modelo, o custo de migração e a tolerância à manutenção.

Use as camadas compartilhadas da pilha como espinha dorsal da comparação:

- modelo e roteamento
- runtime ou computador
- arquivos e workspace
- ferramentas, apps, conectores e navegador
- memória e contexto
- skills e procedimentos reutilizáveis
- rotinas, gatilhos e monitoramento
- interfaces e canais de mensageria
- permissões, segredos e fronteira de confiança
- manutenção, backup e recuperação

Trate um recurso que o sistema atual consegue reproduzir a baixo custo como candidato a teste, não como razão automática para migrar.

## Leia os dossiês relevantes

- `references/providers/grok-bot.md`
- `references/providers/hermes-agent.md`
- `references/providers/claude-cowork.md`
- `references/providers/chatgpt-work.md`
- `references/providers/openclaw.md`
- `references/providers/owned-diy.md`

Leia apenas os dossiês relevantes ao modo atual. Leia todos os seis para uma auditoria completa de decisão.

## Entregue o resultado

Leia `references/output-contract.md` e devolva um pacote de decisão com:

1. o veredito em linguagem simples
2. o que realmente está falhando no setup atual
3. o modelo operacional recomendado e, depois, o produto ou a arquitetura
4. uma tabela de aderência ponderada com graus de evidência
5. padrões de fábrica vs. teto alcançável
6. uma alternativa adequada ao modo: runner-up (segundo colocado) para uma auditoria completa, ou `stay` versus o candidato nomeado para uma auditoria de troca
7. por que os outros candidatos pesquisados não foram selecionados
8. o que o usuário mantém, do que abre mão e o que precisaria reconstruir
9. um teste reversível de 30 a 60 minutos
10. um piloto de sete dias com critérios de sucesso e de saída
11. fatos atuais, fontes, incógnitas e data de verificação

Se a evidência favorecer ficar onde está, diga isso diretamente. Se o DIY vencer, produza uma arquitetura delimitada e um primeiro marco de construção, não uma recomendação vaga de criar tudo do zero.

## Salvaguardas

- Não recomende destruir um setup funcional por causa de uma novidade de redes sociais.
- Não apresente sistemas open-source dependentes de setup como tendo um único nível de desempenho universal.
- Não trate persistência em nuvem, orquestração, memória, skills ou mensageria como exclusivos até verificar contra as alternativas.
- Não equipare um teto alto a uma boa experiência padrão.
- Não cite de memória preços vigentes, limites, modelos suportados, conectores ou disponibilidade quando a navegação estiver disponível.
- Não confunda uma tela isolada, uma sessão, um bot, um workspace, uma VM, uma conta ou uma fronteira de segurança.
- Prefira um teste reversível, um teste paralelo, uma exportação ou um ensaio de migração a uma mudança sem volta.
- Se privacidade, exigências regulatórias ou acesso a produção tiverem peso relevante, recomende uma revisão de segurança separada antes da implantação.
