> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/providers/hermes-agent.md`](../../../../kit/ai-assistant-system-advisor/references/providers/hermes-agent.md) — em caso de divergência, vale o original.

# Dossiê Hermes Agent

Lock de pesquisa: 23 de agosto de 2026.

- Repositório canônico: https://github.com/NousResearch/hermes-agent
- Última release estável no momento do lock: `v2026.8.19`, Hermes Agent v0.20.5, publicada em 21 de agosto de 2026
- Commit da branch padrão inspecionado: `f293e7206b4ddd66042329442c6afebc19a8808d`
- Licença: MIT no lock de pesquisa

Verifique novamente a release, o commit, a licença, os provedores e as orientações de segurança antes de recomendá-lo.

## Por que se tornou notável

O Hermes é posicionado como um runtime de agente autodesenvolvente (self-improving) e flexível quanto a modelos. Seu diferencial não é uma tela nem um modelo. É o harness (arcabouço de execução) operacional exposto: loop do agente, montagem de prompt, ferramentas, memória, skills, delegação, automação, gateways, backends de execução e controles de recuperação que um operador pode inspecionar e modificar.

O projeto divulga um ciclo de aprendizado fechado no qual o agente pode persistir memória curada, converter trabalho bem-sucedido em skills, aprimorar procedimentos reutilizáveis e pesquisar sessões anteriores. Ele também combina isso com amplo suporte a provedores de modelo, múltiplas superfícies de mensageria, cron, subagentes e execução local ou em nuvem.

## Anatomia do harness

### Pontos de entrada e loop

O Hermes aceita trabalho por meio de sua interface de terminal, gateway de mensageria, servidor de API, executor em lote, adaptador ACP e biblioteca Python. Esses pontos de entrada convergem no runtime principal do agente.

O loop executa a montagem de contexto e de prompt, chamadas a provedores de modelo, seleção e execução de ferramentas, transmissão de resultados em streaming, atualizações de memória e de sessão e verificações de conclusão. A implementação expõe subsistemas separados para roteamento de provedores, runtime de ferramentas, armazenamento de sessões, compressão de contexto, provedores de memória, delegação, gateways e plugins.

### Prompt e contexto

O Hermes monta o contexto de sistema a partir de instruções centrais, contexto de modelo e de provedor, ferramentas, skills, memória, contexto do usuário e histórico de sessão. A compressão de contexto e o cache de prompt junto ao provedor são partes explícitas do harness, o que importa para assistentes de longa duração com prefixos grandes de skills e memória.

### Modelos e roteamento

O Hermes pode usar Nous Portal, OpenRouter, OpenAI, serviços compatíveis com Anthropic, endpoints locais e outros provedores documentados pelo projeto. Os usuários podem trocar de modelo sem reescrever a camada operacional. Roteamento de provedores, cadeias de fallback, proxies de assinatura e configuração de modelo por perfil podem elevar o teto, mas também acrescentam carga de configuração e de depuração.

Não reduza isto a `any model works`. Verifique o provedor exato, a rota de autenticação, os recursos do modelo e os termos que o usuário pretende usar.

### Ferramentas e backends de execução

O runtime suporta ferramentas nativas, conjuntos de ferramentas agrupados, integrações MCP, provedores de navegador e de busca, execução de código, operações de arquivos e ferramentas contribuídas por plugins. A execução de terminal pode ser local ou rodar por meio de Docker, SSH, Singularity, Modal, Daytona ou Vercel Sandbox, conforme a documentação atual do projeto.

Essa é uma distinção importante entre padrão e teto. Uma instalação local básica e uma implantação em nuvem endurecida são duas formas do Hermes, mas não têm o mesmo perfil de persistência, segurança, custo ou manutenção.

### Skills e ciclo de aprendizado

Skills são instruções procedurais reutilizáveis compatíveis com o formato Agent Skills. O Hermes pode carregar skills embutidas, opcionais, instaladas e criadas pelo usuário. O produto atual também permite aprender ou destilar procedimentos a partir de trabalho concluído e iterar sobre eles ao longo do tempo.

Avalie a qualidade da skill resultante, não a existência de um comando de aprendizado. Uma skill aprendida ainda precisa de entradas explícitas, regras de decisão, validação, tratamento de falhas e fronteiras de aprovação.

### Memória

O Hermes separa memória curada, contexto do usuário, histórico de sessão, skills e plugins opcionais de provedores de memória. O ferramental de memória incluído permite adicionar, substituir e remover entradas, enquanto a busca em sessões oferece um caminho de volta para conversas anteriores. Provedores opcionais podem agregar comportamentos diferentes de armazenamento ou recuperação.

Pergunte ao usuário qual camada precisa ser portátil. `It has memory` não basta. Verifique autoridade de escrita, capacidade de edição, escopo, local de armazenamento, backup, comportamento de recuperação e defesas contra envenenamento para a configuração planejada.

### Delegação e orquestração

O Hermes pode criar subagentes para fluxos de trabalho separados e executar a delegação em primeiro ou em segundo plano. O teto inclui múltiplos perfis, tarefas isoladas, trabalhadores especializados e resultados coordenados. Confirme se o design desejado pelo usuário exige paralelismo, isolamento estrito, estado compartilhado ou apenas alguns papéis nomeados. São requisitos diferentes.

### Rotinas e entrega

O cron embutido pode executar tarefas em linguagem natural ou baseadas em script e entregar resultados às plataformas configuradas. No lock de pesquisa atual, as tarefas do cron podem carregar memória persistente e configurações de raciocínio por tarefa. O gateway de mensageria suporta um conjunto grande e em mudança de plataformas.

O comportamento sempre ativo depende de onde o Hermes e seu gateway rodam. Um VPS, um contêiner persistente, uma nuvem gerenciada ou um backend serverless pode continuar funcionando sem o notebook do usuário. Um processo local não.

## Segurança e recuperação

O Hermes documenta controles em camadas, incluindo aprovações para comandos perigosos, bloqueios rígidos para comandos extremos, regras de negação definidas pelo usuário, autorização e pareamento do gateway, proteções de gravação de arquivos, mascaramento de segredos, filtragem de credenciais, isolamento de contêiner e restrições de sites.

Nuances importantes:

- A execução local de terminal não é uma fronteira de contenção.
- Backends Docker, remotos e serverless alteram o modelo de isolamento.
- O cron headless precisa de uma política explícita para comandos que normalmente exigiriam aprovação.
- Skills, MCPs, conteúdo de navegador, memória e saída de ferramentas podem introduzir risco de injeção de prompt ou de cadeia de suprimentos.
- Checkpoints e rollback são opt-in e protegem arquivos, não todos os efeitos colaterais externos.
- O operador continua responsável por patches, segredos, backups, controle de acesso, logs e testes de recuperação.

O Hermes pode importar do OpenClaw configurações selecionadas, memória, skills, allowlists, configuração de mensageria e credenciais. Use um dry run e um backup. Não presuma equivalência semântica entre os dois sistemas.

## Padrões de fábrica vs. teto alcançável

| Camada | Padrão típico | Teto alcançável |
| --- | --- | --- |
| Setup | Instalação local guiada ou caminho pelo Nous Portal | Múltiplos perfis, provedores personalizados, implantação remota endurecida |
| Modelos | Um provedor e um modelo configurados | Roteamento, fallbacks, modelos locais, proxies de assinatura |
| Runtime | Terminal e arquivos locais | VPS, Docker, SSH, ambientes serverless ou GPU |
| Memória | Memória curada mais sessões | Provedores personalizados, modelos de usuário explícitos, camada de skills portátil |
| Ferramentas | Recursos embutidos e integrações selecionadas | MCPs, plugins, ferramentas personalizadas, controle de navegador e do computador |
| Automação | Cron e entrega pelo gateway | Rotinas multiagente, trabalho em segundo plano, sistemas orientados a eventos |
| Segurança | Padrões de aprovação e de gateway | Isolamento, regras de negação, gerenciador de segredos, checkpoints, políticas auditadas |

## Encaixe forte

- Operador técnico que quer inspecionar e modificar o harness.
- Usuário que precisa de roteamento de modelos ou quer que a camada operacional sobreviva a trocas de modelo.
- Equipe que precisa de canais de mensageria personalizados, hospedagem em nuvem ou skills reutilizáveis.
- Construtor que aceita manutenção em troca de propriedade e de teto.
- Operador atual do OpenClaw que quer um caminho de migração documentado e um modelo diferente de aprendizado ou de ferramentas.

## Encaixe fraco

- Usuário que quer zero setup e nenhum responsável pelo sistema.
- Equipe que não consegue operar patches, segredos, backups ou resposta a incidentes.
- Comprador cujos requisitos já são atendidos por um assistente gerenciado.
- Organização que precisa de compromissos de conformidade gerenciados pelo fornecedor que o stack auto-hospedado escolhido não oferece.

## Verificar antes de recomendar

- última release estável e notas de release
- SO suportado e caminho de instalação
- rota exata de provedor e de modelo
- termos de assinatura ou de API
- backend de terminal escolhido e comportamento de persistência
- adaptadores de mensageria necessários
- procedência de skills e plugins
- política de aprovação para trabalho interativo e agendado
- responsável por backup, restauração, monitoramento e atualização
- custo mensal total de infraestrutura e do operador

## Fontes primárias

- Repositório e README: https://github.com/NousResearch/hermes-agent
- Releases: https://github.com/NousResearch/hermes-agent/releases
- Arquitetura: https://hermes-agent.nousresearch.com/docs/developer-guide/architecture
- Loop do agente: https://hermes-agent.nousresearch.com/docs/developer-guide/agent-loop
- Montagem de prompt: https://hermes-agent.nousresearch.com/docs/developer-guide/prompt-assembly
- Skills: https://hermes-agent.nousresearch.com/docs/user-guide/features/skills
- Memória: https://hermes-agent.nousresearch.com/docs/user-guide/features/memory
- Delegação: https://hermes-agent.nousresearch.com/docs/user-guide/features/delegation
- Cron: https://hermes-agent.nousresearch.com/docs/user-guide/features/cron
- Roteamento de provedores: https://hermes-agent.nousresearch.com/docs/user-guide/features/provider-routing
- Mensageria: https://hermes-agent.nousresearch.com/docs/user-guide/messaging
- Segurança: https://hermes-agent.nousresearch.com/docs/user-guide/security
- Migração do OpenClaw: https://hermes-agent.nousresearch.com/docs/guides/migrate-from-openclaw

