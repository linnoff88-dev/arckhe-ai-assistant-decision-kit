> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/providers/grok-bot.md`](../../../../kit/ai-assistant-system-advisor/references/providers/grok-bot.md) — em caso de divergência, vale o original.

# Dossiê do Grok Bot

Lock de pesquisa: 23 de agosto de 2026.

O Grok Bot é um assistente gerenciado em nuvem no ecossistema atual de xAI, Grok e Cursor. Antes de recomendá-lo, verifique planos elegíveis, preços, uso incluído, plataformas suportadas, controles de modelo e disponibilidade para equipes.

## Por que se tornou notável

O Grok Bot transforma em produto um computador em nuvem persistente, Bots nomeados, telas paralelas, arquivos e logins compartilhados, transferências (handoffs), skills e rotinas, tudo isso atrás de uma interface voltada ao consumidor. A novidade, para muitos compradores, não é que agentes em nuvem, cron, skills ou orquestração fossem impossíveis antes. O valor está em o fornecedor empacotar tudo isso sem exigir que o usuário implante um VPS, um gateway ou um runtime open-source.

Trate a atenção nas redes sociais como um catalisador, não como evidência de adequação do produto.

## Modelo operacional atual

### Computador em nuvem persistente

Segundo a documentação oficial, todos os Bots de uma conta usam um único computador em nuvem persistente. Eles compartilham o sistema de arquivos, as sessões de navegador e os logins de aplicativos desse computador. Cada Bot tem a própria tela, o que permite interação em paralelo, mas as telas não são fronteiras de segurança separadas.

Essa nuance é essencial. Um arquivo ou login colocado no computador deve ser tratado como disponível para todos os Bots daquela conta.

### Trabalho em segundo plano

O trabalho do Bot roda no computador em nuvem e pode continuar quando o app desktop, o celular ou o notebook estão fechados. O usuário não precisa operar a VM diretamente.

Portanto, a execução sempre ativa é um padrão nativo forte, mas não um teto exclusivo. Hermes, OpenClaw ou um sistema próprio (DIY) também podem rodar em infraestrutura persistente ou serverless, se o usuário estiver disposto a operá-la.

### Superfícies

No momento do lock de pesquisa, a documentação oficial listava suporte a macOS, Windows e iPhone, com Linux desktop, Android e iPad sem suporte no lançamento inicial. Reconfirme isso, porque o rollout é volátil.

## Harness de trabalho (arcabouço de execução)

### Bots e transferências

Um Bot é um agente ou companheiro de equipe nomeado e persistente. Os Bots podem passar contexto e trabalho uns aos outros pelo computador compartilhado. Bots nomeados não implicam necessariamente arquivos, credenciais, memória ou computação separados.

Pergunte ao usuário se ele precisa de separação de papéis, concorrência ou isolamento de segurança real. O modelo de computador compartilhado do Grok Bot atende aos dois primeiros casos de forma mais direta do que ao terceiro.

### Skills

Skills capturam passos, regras de decisão, saída esperada e limites de segurança. A documentação atual diz que skills podem ficar disponíveis entre Bots, sujeitas aos conectores ou logins exigidos. Uma tarefa única bem-sucedida pode ser salva como uma skill reutilizável.

O recurso Teach a task pode gravar uma demonstração no navegador e transformá-la em um rascunho de skill, onde o recurso estiver disponível. Um fluxo de trabalho gravado ainda precisa de regras de decisão, tratamento de falhas, validação e limites de aprovação.

### Rotinas e gatilhos de eventos

Uma rotina atribui um fluxo de trabalho a um Bot e especifica quando ele é executado. A documentação atual descreve trabalho agendado e acionado por eventos, execuções de teste, histórico de execuções e controles de uso. No momento do lock de pesquisa, um Bot podia ter até 50 rotinas, e o app mantinha os 20 registros mais recentes de execução por rotina. Reconfirme esses limites.

### Ferramentas, aplicativos e logins

Os Bots podem usar o navegador compartilhado, o terminal, o sistema de arquivos, ferramentas conectadas, sites e logins de aplicativos. O ambiente gerenciado pelo fornecedor reduz a carga de configuração e, ao mesmo tempo, aumenta a dependência do computador do fornecedor, das configurações de dados, dos controles de conta e das integrações suportadas.

### Modelos

Não presuma um roteamento amplo de modelos. Verifique qual é o modelo exato usado, se o usuário pode selecionar modelos ou nível de esforço, como o uso é medido e se o produto continua atrelado ao ecossistema atual de contas Grok e Cursor.

## Aprovações, privacidade e confiança

O Grok Bot documenta aprovações, limites explícitos de ação, transferências seguras e o comportamento opcional Auto Review. Trabalhos sensíveis ou de grandes consequências — enviar, publicar, comprar, excluir, alterar permissões ou mexer em produção — devem ter regras de aprovação estreitas.

Fronteiras principais:

- Os Bots compartilham um computador em nuvem, arquivos, sessões de navegador e logins.
- A tela de um Bot não é uma fronteira de segurança.
- O Grok Bot exige armazenamento de dados em nuvem e não suportava o Legacy Privacy Mode no momento do lock de pesquisa.
- As configurações de treinamento e de dados da conta seguem os controles de conta e de privacidade do Cursor aplicáveis, conforme descrito pelo fornecedor.
- As execuções de teste realizam trabalho real e podem acionar ferramentas conectadas ou alterar arquivos.
- As rotinas em segundo plano precisam de políticas para dados obsoletos, ausência de dados, novas tentativas e aprovação.
- Excluir um Bot pode não remover arquivos compartilhados nem logins deixados no computador.

## Padrões de fábrica vs. teto alcançável

| Camada | Padrão comum | Teto alcançável |
| --- | --- | --- |
| Configuração | Instalar o app, criar um Bot, conceder acesso | Múltiplos Bots por papel, skills, rotinas, gatilhos de eventos |
| Runtime | Computador em nuvem persistente gerenciado pelo fornecedor | Telas paralelas e transferências compartilhadas |
| Modelos | Configuração atual de modelos do Grok Bot | Limitado aos controles que o fornecedor expõe |
| Arquivos e aplicativos | Computador, navegador, arquivos e logins compartilhados | Fluxos de trabalho multi-tool conectados |
| Automação | Um turno delegado | Skills, agendamentos, rotinas de eventos, trabalho em segundo plano |
| Propriedade | O fornecedor opera o computador e o harness | O usuário é dono dos procedimentos dentro dos controles expostos |

## Perfis com forte aderência

- Usuário sem perfil técnico que quer execução persistente em nuvem com configuração mínima.
- Comprador que já paga pelo ecossistema Grok e Cursor e o utiliza.
- Usuário que ficou de fora dos assistentes open-source porque VPS, segredos e gateways pareciam complicados demais.
- Fluxo de trabalho que se beneficia de vários Bots especializados por papel compartilhando um mesmo espaço de trabalho.
- Comprador que aceita uma fronteira de confiança em nuvem gerenciada pelo fornecedor e os limites atuais da plataforma.

## Perfis com fraca aderência

- Usuário que precisa de roteamento de modelos independente de provedor ou de um harness inspecionável.
- Equipe que exige isolamento rigoroso entre agentes, papéis, clientes ou credenciais.
- Usuário em uma plataforma sem suporte.
- Comprador cujo sistema atual já reproduz de forma barata a persistência e as rotinas desejadas.
- Organização cujas políticas de privacidade ou de dados conflitam com o armazenamento em nuvem exigido.

## Verificar antes de recomendar

- planos elegíveis atuais, preço, produtos incluídos e uso semanal
- suporte a plataformas desktop e móveis
- disponibilidade para equipes e empresas
- controles atuais de modelo e de escolha de modelo
- isolamento do computador compartilhado e fronteira da conta
- suporte a conectores e logins
- limites de skills, rotinas e eventos
- comportamento de aprovação e Auto Review
- configurações de privacidade, treinamento, retenção, exclusão e armazenamento em nuvem
- opções de exportação e recuperação

## Fontes primárias

- Visão geral: https://docs.x.ai/grok-bot/overview
- Primeiros passos: https://docs.x.ai/grok-bot/get-started
- FAQ: https://docs.x.ai/grok-bot/faq
- Skills e rotinas: https://docs.x.ai/grok-bot/skills-routines-and-automations
- Aprovações, segurança e privacidade: https://docs.x.ai/grok-bot/approvals-security-and-privacy
- Equipes e empresas: https://docs.x.ai/grok-bot/teams-and-enterprises
