> 🌐 **Tradução não-oficial em português (pt-BR).** Original em inglês: [`ai-assistant-system-advisor/references/research-protocol.md`](../../../../kit/ai-assistant-system-advisor/references/research-protocol.md) — em caso de divergência, vale o original.

# Protocolo de Pesquisa Atual

Os fatos sobre assistentes de IA mudam rápido. A pesquisa faz parte da recomendação, não é uma lista decorativa de fontes.

## Lock de pesquisa

No início de uma recomendação, registre:

- data e fuso horário atuais
- produtos avaliados
- URLs das fontes abertas
- datas de atualização das páginas, quando visíveis
- commit do repositório canônico e última release dos produtos open-source
- fatos que não puderam ser verificados

Use uma linha com data, como: `Verificado em fontes de primeira parte (first-party) em 23 de agosto de 2026.`

## Escada de fontes

Use as fontes nesta ordem:

1. Documentação atual do produto e central de ajuda.
2. Páginas atuais de preços, planos, disponibilidade, segurança, privacidade e termos.
3. README do repositório canônico, docs, última release e código-fonte marcado por tag.
4. Demonstrações oficiais, posts de lançamento ou gravações do produto.
5. Issues do repositório apenas como relatos atribuídos, nunca como comportamento universal do produto.
6. A experiência direta do usuário, claramente rotulada como observação.
7. Sua análise, claramente rotulada como análise.

Não use cobertura de lançamento, posts em redes sociais ou tutoriais de terceiros para sobrepor a documentação oficial do fornecedor atual.

## Checklist de produtos gerenciados

Para Grok Bot, Claude Cowork e ChatGPT Work, verifique:

- planos elegíveis, preço, região, tipo de conta e status de rollout
- superfícies suportadas de desktop, web, mobile e sistemas operacionais
- onde rodam o loop do agente, o código, o navegador e os arquivos
- o que continua quando o notebook é fechado
- como se acessa arquivos locais ou aplicativos locais
- persistência de projeto, arquivo, memória e sessão
- aplicativos, conectores, plugins, skills, rotinas, agendamentos e gatilhos disponíveis
- comportamento de trabalho paralelo ou de orquestração
- modos de aprovação e fronteiras para ações destrutivas
- fronteira de isolamento entre usuários, bots, projetos, sessões e computadores
- limites de uso, créditos, limites de taxa ou outro tipo de medição
- controles de exportação, exclusão, recuperação e administração
- modelos suportados e se a escolha de modelo é fixa, selecionável ou não especificada

## Checklist open-source

Para Hermes Agent e OpenClaw, verifique:

- repositório canônico e licença
- última release estável, data de publicação e commit atual da branch padrão
- caminho de instalação e atualização
- loop principal do agente e montagem de prompts
- design de provedores de modelo e fallback
- camadas de ferramentas, plugins, MCP, navegador e uso do computador
- armazenamento de memória, regras de escrita, recuperação e relação com skills
- modelo de subagentes, orquestração, filas e isolamento
- rotinas, cron, hooks, webhooks e comportamento de entrega
- opções de terminal, container, VPS, serverless e host remoto
- gateway de mensageria e canais suportados
- permissões, manuseio de segredos, sandboxing, auditoria de segurança e postura contra injeção de prompt
- backup, rollback, migração, health checks e recuperação
- o que o usuário precisa operar após a instalação

Inspecione a documentação de implementação ou de arquitetura quando uma alegação de marketing for ampla demais. Registre o arquivo ou a página exatos que sustentam a conclusão.

## Pacote de decisão da pesquisa comparativa

Monte uma linha por candidato com estes campos:

| Campo | O que registrar |
| --- | --- |
| Categoria | Ficar onde está, gerenciado, open-source ou próprio (DIY) |
| Famoso por | O motivo pelo qual chamou atenção |
| Padrão nativo | O que funciona com pouco setup |
| Teto alcançável | O que é possível após configuração ou trabalho personalizado |
| Operador | Fornecedor, usuário, admin de equipe ou misto |
| Execução | Nuvem, local, VPS, container, serverless ou misto |
| Condição de atividade contínua | Condição exata sob a qual o trabalho continua |
| Camada de modelo | Fixo, selecionável, roteável ou do próprio usuário |
| Arquivos e memória | Local de armazenamento, persistência, portabilidade |
| Ferramentas e interfaces | Conectores, navegador, terminal, dispositivos, canais |
| Automação | Agendamentos, gatilhos, monitoramento, passagens de bastão |
| Fronteira de confiança | Isolamento, aprovações, segredos, manuseio de dados |
| Manutenção | Atualizações, depuração, backups, recuperação |
| Custo de troca | O que precisará ser reconstruído ou abandonado |
| Verificação | URLs diretas e data |

## Rótulos de alegações

Rotule alegações importantes nas anotações e na saída final:

- **Fato verificado:** diretamente sustentado por uma fonte oficial do fornecedor atual.
- **Observação do usuário:** comportamento que o usuário relatou pessoalmente.
- **Análise:** uma conclusão extraída de fatos e respostas.
- **Desconhecido:** não documentado, conflitante ou indisponível.

Uma incógnita permanece incógnita. Não pontue como falha e não preencha silenciosamente com um palpite.

## Regras de atualização

Sempre reverifique antes de citar:

- preço ou plano elegível
- release e versão
- limites de uso ou créditos
- disponibilidade de modelos
- conectores e plugins
- suporte a plataformas
- termos de privacidade, treinamento e retenção
- status de beta, preview ou rollout

Se um dossiê e a documentação vigente conflitarem, vence a documentação oficial do fornecedor atual, e a resposta final deve registrar a mudança.
