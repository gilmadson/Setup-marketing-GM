# Estratégia: Personas do Comprador

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 01-estrategia

---

## Quando usar / Quando não usar

**Usar quando:**
- Início de campanha — antes de definir segmentação, copy ou criativos
- Campanha com baixa taxa de conversão — persona errada pode ser a causa
- Time de marketing e vendas com visões diferentes sobre quem é o cliente

**Não usar quando:**
- Produto genérico com público amplíssimo (ex: commodity) — segmentação por comportamento resolve sem persona formal
- Dados insuficientes — sem ao menos 20 clientes para entrevistar ou analisar, persona é invenção (usar hipótese explícita e validar)

---

## Pré-requisitos

```
- Acesso a clientes existentes para análise (histórico de vendas, CRM, entrevistas)
- Alternativa sem entrevistas: análise do Audience Insights do Meta, comentários nas redes, avaliações no Google
- Objetivo da campanha definido (persona muda conforme o objetivo)
```

---

## Padrões e convenções

### Persona de Marketing vs Persona de UX — diferenças

```
Persona de UX (setup-skills-GM):
  → Foco: como a pessoa usa o produto
  → Pergunta central: "O que o usuário quer fazer dentro do sistema?"
  → Usado por: designers e devs para tomar decisões de interface

Persona de Marketing / Compradora:
  → Foco: como e por que a pessoa decide comprar
  → Pergunta central: "O que faz esta pessoa abrir a carteira?"
  → Usado por: gestores de tráfego, copywriters, estrategistas

As personas podem ser baseadas no mesmo arquétipo de pessoa,
mas com informações diferentes — complementares, não redundantes.
```

### Estrutura da Persona de Comprador

```
1. Perfil demográfico e de contexto
   → Não só idade e gênero — incluir situação de vida que afeta a compra
   → Exemplos: "tem filhos pequenos", "trabalha em home office", "recém promovido"

2. Objetivo principal (Job to Be Done de compra)
   → "Quando [situação], quero [ação] para que eu possa [resultado]"
   → Ex: "Quando preciso escalar minha loja mas não tenho tempo, quero uma agência
         que cuide do tráfego para que eu possa focar no produto."

3. Dores (o que a impede ou frustra hoje)
   → Dores relacionadas ao problema que o produto resolve
   → Ex: "Já investi R$ 3k em tráfego e não tive retorno", "não entendo os relatórios"

4. Gatilhos de compra (o que faz agir)
   → O que acontece na vida dela que a faz procurar uma solução agora?
   → Ex: Black Friday chegando, lançamento de produto, perdeu cliente para concorrente

5. Objeções (por que não compra)
   → O que a impede de fechar na hora?
   → Ex: "preço alto", "não conheço a marca", "já tentei e não funcionou", "preciso aprovar com sócio"

6. Canais onde está presente
   → Onde consome conteúdo, onde pesquisa antes de comprar, onde toma decisão
   → Ex: Instagram para descoberta, YouTube para aprofundamento, Google para pesquisa antes de comprar

7. Linguagem e vocabulário
   → Que palavras usa para descrever o problema?
   → Ex: diz "anunciar no Instagram" não "mídia paga em social"; diz "vender mais" não "aumentar conversão"
   → Usar a linguagem DELA no copy — não o jargão técnico do mercado
```

### JTBD de compra — Jobs to Be Done aplicado ao marketing

```
Formato: "Quando [situação/gatilho], quero [produto/solução] para que eu possa [resultado desejado]."

Exemplos por produto:

  Software de gestão financeira:
  "Quando perco horas conciliando planilhas no final do mês,
   quero um sistema que faça isso automaticamente
   para que eu possa focar em crescer o negócio."

  Curso de inglês corporativo:
  "Quando trava no inglês em reuniões com clientes estrangeiros,
   quero falar com fluência suficiente para liderar reuniões
   para que eu possa ser promovido ao cargo de gerente regional."

  Agência de tráfego pago:
  "Quando percebo que meus anúncios estão gerando cliques mas não vendas,
   quero um especialista que resolva isso sem eu precisar aprender tudo
   para que eu possa ter previsibilidade de receita."

O JTBD revela o que o cliente está "contratando" o produto para fazer.
É diferente das features — é o resultado de vida que ele busca.
```

### Como levantar dados da persona (sem entrevistas formais)

```
Fonte 1 — CRM e histórico de vendas:
  → Quem são os clientes com maior LTV? Qual perfil?
  → Quais objeções aparecem antes do fechamento?
  → Qual canal gerou os melhores clientes (não mais volume — melhor qualidade)?

Fonte 2 — Meta Audience Insights:
  → Analisar quem interage com o perfil da marca
  → Interesses, comportamentos, demografias dos engajadores

Fonte 3 — Comentários e avaliações:
  → Google Meu Negócio, Reclame Aqui, avaliações de produto
  → Os comentários positivos revelam os benefícios que mais importam
  → Os negativos revelam objeções não resolvidas

Fonte 4 — Concorrentes:
  → Comentários nos anúncios dos concorrentes na Meta Ad Library
  → Perguntas frequentes no Instagram/YouTube do concorrente
  → Reviews dos produtos concorrentes no Mercado Livre, Amazon

Fonte 5 — Busca orgânica:
  → Google Search Console: que termos trazem tráfego para o site?
  → AnswerThePublic / AlsoAsked: que perguntas o público faz?
  → Reddit, Quora, grupos do Facebook: conversas orgânicas sobre o problema
```

