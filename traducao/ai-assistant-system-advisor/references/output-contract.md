> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/output-contract.md`](../../../../kit/ai-assistant-system-advisor/references/output-contract.md) — em caso de divergência, vale o original.

# Contrato de Entrega

O pacote de decisão final deve ser útil o bastante para que um comprador possa agir sem precisar de mais uma comparação genérica.

## 1. Veredito

Comece com uma frase direta:

`Stay with [current setup]`, `Pilot [candidate] beside your current setup`, `Move to [candidate]` ou `Build a narrow owned layer around [engines]` — isto é, "Fique com [setup atual]", "Pilote [candidato] ao lado do seu setup atual", "Mude para [candidato]" ou "Construa uma camada própria e enxuta em torno de [engines]".

Nomeie o caminho operacional antes do fornecedor.

## 2. Diagnóstico do estado atual

Declare:

- o que o usuário está tentando realizar
- o que está realmente falhando
- se o impulso de migrar é guiado por dor, por requisito ou por hype
- o custo de não fazer nada
- o custo de migrar

## 3. Hierarquia de requisitos

Divida os requisitos em:

- não negociáveis
- de alto valor
- desejáveis
- atração de rede social sem valor comprovado para o fluxo de trabalho

## 4. Tabela de aderência com evidências

Mostre os pesos e as pontuações específicos do usuário. Inclua avaliações separadas de padrões de fábrica e de teto alcançável. Atribua `F`, `O`, `A` ou `U` às pontuações relevantes.

## 5. Recomendação

Explique os três motivos mais fortes pelos quais o caminho escolhido se encaixa. Vincule cada motivo a uma resposta da entrevista ou a uma fonte atual.

## 6. Alternativa consciente do modo

- Na auditoria completa, nomeie o runner-up (segundo colocado) e a restrição exata que o fez perder. Declare qual resposta ou mudança de produto reverteria a ordem.
- Na auditoria de troca, compare `stay` ("ficar") com o candidato nomeado. Não invente uma terceira opção, a menos que ela tenha sido pesquisada.
- No mergulho profundo no produto, declare o modelo operacional alternativo mais forte somente se a decisão do usuário exigir um.
- No blueprint de sistema próprio, compare a construção delimitada com permanecer na stack atual.

## 7. Por que não os demais

Dê uma frase útil por candidato sério que foi realmente pesquisado. Não faça alegativas comparativas sobre produtos fora do escopo de pesquisa do modo. Evite insultar um produto que simplesmente foi otimizado para outro tipo de operador.

## 8. Padrões de fábrica vs. teto alcançável

Para a recomendação e para a alternativa adequada ao modo, declare:

- o que funciona imediatamente
- o que exige configuração ou engenharia
- o que o fornecedor opera
- o que o usuário opera
- o teto realista
- a principal carga oculta

## 9. Inventário de troca (switching ledger)

Use um ledger funcional. Adicione uma linha para cada dependência que a entrevista revelou, especialmente projetos compartilhados e ativos de propriedade da equipe.

| Camada ou ativo | Localização ou dono atual | Localização ou dono de destino | Ação: manter, reconstruir, exportar, testar | Validação e status | Gatilho de rollback |
| --- | --- | --- | --- | --- | --- |
| Arquivos | | | | | |
| Projetos e workspaces | | | | | |
| Propriedade de projetos, membros e acessos | | | | | |
| Instruções e convenções compartilhadas | | | | | |
| Memória | | | | | |
| Skills e prompts | | | | | |
| Ferramentas e conectores | | | | | |
| Rotinas e agendamentos | | | | | |
| Interfaces e canais | | | | | |
| Permissões e segredos | | | | | |
| Hábitos e aceitação da equipe | | | | | |

## 10. Teste reversível de 30 a 60 minutos

Desenhe um teste em torno do trabalho real do usuário. Ele deve:

- reproduzir a falha exata ou o requisito difícil que disparou a decisão
- usar entradas copiadas ou não sensíveis
- evitar apagar ou migrar o sistema atual
- incluir os mesmos critérios de aceitação para os dois sistemas
- registrar tempo de setup, número de intervenções, qualidade da conclusão, tempo de execução e falhas
- parar antes de conceder acesso amplo de escrita ou credenciais de produção

Se a execução com o notebook fechado é o requisito decisivo, o teste precisa realmente fechar ou desconectar o notebook pelo intervalo relevante. Se um conector, colega de equipe, gatilho agendado, arquivo local ou fronteira de aprovação é decisivo, exercite exatamente essa dependência em vez de substituir por uma demonstração genérica.

## 11. Piloto de sete dias

Especifique:

- três fluxos de trabalho reais
- limiar mínimo de sucesso
- tempo máximo aceitável de intervenção e manutenção
- rastreamento de custo ou uso
- fronteira de permissões
- caminho de fallback
- critérios claros de `adopt`, `extend test` ou `reject` — ou seja, adotar, estender o teste ou rejeitar

## 12. Não migre, a menos que

Nomeie o limiar exato que justifica a migração. Exemplo:

`Do not migrate unless the pilot completes the weekly research workflow with at least 30 percent less operator time and no new permission or reliability failure.` — ou seja, "Não migre, a menos que o piloto complete o fluxo semanal de pesquisa com pelo menos 30% menos tempo de operador e nenhuma falha nova de permissão ou confiabilidade."

## 13. Fontes e confiança

Termine com:

- data de verificação
- links diretos de primeira parte (first-party)
- tags de release open-source e repositórios canônicos
- incógnitas não resolvidas
- nível de confiança e o que o elevaria

Mantenha fato verificado, observação do usuário e análise visivelmente separados.
