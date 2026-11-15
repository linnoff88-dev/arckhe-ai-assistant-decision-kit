> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/providers/owned-diy.md`](../../../../kit/ai-assistant-system-advisor/references/providers/owned-diy.md) — em caso de divergência, vale o original.

# Dossiê do Sistema Próprio (DIY)

Lock de pesquisa: 23 de agosto de 2026.

Um sistema próprio (DIY) não é um único produto. É uma camada operacional na qual o usuário controla as partes duráveis do assistente e trata Claude, Codex, Grok, um modelo aberto ou outro provedor como um motor substituível.

## Por que esse caminho existe

Assistentes gerenciados empacotam repetidamente as mesmas primitivas amplas com padrões, superfícies e fronteiras de confiança diferentes. Sistemas open-source expõem mais da maquinaria, mas ainda assim trazem uma arquitetura opinativa. Um sistema próprio (DIY) torna-se atraente quando o próprio fluxo de trabalho do usuário é o ativo valioso e precisa sobreviver a mudanças de produto.

Esse caminho não deve vencer apenas porque tem o maior teto teórico.

## As dez camadas

### 1. Gateway de modelos

Defina uma interface pequena entre a camada operacional e o provedor de modelos. Ela deve expressar as capacidades de que o sistema realmente precisa, como texto, ferramentas, imagens, execução de código, saída estruturada ou trabalho de longa duração.

Mantenha autenticação e parâmetros específicos do provedor atrás de adaptadores. Verifique os termos do SDK e da assinatura antes de escolher rotas com login em cache, OAuth, API ou corporativas.

### 2. Runtime e workers

Escolha onde o trabalho roda:

- máquina local, para alcance direto do dispositivo
- VPS persistente, para trabalho simples sempre ativo
- container, para reprodutibilidade e isolamento
- sandbox serverless, para tarefas intermitentes
- sessão gerenciada do fornecedor, para menor carga operacional

Um sistema pode usar mais de um runtime. A localização deve seguir o requisito de dados e de ferramentas.

### 3. Workspace e arquivos

Use um layout de projeto estável, com propriedade clara, áreas temporárias, saídas, logs e recuperação. Mantenha os artefatos gerados separados dos arquivos-fonte autoritativos. Evite dar a todo worker acesso irrestrito ao mesmo sistema de arquivos.

### 4. Ferramentas e conectores

Prefira a ferramenta mais estreita e confiável:

1. API ou conector de propósito específico
2. MCP ou CLI
3. automação de navegador
4. uso de computador

Defina, por ferramenta, escopos de leitura e escrita, limiares de aprovação, idempotência, novas tentativas e logs de auditoria.

### 5. Memória e contexto

Separe:

- fatos duráveis sobre o usuário
- conhecimento do projeto
- transcrição da sessão
- skills procedurais
- estado da tarefa
- índice de recuperação
- observações que ainda não foram promovidas

A pergunta essencial de design é quem pode escrever memória autoritativa e como conteúdo contaminado ou obsoleto é rejeitado.

### 6. Skills e procedimentos

Armazene fluxos de trabalho bem-sucedidos como skills portáteis, com gatilhos, entradas, regras de decisão, validação, tratamento de falhas e limites de aprovação. Mantenha-os independentes da fraseologia de um modelo específico, quando possível.

### 7. Rotinas e eventos

Use um agendador ou sistema de eventos que registre a fonte de entrada, o estado da execução, as tentativas, a saída, o custo e a falha. Uma tarefa recorrente precisa de comportamento definido para dados obsoletos, política de novas tentativas, responsável e caminho de notificação.

### 8. Orquestração

Use um único agente até o paralelismo trazer um benefício mensurável. Adicione workers quando as tarefas forem verificáveis de forma independente ou precisarem de ferramentas, modelos, permissões ou contextos diferentes.

Defina explicitamente o estado compartilhado. Não confunda chats separados com fronteiras de segurança separadas.

### 9. Interfaces e canais

Escolha as superfícies de que o usuário realmente precisa: web, desktop, terminal, celular, Slack, Telegram, e-mail ou um painel privado. Mantenha os adaptadores de interface separados do fluxo central de trabalho, para que a camada operacional sobreviva a uma mudança de UI.

### 10. Confiança, operações e recuperação

Defina:

- política de aprovação
- gerenciador de segredos
- fronteira de rede e de sistema de arquivos
- tratamento de prompt injection
- logs e trilha de auditoria
- backups e testes de restauração
- política de atualização
- health checks e alertas
- responsável por incidentes
- kill switch

Se ninguém for responsável por isso, o sistema não é realmente próprio. É apenas infraestrutura abandonada.

## Gate de construção

Recomende um sistema próprio (DIY) somente se tudo isto for verdadeiro:

1. O usuário tem um fluxo de trabalho recorrente e valioso que os produtos gerenciados não atendem de forma limpa.
2. O fluxo de trabalho durável é mais valioso do que qualquer interface individual de provedor.
3. Uma pessoa designada pode fazer a manutenção do sistema.
4. O primeiro marco pode ser construído e testado em escopo restrito.
5. Segurança e recuperação estão incluídas no design.
6. O usuário aceita um padrão menos polido em troca de controle.

## Arquitetura mínima viável

Comece com um fluxo de trabalho e seis objetos:

```text
Interface
  -> task contract
  -> one agent loop
  -> model adapter
  -> narrow tool set
  -> project workspace and memory
  -> run log and approval gate
