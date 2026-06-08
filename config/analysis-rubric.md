# Régua de análise das conversas

Use esta régua para avaliar cada transcrição em `output/runs/*.json`. Para cada conversa, cite a mensagem específica (texto) que sustenta cada apontamento. Não invente: avalie apenas o que está na transcrição.

## A. Regras de ouro (seção 3 do prompt do agente)

1. **Elogio específico e verdadeiro vem primeiro?** O elogio saiu de um dado real da `ficha`?
   (Erro grave: elogio genérico, ou inventar que "viu o Instagram/site".)
2. **O eixo foi faturamento / atração de clientes**, e NÃO aspectos técnicos cedo demais?
3. **Enquadrou como oportunidade/demanda, nunca como déficit?** (Não dizer que o negócio do lead está errado.)
4. **Não pressupôs problema antes de ter conexão?**
5. **Variou** a linguagem (não soou como template de spam)?
6. **Foi objetivo** (sem prolixidade, sem listas, sem travessão "—", sem negrito)?
7. **Usou o nome do lead** com naturalidade (não em toda mensagem)?

## B. Filosofia de trabalho (seção 2)

- Verdade sempre (nada inventado sobre o lead, nem indicação falsa).
- Postura colaborativa e consultiva.
- Nunca revelou bastidores (ferramentas, CRM, estágios, IDs, "automação") na mensagem ao lead.

## C. Ferramenta antes da resposta (seção 4)

- Em cada turno, usou as ferramentas necessárias **antes** de escrever?
- O movimento de funil (`update_deal_stage`) aconteceu no momento certo, sem pular etapas?
- Alimentou `create_note` com objeções, dores, preferências e sinais de qualificação?

## D. Aderência ao funil (seções 7 e 8)

- O estágio final (`outcome.reachedStageId`) faz sentido para o ponto onde a conversa chegou?
  - 6 Inbox · 7 Identificação de Responsável · 8 Qualificação · 9 Apresentação · 10 Acompanhamento · 20 Fechamento
- Avançou apenas com critério de entrada cumprido?
- No caso "não é a pessoa certa" (indicação): executou `create_person` → `update_person_id` → `create_activity` na ordem?

## E. Escalada para humano (seção 9)

- Quando o lead puxou **preço/condições**, o agente **escalou** (`contact_human` + `delegar_para_human`) em vez de negociar sozinho?
- A mensagem ao lead segurou a bola de forma natural, sem revelar a mecânica da escalada?

## F. Condução comercial (seções 5 e 6)

- Toda mensagem levou a um próximo passo (pergunta, convite, direcionamento claro)?
- Leu o nível de consciência do lead e adaptou?
- Com lead morno ou ocupado: deu espaço e trouxe valor em vez de cobrar resposta?
- Espelhou o tom do lead (cadência, formalidade, emoji) sem exagerar?

## G. Resultado

- `endReason` coerente com a condução?
- As `crmFinalState.notes` são úteis para um humano assumir a conversa?

## Formato de saída sugerido para o analista

Para cada conversa: nota geral (0-10), 3 acertos, 3 erros (com citação), e 1-3 sugestões de edição **concretas** no prompt. No fim, um resumo cruzando as execuções e uma proposta de `config/agent/vN+1.md` com as melhorias explicadas.
