> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/decision-model.md`](../../../../kit/ai-assistant-system-advisor/references/decision-model.md) — em caso de divergência, vale o original.

# Modelo de Decisão

O propósito da pontuação é expor trade-offs, não fabricar falsa precisão.

## Passo 1: definir a hipótese de caminho operacional

Escolha entre estes caminhos antes de escolher uma marca.

### Ficar onde está

Lidere quando o setup atual conclui o trabalho importante, a dor não está comprovada, o recurso desejado é reproduzível com uma pequena mudança, ou o custo de migração supera o valor provável.

### Assistente gerenciado

Lidere quando o usuário valoriza mais setup baixo, infraestrutura operada pelo fornecedor, interfaces refinadas e integração com ecossistema do que liberdade de modelo ou personalização profunda.

### Runtime open-source

Lidere quando o usuário precisa de inspecionabilidade, roteamento de modelos, canais personalizados, controle de hospedagem ou de um harness (arcabouço de execução) modificável, e tem um operador real para atualizações, segredos, segurança e recuperação.

### Sistema próprio (DIY)

Lidere quando o ativo duradouro do usuário é um fluxo de trabalho diferenciado e ele quer que arquivos, memória, skills, rotinas, permissões e interfaces sobrevivam às trocas de modelo. Exija um responsável pela manutenção e um primeiro marco restrito.

## Passo 2: derivar os pesos a partir da entrevista

Comece com estes pesos padrão e depois mude-os com base nas respostas do usuário. Mantenha o total em 100.

| Dimensão | Peso padrão | Eleve quando |
| --- | ---: | --- |
| Aderência ao fluxo de trabalho central | 20 | O usuário cita um trabalho ligado a receita, operações ou missão crítica |
| Aderência a ecossistema e conectores | 15 | Os aplicativos, controles de administração ou hábitos de equipe existentes têm substituição custosa |
| Aderência de operador e manutenção | 15 | O usuário tem pouco conforto técnico ou não há responsável pelo sistema |
| Confiança, privacidade e permissões | 10 | Dados sensíveis ou ações de alto impacto estão envolvidos |
| Atividade contínua e confiabilidade | 10 | O trabalho precisa continuar sem o dispositivo do usuário |
| Propriedade e flexibilidade de modelo | 10 | Portabilidade ou roteamento de modelos é requisito obrigatório |
| Interfaces e canais | 10 | Telefone, terminal, mensageria, navegador ou aplicativos locais são essenciais |
| Custo de troca e reversibilidade | 10 | A memória, skills, rotinas ou processos de equipe existentes são substanciais |

Mostre os pesos finais e uma frase explicando qualquer ajuste grande.

## Passo 3: pontuar com evidência

Dê nota a cada candidato de 0 a 5 em cada dimensão:

- `0`: contradiz um requisito inegociável
- `1`: possível apenas por meio de uma solução alternativa drástica ou de um ônus inaceitável
- `2`: desencontro significativo
- `3`: adequado
- `4`: forte aderência
- `5`: aderência nativa excepcionalmente forte
- `U`: desconhecido ou não verificado

Acrescente uma nota de evidência:

- `F`: fato atual de primeira parte (first-party)
- `O`: comportamento observado pelo usuário
- `A`: análise feita a partir de fatos e respostas do usuário
- `U`: incógnita não resolvida

Exemplo: `4F` significa forte aderência sustentada por uma fonte oficial do fornecedor e atual. `3A` significa aderência adequada com base em análise. Não converta `U` em zero.

## Passo 4: aplicar restrições rígidas

Um candidato não pode vencer se viola um requisito inegociável, mesmo com uma pontuação ponderada alta. Restrições rígidas comuns incluem:

- plataforma necessária indisponível
- dado ou limite administrativo sem suporte
- nenhuma forma aceitável de alcançar arquivos locais ou aplicativos locais
- nenhum caminho sempre ativo para o trabalho exigido
- exigência de manutenção acima da capacidade de operador disponível
- modelo fixo quando a portabilidade de modelos é obrigatória
- preço acima de um teto de orçamento firme
- migração destrutiva ou irreversível sem exportação ou fallback

## Passo 5: comparar padrões de fábrica e tetos alcançáveis

Crie duas colunas separadas:

- **Aderência aos padrões de fábrica:** O que um usuário normal recebe após um setup comum.
- **Aderência ao teto alcançável:** O que um operador habilidoso poderia alcançar com configuração, hospedagem, plugins, código ou arquitetura personalizada.

Não puna um runtime open-source configurável por um setup fraco como se ele fosse um produto fixo. Não credite a um produto gerenciado um teto personalizado hipotético que ele não expõe.

## Passo 6: calcular a realidade da migração

Faça o inventário do que muda:

- arquivos e estrutura de pastas
- contexto salvo e memória
- skills, prompts, plugins e MCPs
- autorizações de aplicativos e segredos
- rotinas, gatilhos e monitoramento
- interfaces de usuário e canais de mensageria
- políticas de administração e aprovações
- treinamento e hábitos de equipe
- backup, rollback e resposta a incidentes

Classifique o esforço de migração como `small` (pequeno), `meaningful` (significativo) ou `rebuild` (refazer). Indique a evidência.

## Passo 7: usar os limiares de decisão

- **Ficar:** O candidato não melhora um problema de peso alto em pelo menos um nível claro, ou o ganho não supera o custo de troca.
- **Testar:** O candidato parece melhor, mas um ou mais fatos críticos ou resultados de fluxo de trabalho seguem sem comprovação.
- **Migrar:** O piloto atinge o limiar de sucesso, as restrições rígidas são satisfeitas e o ganho é grande o suficiente para justificar reconstruir as camadas afetadas.
- **Construir:** Nenhum padrão gerenciado ou open-source satisfaz o fluxo de trabalho diferenciado, e o usuário tem um responsável crível, orçamento de manutenção e um marco restrito.

## Armadilhas comuns

- Tratar `works in the cloud` ("funciona na nuvem") como exclusividade sem verificar VPS, serverless e sessões gerenciadas concorrentes.
- Tratar `multi-agent` como uma capacidade única, em vez de verificar isolamento, estado compartilhado, roteamento, aprovações e tratamento de falhas.
- Tratar muitos conectores como úteis quando falta justamente o conector de que o usuário precisa.
- Tratar memória como um item de checklist sem verificar regras de escrita, editabilidade, escopo, portabilidade e risco de envenenamento.
- Tratar um modelo familiar como prova de um sistema operacional melhor.
- Ignorar que o setup atual do usuário talvez já contenha o valor conquistado a duras penas.
