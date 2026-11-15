> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/providers/openclaw.md`](../../../../kit/ai-assistant-system-advisor/references/providers/openclaw.md) — em caso de divergência, vale o original.

# Dossiê OpenClaw

Lock de pesquisa: 23 de agosto de 2026.

- Repositório canônico: https://github.com/openclaw/openclaw
- Última release estável do GitHub no momento do lock: `v2026.7.1-2`, publicada em 4 de agosto de 2026
- Commit da branch padrão inspecionado: `c4e0c003a406cdd943291a6b31af3e302c14ccaf`

Verifique a última release, o commit, a licença e a documentação atuais antes de recomendá-lo.

## Por que se tornou notável

O OpenClaw demonstrou que modelos existentes, ferramentas, canais de mensageria, dispositivos, arquivos, automações e runtimes remotos podiam ser costurados em um assistente pessoal persistente. Sua importância histórica é o padrão completo de gateway. Ele tornou a categoria legível mesmo quando a experiência inicial era complexa.

Não avalie o projeto atual apenas pela crítica ou pelo hype da época do lançamento. O repositório continuou a evoluir. Compare a release e a arquitetura atuais com os requisitos reais do usuário.

## Anatomia do harness (arcabouço de execução)

### Gateway primeiro

O Gateway de longa duração é o plano de controle. Ele controla as superfícies de mensageria, expõe uma API WebSocket tipada, gerencia eventos e integridade, aceita clientes e conecta nós de dispositivos. Apps de desktop, CLI, UI web, automações e dispositivos se conectam ao gateway.

Isso torna o OpenClaw especialmente relevante quando o assistente precisa estar presente em múltiplos canais e dispositivos. Também significa que o gateway é uma fronteira operacional e de segurança que precisa ser hospedada, autenticada, monitorada e recuperada.

### Runtime do agente

O runtime embutido cuida do loop do agente, da seleção de modelo, da normalização de provedores, do contexto e da compactação, das sessões, dos prompts, das skills, das ferramentas, do streaming e da persistência de transcripts. O OpenClaw também expõe um registro de harness para que runtimes de plugins possam ser selecionados sob regras documentadas.

O loop de execução resolve uma sessão, serializa o trabalho para evitar corridas de estado, monta o snapshot de prompt e skills, seleciona um modelo e um perfil de autenticação, executa ferramentas, transmite o progresso em streaming e grava o transcript durável sob fencing de writer-claim.

### Modelos e seleção de harness

O registro de provedores de modelo e o harness do agente são conceitos separados. O OpenClaw pode rotear entre provedores documentados, enquanto um nome de provedor ou de modelo, sozinho, não necessariamente seleciona um harness diferente. Verifique a rota efetiva, a autenticação, o comportamento das requisições e a seleção de runtime, em vez de presumir que trocar o modelo muda toda a camada operacional.

### Workspace, sessões e recursos

Os agentes operam dentro de workspaces com histórico de sessão e descoberta de recursos. Pacotes de recursos podem contribuir com extensões, skills, prompts e temas. As sessões são duráveis, e os modos de fila determinam como novas mensagens orientam, acompanham, acumulam ou interrompem o trabalho ativo.

### Memória

A arquitetura de memória atual usa arquivos inspecionáveis além de um índice SQLite, com múltiplos níveis de memória, procedência, regras de escrita, trilhas de recall, modelagem do usuário, memória ativa, intenções permanentes e curadoria em segundo plano. A arquitetura trata o caminho de escrita como a fronteira de segurança principal.

Esta é uma afirmação mais forte do que `OpenClaw remembers`. Avalie:

- quem ou o que pode escrever em cada superfície de memória
- como se impede que conteúdo não confiável se torne autoritativo
- o que é visível e editável
- o que é recuperado a cada turno
- como a memória recebe backup ou é movida
- se múltiplos usuários ou salas precisam de fronteiras separadas

### Agentes e delegação

O OpenClaw suporta múltiplos agentes, bindings de agente, trabalho delegado, filas, sessões e trilhas de especialista. Pergunte se a configuração desejada precisa de identidades separadas, workspaces separados, credenciais separadas ou apenas de conversas separadas. Trabalho em paralelo não implica automaticamente isolamento de segurança.

### Automação

Tarefas de cron, hooks, webhooks, ordens permanentes, polling, fluxos de tarefas e heartbeats podem sustentar trabalho recorrente ou orientado a eventos. O mecanismo certo depende de a tarefa ser baseada em tempo, baseada em eventos, com estado ou exigir uma sessão ativa.

### Canais e dispositivos

O gateway oferece um catálogo amplo e em constante mudança de canais, incluindo superfícies comuns de mensageria e colaboração. Quando configurados, os nós de dispositivos podem expor capacidades como tela, câmera, localização e interfaces hospedadas.

Esse alcance de canais é um dos casos de uso mais fortes do OpenClaw. Ele também amplia a superfície de ataque e a carga de autorização.

## Segurança e fronteira operacional

O projeto documenta autenticação, pareamento de dispositivos, modos de permissão, sandboxing, política de ferramentas, segredos, auditorias de segurança, limitação de taxa, operações seguras de arquivos, exposição de rede e resposta a incidentes.

Nuances importantes:

- O modelo de confiança padrão é o de um assistente pessoal para um único operador, e não um isolamento multi-tenant hostil.
- Um gateway, uma sessão, um workspace, um canal ou uma credencial compartilhados podem vazar contexto se as fronteiras forem configuradas incorretamente.
- Execução local, execução em sandbox e execução elevada no host são níveis de risco diferentes.
- Plugins, skills, hooks, servidores MCP, canais, conteúdo de navegador e memória recuperada podem carregar entrada não confiável.
- Expor o gateway publicamente exige controles deliberados de autenticação, de rede e de limitação de taxa.
- Auditorias de segurança detectam riscos de configuração, mas não substituem a responsabilidade operacional.

Rode a auditoria de segurança documentada e um backup antes de mudanças de configuração relevantes. Prefira acesso por rede privada — como uma VPN ou um túnel autenticado — a uma exposição pública ampla.

## Padrões de fábrica vs. teto alcançável

| Camada | Padrão típico | Teto alcançável |
| --- | --- | --- |
| Interface | CLI, web, canais configurados | Presença ampla multicanal e em dispositivos |
| Runtime | Um gateway e o harness embutido | Harnesses de plugin, nós remotos, agentes especializados |
| Modelos | Provedor e modelo configurados | Roteamento de provedores, failover, modelos locais e hospedados |
| Memória | Arquivos do workspace e recall indexado | Curadoria em camadas, modelo do usuário, intenções permanentes |
| Automação | Cron básico e hooks | Fluxos orientados a eventos, ordens permanentes, webhooks, trilhas de especialista |
| Segurança | Gateway local e aprovações | Ingress privado endurecido, sandboxing, operadores com escopo, auditorias |

## Encaixe forte

- Operador que valoriza o alcance de mensageria e dispositivos como interface principal.
- Construtor que quer um gateway, workspaces, memória e stack de automação inspecionáveis.
- Usuário com uma instalação existente do OpenClaw cujas skills e canais conquistados com esforço já funcionam.
- Equipe disposta a operar autenticação, upgrades, plugins, backups e monitoramento.
- Arquiteto estudando um sistema de assistente maduro e abrangente antes de construir uma camada própria.

## Encaixe fraco

- Usuário não técnico que quer uma configuração polida de cinco minutos.
- Equipe sem alguém responsável pela segurança e pela recuperação do gateway.
- Organização que precisa de forte isolamento multi-tenant sem um trabalho de design significativo.
- Usuário cujas necessidades se limitam a documentos gerenciados e trabalho de conhecimento conectado.
- Comprador considerando migração apenas porque outro produto está na moda no momento.

## Verificar antes de recomendar

- última release estável e notas de migração
- sistema operacional exato e caminho de hospedagem
- exposição e autenticação escolhidas para o gateway
- adaptadores de canal necessários e seu estado de manutenção
- rota de provedor de modelo e de harness
- isolamento de workspace, sessão, agente e usuário
- política de escrita e backup da memória
- sandbox, aprovações e política de ferramentas
- cadeia de suprimentos de segredos e plugins
- responsável por monitoramento de saúde, atualização e incidentes

## Fontes primárias

- Repositório e README: https://github.com/openclaw/openclaw
- Releases: https://github.com/openclaw/openclaw/releases
- Arquitetura do runtime: https://github.com/openclaw/openclaw/blob/main/docs/agent-runtime-architecture.md
- Arquitetura do gateway: https://github.com/openclaw/openclaw/blob/main/docs/concepts/architecture.md
- Loop do agente: https://github.com/openclaw/openclaw/blob/main/docs/concepts/agent-loop.md
- Arquitetura da memória: https://github.com/openclaw/openclaw/blob/main/docs/concepts/memory-architecture.md
- Conceitos multiagente: https://github.com/openclaw/openclaw/blob/main/docs/concepts/multi-agent.md
- Cron: https://github.com/openclaw/openclaw/blob/main/docs/automation/cron-jobs.md
- Canais: https://github.com/openclaw/openclaw/blob/main/docs/channels/index.md
- Segurança do gateway: https://github.com/openclaw/openclaw/blob/main/docs/gateway/security/index.md
- Sandboxing: https://github.com/openclaw/openclaw/blob/main/docs/gateway/sandboxing.md
- Auditoria de segurança: https://github.com/openclaw/openclaw/blob/main/docs/cli/security.md

