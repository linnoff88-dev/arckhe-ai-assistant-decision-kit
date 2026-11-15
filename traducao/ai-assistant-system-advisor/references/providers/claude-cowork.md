> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/providers/claude-cowork.md`](../../../../kit/ai-assistant-system-advisor/references/providers/claude-cowork.md) — em caso de divergência, vale o original.

# Dossiê Claude Cowork

Lock de pesquisa: 23 de agosto de 2026.

Claude Cowork é um agente de trabalho gerenciado no ecossistema Claude. Verifique elegibilidade de plano, estado de rollout, limites de uso, disponibilidade de modelos e suporte a conectores imediatamente antes de recomendá-lo.

## Por que ele se tornou notável

O Cowork criou uma camada intermediária prática entre o Claude conversacional e um fluxo de trabalho do Claude Code centrado no terminal. Deu aos usuários não técnicos e de trabalho do conhecimento um agente capaz de planejar, usar arquivos e ferramentas conectadas, executar código, coordenar subtarefas e devolver entregas finalizadas sem exigir que eles operassem o harness (arcabouço de execução) de terminal diretamente.

A relevância do produto está na conveniência e na integração, não em uma reivindicação exclusiva sobre cada primitiva subjacente. Sistemas open-source e sistemas próprios (DIY) podem reproduzir muitas dessas mesmas primitivas, mas o Cowork as empacota atrás de uma interface e de um modelo de permissões gerenciados pelo fornecedor.

## Modelo operacional atual

### Sessões em nuvem

A documentação oficial atual diz que sessões do Cowork podem rodar na nuvem da Anthropic. O loop do agente e o código executam em um ambiente temporário isolado em infraestrutura gerenciada pela Anthropic, enquanto as sessões e os arquivos ficam associados à conta Claude do usuário. Sessões em nuvem podem continuar mesmo com o laptop fechado.

Quando uma sessão em nuvem precisa de um arquivo local, de um navegador local ou de um aplicativo local, ela acessa o dispositivo por meio do Claude Desktop. Essa dependência local exige que o dispositivo e a ponte de desktop permaneçam disponíveis no momento do acesso.

### Sessões locais

Implantações de desktop existentes podem usar um caminho de execução local. Nessa arquitetura, o loop do agente roda no dispositivo e o código executa dentro de uma VM local isolada. Leituras de arquivos locais, acesso ao navegador e servidores MCP de plugins locais seguem as permissões do dispositivo e os controles de rede.

Nunca diga simplesmente `Cowork runs in the cloud` ou `Cowork runs locally`. O modo e o recurso necessário determinam a resposta.

### Superfícies e continuidade

O Cowork é documentado no desktop, na web e no celular para planos pagos elegíveis, com sessões em nuvem sincronizadas entre as superfícies. O estado de rollout pode variar por plano e plataforma.

O Dispatch é um caminho do celular para o desktop. Ele pode iniciar um trabalho a partir de um celular que usa arquivos locais, plugins, conectores e aplicativos de desktop, mas o desktop precisa permanecer acordado e o Claude Desktop deve continuar aberto. Isso difere de uma sessão em nuvem que não tem dependência local ativa.

## Harness de trabalho

### Planejamento e trabalho paralelo

O Cowork pode planejar uma tarefa complexa, dividir o trabalho em subtarefas, coordenar fluxos paralelos de trabalho, executar código e comandos de shell no seu ambiente e produzir saídas finalizadas. O comportamento multiagente ou paralelo, portanto, não é exclusivo de produtos open-source.

O usuário não controla o harness subjacente com o mesmo grau que Hermes, OpenClaw ou um sistema próprio (DIY).

### Arquivos, projetos e memória

Projetos do Cowork podem conter arquivos, links, instruções e memória de projeto. Projetos de pasta local estão atrelados à disponibilidade do desktop, enquanto projetos em nuvem são salvos junto à conta do membro.

As páginas oficiais mudaram rapidamente quanto ao comportamento mais amplo da memória. No lock de pesquisa, uma página de ajuda diz que a memória de chat não é automaticamente levada para o Cowork e que a memória é suportada dentro dos projetos, enquanto a orientação sobre o Dispatch descreve memória entre sessões. Trate o escopo exato como um fato volátil. Verifique se a memória esperada pelo usuário é global, com escopo de projeto, derivada do chat, editável e portátil.

### Conectores, plugins e skills

O Cowork pode usar conectores e plugins. Os plugins atuais da Anthropic podem agrupar skills, conectores e subagentes. Alguns recursos de plugin e servidores MCP locais continuam dependentes do desktop. Serviços conectados podem incluir sistemas comuns de trabalho do conhecimento como Google Drive, Gmail, Slack e outros disponíveis no catálogo atual.

Não pontue a quantidade de conectores. Verifique os serviços, as ações, as permissões de administrador, a autenticação e as capacidades de escrita exatas de que o usuário precisa.

### Uso de navegador e computador

O Cowork usa primeiro a ferramenta mais precisa disponível. Ele pode preferir um conector e, quando necessário, recorrer a caminhos de uso do navegador ou do computador. O uso do computador pode agir sobre aplicativos locais em ambientes de desktop suportados e traz risco maior do que um conector estruturado.

### Tarefas agendadas

Tarefas agendadas podem executar trabalho recorrente ou sob demanda. Agendamentos em nuvem podem continuar com o computador do usuário desligado e podem usar arquivos em nuvem, conectores, skills e plugins. Uma tarefa agendada que exige arquivos ou aplicativos locais precisa rodar localmente e, portanto, depende do dispositivo.

## Permissões, privacidade e limites

O Cowork oferece modos de permissão que vão de revisão manual a operação mais automática. A documentação atual distingue os modos Manual, Auto e Skip, com controles ou restrições adicionais para organizações Team e Enterprise. Ações sensíveis e políticas organizacionais ainda podem forçar aprovação.

Fronteiras principais:

- Tokens de autorização de conectores são documentados como permanecendo fora do sandbox de nuvem, e as chamadas ocorrem no lado do servidor.
- Uma sessão em nuvem que acessa um arquivo local processa esse conteúdo nos servidores da Anthropic.
- Pastas e ferramentas conectadas definem o que o Cowork pode alcançar, mas não eliminam o risco de injeção de prompt nem o risco de ações com consequências relevantes.
- Plugins e servidores MCP locais expandem a fronteira de confiança.
- Para trabalhos complexos, o Cowork consome mais da alocação do usuário do que um chat comum.
- Disponibilidade e controles podem variar por plano e organização.

## Padrões de fábrica vs. teto alcançável

| Camada | Padrão comum | Teto alcançável |
| --- | --- | --- |
| Configuração | Selecionar o Cowork e descrever uma tarefa | Projetos, plugins, conectores, agendamentos, instruções globais e de pasta |
| Runtime em nuvem | Uma tarefa do Cowork compatível com nuvem roda em infraestrutura gerenciada pela Anthropic | Trabalho com o laptop fechado usando arquivos em nuvem, conectores, skills, plugins e agendamentos |
| Runtime local | Uma tarefa que precisa de pastas locais aprovadas ou aplicativos de desktop depende do caminho de desktop suportado | Fluxos de trabalho mistos de nuvem e desktop com uso do computador, mas dependências locais ainda exigem o dispositivo |
| Modelos | Modelos Claude expostos pelo produto | Limitado aos controles atuais de produto da Anthropic |
| Arquivos | Arquivos da conta ou pastas locais aprovadas | Memória de projeto, arquivos em nuvem, serviços conectados, ponte de desktop |
| Automação | Uma tarefa gerenciada | Tarefas agendadas, plugins, subagentes, despacho pelo celular |
| Propriedade | Harness gerenciado pelo fornecedor | Comportamento personalizado dentro das instruções, skills e plugins expostos |

## Melhor encaixe

- Cliente existente do Claude que quer um agente gerenciado de trabalho do conhecimento.
- Usuário que valoriza arquivos bem-acabados, projetos, conectores e continuidade entre dispositivos.
- Operador não técnico que não quer administrar uma VPS nem fazer manutenção de um gateway.
- Organização já confortável com as fronteiras de administração e de dados da Anthropic.
- Usuário que precisa de um meio-termo entre o chat e o Claude Code.

## Encaixe fraco

- Usuário que precisa de roteamento de modelos independente de provedor.
- Operador que precisa possuir ou alterar profundamente memória, contexto e detalhes internos de execução.
- Fluxo de trabalho que exige um canal de mensageria não suportado pelo produto atual.
- Equipe cujos arquivos locais jamais podem ser processados em uma sessão de nuvem do fornecedor.
- Usuário intenso cuja alocação ou limites de taxa tornam a carga de trabalho instável ou antieconômica.

## Verifique antes de recomendar

- planos elegíveis atuais e rollout por superfície
- modo em nuvem versus local para o fluxo de trabalho exato
- dependência de arquivos e aplicativos locais
- escopo da memória e portabilidade
- suporte exato a conectores, plugins e ações de escrita
- suporte de plataforma ao uso do computador
- comportamento e limites das tarefas agendadas
- modos de permissão e controles de organização
- limites de uso e custo
- compromissos de tratamento e retenção de dados

## Fontes primárias

- Introdução: https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork
- Visão geral da arquitetura: https://support.claude.com/en/articles/14479288-claude-cowork-architecture-overview
- Tarefas agendadas: https://support.claude.com/en/articles/13854387-schedule-recurring-tasks-in-claude-cowork
- Dispatch: https://support.claude.com/en/articles/13947068-assign-tasks-from-anywhere-in-claude-cowork
- Uso do computador: https://support.claude.com/en/articles/14128542-let-claude-use-your-computer-in-cowork
- Plugins: https://support.claude.com/en/articles/13837440-use-plugins-in-claude
- Team e Enterprise: https://support.claude.com/en/articles/13455879-use-claude-cowork-on-team-and-enterprise-plans
- Segurança: https://support.claude.com/en/articles/13364135-use-claude-cowork-safely