### Objeções — como usar no copy e nos criativos

```
Cada objeção é uma oportunidade de criativo ou copy.

Objeção: "É caro"
  Copy: "Entendemos que R$ 497 parece muito. Mas clientes que aplicaram o método
         recuperam esse investimento em média em 2 sprints de campanha."

Objeção: "Já tentei e não funcionou"
  Copy: "Se você já investiu em tráfego sem retorno, não é sua culpa —
         provavelmente faltou [X que nosso método faz diferente]."

Objeção: "Não conheço a marca"
  Criativo: depoimento de cliente real em vídeo + caso de sucesso com números

Objeção: "Preciso pensar / aprovar com alguém"
  Criativo: urgência real (vagas limitadas, desconto expira em X dias)
  Copy: "Leve para mostrar ao seu sócio: aqui está o nosso case comparando
         antes e depois de 3 meses com nosso método."
```

---

## Templates prontos

### Card de Persona de Comprador

```markdown
## Persona: [Nome Fictício]

| Atributo | Valor |
|----------|-------|
| Perfil | [cargo / situação de vida] |
| Contexto | [empresa / setor / momento de vida] |
| Faixa etária | [ex: 30-45 anos] |
| Localização | [cidade / estado / nacional] |

### Job to Be Done
"Quando [situação/gatilho], quero [ação/produto] para que eu possa [resultado]."

### Dores (o que a impede hoje)
- [dor 1 — diretamente relacionada ao que o produto resolve]
- [dor 2]
- [dor 3]

### Gatilhos de compra (o que a faz agir agora)
- [gatilho 1 — evento ou situação que cria urgência]
- [gatilho 2]

### Objeções (por que não compra de imediato)
- [objeção 1] → resposta no copy: [como rebater]
- [objeção 2] → resposta no copy: [como rebater]

### Canais onde está presente
- Descoberta: [ex: Instagram Reels, TikTok]
- Pesquisa: [ex: Google, YouTube]
- Decisão: [ex: WhatsApp, e-mail, conversa com vendedor]

### Linguagem que usa
- Diz "[termo dela]" não "[jargão técnico]"
- Exemplos de frases reais: "[citação de entrevista ou comentário]"

### Quem NÃO é esta persona
[Perfil que parece similar mas compra por razões diferentes — excluir da segmentação]
```

---

## Checklist de qualidade

- [ ] Persona baseada em dados reais (entrevistas, CRM, analytics) — não em suposições
- [ ] JTBD definido: situação + desejo + resultado
- [ ] Objeções mapeadas com resposta de copy para cada uma
- [ ] Gatilhos de compra identificados (usados para definir timing e urgência)
- [ ] Linguagem da persona documentada — copywriter vai usar as palavras dela
- [ ] Canais de descoberta, pesquisa e decisão separados (impacta onde anunciar em cada etapa do funil)
- [ ] Quem NÃO é a persona definido — para excluir da segmentação e economizar budget

---

## Armadilhas comuns

**Persona demográfica:** "mulher, 35 anos, ensino superior, classe B" — isso não diz nada sobre por que ela compraria. Comportamento e JTBD importam mais que dados demográficos.

**Uma persona para tudo:** empresa com 3 produtos diferentes usando a mesma persona para todos. Cada produto resolve um problema diferente — personas diferentes.

**Persona inventada:** "nosso cliente é alguém que valoriza qualidade" — sem entrevistas ou dados. Persona de suposição gera copy genérico que não converte.

**Objeções não respondidas no criativo:** anúncio bonito que não aborda as principais razões pelas quais as pessoas não compram. Objeções não tratadas no criativo são tratadas no momento do pagamento — aí já é tarde.

**Ignorar quem não é a persona:** segmentação muito ampla inclui pessoas que nunca vão comprar. Definir exclusões é tão importante quanto definir o público.

---

## Referências confiáveis

- [Buyer Persona Institute](https://buyerpersona.com/) — metodologia de entrevistas, verificado 2026-05-01
- [Jobs to Be Done — Intercom](https://www.intercom.com/blog/where-do-you-find-the-jobs-to-be-done/) — verificado 2026-05-01
- [AnswerThePublic](https://answerthepublic.com/) — perguntas reais do público sobre qualquer tema, verificado 2026-05-01

---

## Versão e histórico
→ Ver [estrategia-personas-comprador.changelog.md](estrategia-personas-comprador.changelog.md)
