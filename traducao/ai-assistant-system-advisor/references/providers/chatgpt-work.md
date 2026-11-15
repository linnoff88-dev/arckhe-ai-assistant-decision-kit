> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/providers/chatgpt-work.md`](../../../../kit/ai-assistant-system-advisor/references/providers/chatgpt-work.md) — em caso de divergência, vale o original.

# Dossiê ChatGPT Work

Lock de pesquisa: 23 de agosto de 2026.

ChatGPT Work é um agente de trabalho gerenciado no ecossistema OpenAI. Verifique elegibilidade de plano, rollout, uso, aplicativos, controles de modelo e suporte de plataforma antes de recomendá-lo.

## Por que ele se tornou notável

O Work fica entre o ChatGPT conversacional rápido e o foco em desenvolvimento de software do Codex. Ele foi projetado para trabalhos mais longos e com múltiplas etapas e para entregas finalizadas como pesquisas, documentos, planilhas, apresentações, relatórios e Sites.

Seu principal valor é a combinação de uma conta ChatGPT familiar, aplicativos conectados, projetos, sessões em nuvem, trabalho agendado, criação de arquivos e entregas revisáveis. Ele não é automaticamente melhor que o Codex para sistemas técnicos, nem melhor que o Cowork para toda tarefa de trabalho do conhecimento.

## Modelo operacional atual

### Superfícies

A documentação atual da OpenAI descreve o Work no desktop, na web e no celular para contas elegíveis. Chats de Work em nuvem sincronizam entre essas superfícies. O Codex continua sendo uma experiência separada, com o acesso remoto ao Codex suportado exposto pelo aplicativo móvel, em vez de se tornar um chat normal de Work na web.

### Nuvem e arquivos locais

O Work em nuvem pode continuar e sincronizar sem tratar o laptop do usuário como o runtime. Arquivos e pastas locais exigem o aplicativo de desktop e acesso local explícito. O Work na web e no celular não consegue acessar diretamente arquivos locais não sincronizados.

Saídas locais podem permanecer no projeto ou na pasta local. Arquivos criados na nuvem podem ser armazenados na Library da conta, onde disponível. Verifique o comportamento exato de armazenamento e retenção para o plano do usuário.

## Harness de trabalho (arcabouço de execução)

### Projetos e contexto

Projetos agrupam chats, arquivos e instruções. São a principal camada de continuidade para o trabalho gerenciado em andamento. Memória da conta, instruções de projeto, dados de aplicativos e arquivos enviados são superfícies separadas e não devem ser tratados como um único sistema de memória intercambiável.

### Aplicativos, plugins e ações

Aplicativos do ChatGPT conectam dados e ações externas. A terminologia atual de produto da OpenAI coloca os aplicativos dentro de um sistema de plugins mais amplo, que pode empacotar skills, aplicativos e modelos de aplicativos. Dependendo do aplicativo e do plano, as capacidades podem incluir busca, deep research, sincronização, UI interativa e ações de escrita.

As permissões podem ser configuradas para sempre perguntar, perguntar em mudanças ou ações importantes ou permitir operação mais automática quando disponível. Administradores do workspace podem restringir aplicativos, ações, escopos e acesso de usuários.

Verifique o aplicativo e a ação necessários. O tamanho do catálogo não prova adequação ao fluxo de trabalho.

### Documentos, planilhas e apresentações

O Work pode criar e editar entregas corporativas comuns a partir de instruções, material-fonte anexado, arquivos de referência e modelos reutilizáveis. A documentação atual descreve suporte nativo a Google Docs, Sheets e Slides quando o aplicativo Google Workspace correspondente está habilitado.

A relação do desktop com o Microsoft Excel pode passar pelo Codex e pelo complemento ChatGPT for Excel. No lock de pesquisa, a documentação da OpenAI dizia que o PowerPoint não estava incluído nesse fluxo específico de Work no desktop no lançamento. Verifique o suporte atual em vez de generalizar a partir da exportação de arquivos.

### Agendamento e monitoramento

O Work pode executar uma vez, repetir em um agendamento ou gatilho e monitorar mudanças por meio de Scheduled Tasks. Verifique o catálogo atual de gatilhos, limites do plano, comportamento de aprovação e se a tarefa depende de um recurso local.

### Orquestração

O Work gerenciado pode planejar e executar tarefas com múltiplas etapas e pode usar ferramentas especializadas ou agentes expostos pelo produto. Não afirme que a orquestração está ausente apenas porque a interface é mais simples que a de um harness open-source. Verifique o comportamento real de que o usuário precisa.

## Uso, permissões e confiança

A orientação atual da OpenAI diz que o Work segue a mesma estrutura de uso do Codex, embora o consumo real varie por tarefa. Isso torna limites e créditos uma verificação obrigatória para fluxos de trabalho intensos ou recorrentes.

Fronteiras principais:

- O Work em nuvem e o Work local não têm o mesmo alcance de arquivos.
- As permissões de aplicativo regem quando as ações conectadas pedem aprovação, não o escopo completo que o aplicativo externo concedeu durante a autorização.
- Projetos, Library, aplicativos conectados e pastas locais têm comportamentos diferentes de armazenamento e exclusão.
- Administradores do workspace podem alterar a disponibilidade e os controles de ações.
- Planilhas, documentos e apresentações gerados ainda exigem revisão de fórmulas, fontes, estrutura e ações sensíveis.
- Os controles atuais de seleção de modelo e raciocínio devem ser verificados no produto em si e na documentação oficial.

## Padrões de fábrica vs. teto alcançável

| Camada | Padrão comum | Teto alcançável |
| --- | --- | --- |
| Configuração | Selecionar o Work e fornecer a ele arquivos e uma entrega | Projetos, plugins, aplicativos conectados, modelos, tarefas agendadas |
| Runtime | Work em nuvem gerenciado | Fluxos de trabalho mistos de nuvem e desktop, acesso a projeto local |
| Modelos | Modelos expostos pela experiência atual do Work | Limitado aos controles atuais de produto da OpenAI |
| Arquivos | Uploads e arquivos gerados | Library, projetos, arquivos nativos do Google, arquivos locais do desktop |
| Automação | Uma tarefa com múltiplas etapas | Agendamentos, gatilhos, monitoramento, ações conectadas |
| Teto técnico | Trabalho gerenciado de entregas | Codex e SDKs continuam sendo caminhos separados para sistemas técnicos próprios |

## Melhor encaixe

- Cliente existente do ChatGPT que quer um agente de trabalho gerenciado sem um ecossistema novo.
- Usuário focado em pesquisa e em entregas corporativas finalizadas.
- Equipe que já usa aplicativos, plugins, projetos ou controles de workspace da OpenAI.
- Comprador que valoriza continuidade entre web e celular e baixa carga de infraestrutura.
- Usuário disposto a trocar a posse profunda do harness por um produto gerenciado familiar.

## Encaixe fraco

- Usuário que precisa de um harness de agente inspecionável e independente de provedor.
- Fluxo de trabalho que depende de arquivos ou aplicativos locais não suportados enquanto o dispositivo está offline.
- Uso recorrente intenso que atinge repetidamente limites do plano ou créditos.
- Organização cujas ações de aplicativo necessárias ou fronteiras de dados não estão aprovadas.
- Construtor cuja necessidade principal é uma camada operacional interna personalizada e duradoura, em vez de entregas gerenciadas.

## Verifique antes de recomendar

- plano atual e disponibilidade regional
- controles de modelo e raciocínio
- alocação de uso, créditos e limites de tarefas
- comportamento de arquivos na nuvem versus local
- aplicativos, plugins, ações e modos de aprovação necessários
- comportamento de projeto, Library, memória e exclusão
- limites de agendamentos, gatilhos e monitoramento
- suporte a saídas de documento, planilha, apresentação e Site
- administração do workspace e controles de dados
- relação atual entre Work, Codex e acesso remoto pelo celular

## Fontes primárias

- Work e Codex: https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex
- Entregas: https://help.openai.com/en/articles/20001278-creating-and-editing-documents-spreadsheets-and-presentations-with-chatgpt-work
- Aplicativos no ChatGPT: https://help.openai.com/en/articles/11487775-apps-in-chatgpt
- Plugins no ChatGPT e no Codex: https://help.openai.com/en/articles/20001256-plugins-in-chatgpt-and-codex
- Library de arquivos: https://help.openai.com/en/articles/20001052-library-for-chatgpt
- Tipos de arquivo suportados: https://help.openai.com/en/articles/8983675-what-types-of-files-are-supported
- ChatGPT for Excel e Google Sheets: https://help.openai.com/en/articles/20001063-chatgpt-for-excel-and-google-sheets

