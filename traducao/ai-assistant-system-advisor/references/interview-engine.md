> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/interview-engine.md`](../../../../kit/ai-assistant-system-advisor/references/interview-engine.md) — em caso de divergência, vale o original.

# Motor de Entrevista Adaptativa

A entrevista precisa trazer informação suficiente para mudar a decisão. Ela não é um teste de personalidade e não deve fazer todas as perguntas possíveis.

## Adaptador de interação

### Claude Code

Use `AskUserQuestion`. Faça no máximo três perguntas em uma única chamada. Ofereça escolhas concretas mais uma válvula de escape em texto livre que seja realmente útil. Use seleção múltipla apenas quando mais de uma resposta puder ser verdadeira, como tipos de trabalho ou interfaces exigidas. Aguarde a resposta antes da próxima chamada.

### Codex

Use `request_user_input` quando exposto no modo atual. Faça de uma a três perguntas curtas por chamada e coloque primeiro a opção neutra mais provável. Converta diagnósticos abertos em escolhas forçadas honestas, use a opção de texto livre disponibilizada automaticamente para nuances e não invente uma falsa dicotomia. Se a ferramenta não estiver disponível, faça um bloco numerado compacto na conversa e pare até o usuário responder.

### ChatGPT e outras interfaces de chat

Faça uma rodada curta numerada em uma conversa normal. Diga explicitamente que a recomendação virá depois das respostas. Não acrescente um vencedor provisório abaixo das perguntas.

## Rodada 1: diagnosticar a mudança

Primeiro, extraia as respostas já presentes na mensagem do usuário. Nunca refaça uma pergunta já respondida. Faça no máximo três perguntas sem resposta por vez e adapte os exemplos ao contexto do usuário.

1. **Sistema atual:** O que você usa hoje, e o que já construiu em torno disso?
2. **Falha e consequência:** Que trabalho recorrente específico está não confiável, impossível ou caro demais hoje, e o que isso custa em tempo, dinheiro, risco ou entregas perdidas?
3. **Teste do hype:** Se as redes sociais parassem de falar dos novos assistentes por 30 dias, você ainda iria querer mudar? Por quê?

Se o usuário não conseguir identificar uma falha recorrente ou uma consequência relevante, torne `stay put` (ficar onde está) a hipótese principal. Continue a entrevista, porque ainda pode existir um requisito futuro válido.

## Rodada 2: resolver a arquitetura

Pergunte apenas o que permanece sem resposta e pode mudar o caminho.

### Trabalho e interfaces

- Quais três fluxos de trabalho importam mais?
- A saída principal é pesquisa, decisões, mensagens, documentos, planilhas, apresentações, código, trabalho no navegador, operações com arquivos ou monitoramento?
- Por onde o assistente precisa estar acessível: desktop, web, telefone, terminal, Slack, Telegram, e-mail ou outro canal?
- Precisa continuar funcionando com o notebook fechado? Em caso afirmativo, o trabalho pode depender de arquivos locais ou aplicativos locais?

### Gravidade existente

- Qual ecossistema já está pago e inspira confiança: Claude, ChatGPT, Grok e Cursor, Google, Microsoft, ferramentas open-source ou nenhum?
- Quais arquivos, projetos, memórias, skills, conectores, permissões, trabalhos agendados e hábitos de equipe precisariam migrar?
- Quem, além do usuário, depende do setup atual?

### Adequação do operador

- O usuário usa terminal e GitHub com conforto?
- Essa pessoa consegue implantar e proteger um VPS ou container?
- Quem será o responsável por atualizações, rotinas que falharem, backups, rotação de segredos, logs e recuperação daqui a três meses?
- Quantas horas por mês serão dedicadas realisticamente à manutenção do sistema?

### Controle e confiança

- A escolha de modelo é um requisito ou apenas uma preferência?
- Memória, prompts, skills e logs precisam ser inspecionáveis e editáveis?
- São exigidos dados exclusivamente locais, controles regionais, políticas de administrador, logs de auditoria ou compromissos de retenção de dados?
- Quais ações o assistente pode tomar sem aprovação?

### Economia

- Qual é o teto mensal de orçamento?
- O usuário busca o menor custo financeiro, o menor tempo de operador ou a maior alavancagem de longo prazo?
- O que tornaria um teste bem-sucedido o suficiente para justificar a migração?

## Rodada 3: checagens de contradição

Use uma terceira rodada apenas quando as respostas entrarem em conflito. Exemplos:

- Quer manutenção zero e roteamento de modelos irrestrito.
- Quer execução com o notebook fechado, mas exige arquivos locais fora de sincronização e um desktop off-line.
- Quer isolamento forte, mas planeja dar a todos os agentes um único login e sistema de arquivos compartilhados.
- Quer propriedade completa, mas não consegue alocar um operador.
- Quer uma migração rápida, mas tem anos de memórias, skills e processos de equipe insubstituíveis.

Nomeie o conflito de forma direta e pergunte qual lado tem prioridade.

## Escolhas forçadas de alta informação

Use estas perguntas quando o usuário der respostas vagas:

- **Qual dor você pagaria para eliminar?** Tempo de setup, manutenção, limites de taxa, lock-in de modelo, lacunas de conectores, memória fraca, canais ausentes ou entregas não confiáveis.
- **Qual carga você prefere herdar?** Limites do fornecedor, custo de assinatura, manutenção de infraestrutura ou manutenção de um sistema próprio (DIY).
- **Qual falha é a menos aceitável?** Trabalho parado, ação errada, exposição de dados, lock-in, custo inesperado ou um sistema difícil de reparar.
- **Qual ativo precisa sobreviver a uma troca de provedor?** Arquivos, memória, skills, rotinas, interfaces, ou nada por enquanto.

## Teste de conclusão da entrevista

Não recomende até conseguir enunciar todos os itens abaixo:

- o sistema atual do usuário
- o trabalho recorrente que importa
- a falha concreta ou o requisito não atendido
- o local de execução e as interfaces exigidos
- a gravidade do ecossistema do usuário
- a capacidade de manutenção do usuário
- a fronteira de confiança ou privacidade do usuário
- o custo de troca do usuário
- a prioridade de orçamento ou de custo do usuário
- o limiar de sucesso para um teste reversível