```

Não comece com uma frota de agentes nomeados. Adicione agendamentos, canais, modelos extras e subagentes somente depois que o primeiro fluxo de trabalho passar repetidamente pelo teste de aceitação.

## Contrato do primeiro marco

Defina:

- uma entrada
- uma saída finalizada
- um adaptador de modelo
- no máximo três ferramentas
- um workspace
- uma fronteira de aprovação
- um mecanismo de recuperação
- um conjunto de avaliação com cinco exemplos reais

O marco está completo quando ele passa no conjunto de avaliação, registra as falhas e pode ser reexecutado após a troca do adaptador de modelo sem redesenhar o fluxo de trabalho.

## Perfis com forte aderência

- Usuário com fluxos de trabalho recorrentes peculiares e preocupação significativa com a troca de provedores.
- Fundador técnico ou equipe técnica com um operador e um orçamento real de manutenção.
- Organização que precisa de memória, permissões, interfaces ou fronteiras de dados personalizadas.
- Construtor que quer absorver ideias úteis de novos produtos sem migrar o sistema inteiro.
- Usuário que já tem uma camada funcional baseada no SDK do Claude ou do Codex e quer torná-la agnóstica em relação a modelos.

## Perfis com fraca aderência

- Usuário que quer um produto polido imediatamente.
- Comprador sem um fluxo de trabalho recorrente ou sem valor de negócio mensurável.
- Equipe sem nenhum responsável pela manutenção.
- Usuário cujas necessidades já são atendidas por um único assistente gerenciado.
- Organização tentando burlar os termos dos provedores ou revender computação obtida via assinatura.

## Verificar antes de recomendar

- termos atuais de SDK e de autenticação dos provedores
- restrições de uso pessoal, interno, comercial e de revenda
- localização da implantação e dos dados
- limites de uso de modelos e ferramentas
- armazenamento e rotação de segredos
- design de backup e de rollback
- tempo de operador e custo de infraestrutura
- plano de avaliação e monitoramento
- caminho de saída caso a pessoa responsável pela manutenção saia

## Arquiteturas de referência úteis

Estude os repositórios canônicos atuais e as documentações oficiais dos produtos gerenciados em busca de padrões, não para clonar às cegas:

- Hermes Agent: https://github.com/NousResearch/hermes-agent
- OpenClaw: https://github.com/openclaw/openclaw
- Arquitetura do Claude Cowork: https://support.claude.com/en/articles/14479288-claude-cowork-architecture-overview
- ChatGPT Work: https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex
- Visão geral do Grok Bot: https://docs.x.ai/grok-bot/overview
