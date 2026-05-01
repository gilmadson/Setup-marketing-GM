# Estratégia: Budget e Distribuição de Canais

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 01-estrategia

---

## Quando usar / Quando não usar

**Usar quando:**
- Distribuindo budget entre 2 ou mais canais — evitar decisão por intuição
- Resultado abaixo do esperado — redistribuir para onde está performando melhor
- Budget aumentou ou diminuiu — recalcular a alocação proporcionalmente

**Não usar quando:**
- Canal único (ex: só Google Search) — todo o budget vai para um lugar, não há distribuição
- Budget abaixo de R$ 1.500/mês — concentrar em 1 canal; distribuir gera fragmentação sem dados suficientes

---

## Pré-requisitos

```
- Objetivo da campanha definido (ver estrategia-briefing-campanha)
- Funil mapeado (ver estrategia-funil-marketing)
- KPIs e metas por canal definidos
- Histórico de performance em campanhas anteriores (se existir)
```

---

## Padrões e convenções

### Regra 70/20/10 — alocação de budget

```
70% → Canal principal (já validado, melhor performance histórica)
      Objetivo: escalar o que funciona

20% → Canal secundário (em crescimento ou com boa performance)
      Objetivo: diversificar, reduzir dependência do canal principal

10% → Testes (novo canal, novo formato, nova segmentação)
      Objetivo: descobrir a próxima oportunidade

Exemplo com R$ 10.000/mês:
  R$ 7.000 → Google Search + PMax (canal validado com ROAS 4x)
  R$ 2.000 → Meta Ads (em crescimento, CPL aceitável)
  R$ 1.000 → TikTok Ads (testando — ainda sem dados suficientes)

Quando mover de 10% → 20%:
  → Teste gerou CPL/ROAS dentro da meta por 2 semanas consecutivas
  → Volume suficiente para ser estatisticamente relevante (> 30 conversões)

Quando mover de 20% → 70%:
  → Canal secundário superou o principal por 30 dias consecutivos
  → Principal começou a saturar (frequência alta, custo crescendo)
```

### CPL máximo suportável — cálculo

```
Fórmula:
  CPL máximo = Ticket médio × Taxa de fechamento × Margem

Exemplo:
  Ticket médio: R$ 2.000
  Taxa de fechamento: 30% (de cada 10 leads, 3 viram clientes)
  Margem: 40%

  Receita por lead = R$ 2.000 × 30% = R$ 600
  CPL máximo = R$ 600 × 40% = R$ 240

  Com CPL de até R$ 240, a campanha é lucrativa.
  CPL acima de R$ 240 = está operando no prejuízo.

Para e-commerce (ROAS mínimo):
  ROAS mínimo = 1 / Margem bruta
  Margem 30% → ROAS mínimo = 1/0,3 = 3,33x
  Margem 40% → ROAS mínimo = 1/0,4 = 2,5x

  Abaixo do ROAS mínimo = prejuízo operacional.
  ROAS alvo = ROAS mínimo × 1,5 (para cobrir overhead, impostos, devolução)
```

### Budget mínimo por canal — para ter dados suficientes

```
Meta Ads (Feed/Stories/Reels):
  Mínimo para aprendizado: R$ 50/dia (R$ 1.500/mês)
  Mínimo recomendado: R$ 100-200/dia por Ad Set com objetivo de conversão
  Abaixo de R$ 30/dia: algoritmo não sai da fase de aprendizado (precisa de ~50 conversões/semana)

Google Search:
  Mínimo para aprendizado: R$ 50-80/dia (depende do CPC da palavra-chave)
  Mínimo por campanha com Smart Bidding: R$ 3-5 × CPC médio da palavra-chave × 10/dia
  Exemplo: CPC médio R$ 5 → budget mínimo R$ 50/dia por campanha

Google PMax / Shopping:
  Mínimo: R$ 100/dia (PMax precisa de dados para otimizar)
  Ideal: ≥ 30 conversões/mês para o algoritmo ter dados suficientes

TikTok Ads:
  Mínimo por Ad Group: R$ 50/dia (restrição da plataforma)
  Mínimo para aprendizado real: R$ 100/dia

LinkedIn Ads:
  CPCs e CPMs mais altos — mínimo R$ 150-200/dia para ter volume B2B

Email Marketing:
  Custo não é por clique mas por lista e disparos — R$ 100-300/mês (ferramentas como RD Station, Mailchimp)
```

### Sazonalidade — quando aumentar ou reduzir budget

```
Períodos de alta (aumentar budget 30-100% no período):
  Janeiro: retomada pós-festas — produtos de organização, educação, saúde
  Março/Abril: Páscoa — alimentação, turismo, entretenimento
  Maio: Dia das Mães (maior data do varejo brasileiro após Natal)
  Junho: Dia dos Namorados + Festas Juninas (alimentação, bebidas, turismo)
  Agosto: Dia dos Pais
  Novembro: Black Friday + início Natal (maiores picos do ano)
  Dezembro: Natal + saldão de ano novo

Períodos de baixa (reduzir ou manter mínimo):
  Janeiro (1ª quinzena): pós-festas, consumidor sem dinheiro
  Fevereiro: Carnaval — CTR cai, CPM sobe (mais gente online mas sem intenção de compra)
  Julho (início): férias escolares — foco em turismo e lazer, outros setores caem

Regra: antecipar aumento de budget antes do pico
  → Black Friday: aumentar 2 semanas antes, não na semana
  → Dia das Mães: aumentar 10 dias antes
  → Por quê: custo por resultado é menor antes do pico (menos concorrentes licitando)
```

### Redistribuição baseada em performance — protocolo

```
Revisar semanalmente (primeiros 60 dias) ou quinzenalmente (campanha madura):

Critérios para aumentar budget em um canal:
  → CPA/CPL dentro da meta por 2 semanas consecutivas
  → ROAS acima do mínimo com volume crescente
  → Frequência baixa (público ainda não saturado)

Critérios para reduzir ou pausar canal:
  → CPA/CPL 50% acima da meta por 2 semanas
  → ROAS abaixo do mínimo por 2 semanas
  → Frequência > 4x/semana (público saturando)
  → CTR caindo semana a semana (criativo fatigado)

Como redistribuir:
  → Mover budget do canal que underperforma para o que está melhor
  → Nunca pausar totalmente sem investigar — pausar campanha perde o histórico de aprendizado
  → Se o canal inteiro underperforma: revisar criativo e segmentação antes de abandonar o canal
```

---

## Templates prontos

### Planilha de distribuição de budget

```markdown
## Budget — [Nome da Campanha] — [Mês/Ano]

**Budget total:** R$ [valor]/mês

| Canal | Etapa do Funil | Budget | % | KPI | Meta | Atual |
|-------|---------------|--------|---|-----|------|-------|
| Google Search | BOFU | R$ [valor] | [%]% | CPA | R$ [meta] | R$ [atual] |
| Meta Ads | TOFU/MOFU | R$ [valor] | [%]% | CPL | R$ [meta] | R$ [atual] |
| Google PMax | BOFU | R$ [valor] | [%]% | ROAS | [N]x | [N]x |
| TikTok Ads | Teste | R$ [valor] | [%]% | CPL | R$ [meta] | — |
| Email Marketing | Retention | R$ [valor] | [%]% | CAC | R$ [meta] | — |
| **Total** | | **R$ [total]** | **100%** | | | |

### Alertas de redistribuição
- Se [canal X] ultrapassar CPL de R$ [valor] por 2 semanas → mover 50% para [canal Y]
- Se [canal Y] atingir ROAS [N]x por 2 semanas → aumentar em R$ [valor]
```

### Cálculo de CPL máximo

```markdown
## CPL Máximo Suportável — [Produto]

- Ticket médio: R$ [valor]
- Taxa de fechamento: [%]%
- Margem bruta: [%]%

**Cálculo:**
- Receita por lead: R$ [ticket] × [fechamento]% = R$ [valor]
- CPL máximo: R$ [receita/lead] × [margem]% = R$ [CPL máximo]

**Meta de CPL na campanha:** R$ [CPL máximo × 70%] (margem de segurança de 30%)
```

---

## Checklist de qualidade

- [ ] CPL máximo ou ROAS mínimo calculado antes de distribuir o budget
- [ ] Budget mínimo por canal verificado (abaixo do mínimo, algoritmo não aprende)
- [ ] Regra 70/20/10 aplicada (ou justificativa para diferente)
- [ ] Sazonalidade mapeada — picos e vales do setor considerados no planejamento anual
- [ ] Protocolo de redistribuição documentado (critérios para mover budget entre canais)
- [ ] Revisão semanal de performance agendada — não esperar 30 dias para ajustar

---

## Armadilhas comuns

**Distribuir demais com pouco budget:** R$ 3.000 divididos em 5 canais = R$ 600/canal = abaixo do mínimo em todos. Nenhum aprende, nenhum performa. Concentrar em 1-2 canais até ter dados.

**ROAS sem calcular margem:** campanha com ROAS 3x parece boa mas a margem é 25% — está no prejuízo. Calcular sempre o ROAS mínimo baseado na margem real do produto.

**Não antecipar sazonalidade:** aumentar budget na semana do Black Friday quando o CPM já dobrou. Planejar o aumento 2 semanas antes quando o custo ainda está baixo.

**Pausar canal após 1 semana ruim:** plataformas precisam de 2-4 semanas para otimizar. Mudanças bruscas resetam o aprendizado. Dar tempo, ajustar criativos antes de pausar.

**Budget igual para todos os canais:** tratar Meta, Google e TikTok com o mesmo budget sem considerar que têm CPCs, CPMs e curvas de aprendizado completamente diferentes.

---

## Referências confiáveis

- [Meta — Guia de orçamento para anúncios](https://www.facebook.com/business/help/190490051321426) — verificado 2026-05-01
- [Google — Smart Bidding e orçamento](https://support.google.com/google-ads/answer/6154846) — verificado 2026-05-01
- [WordStream — PPC Benchmarks](https://www.wordstream.com/blog/ws/2016/02/29/google-adwords-industry-benchmarks) — benchmarks de CPC/CTR por setor, verificado 2026-05-01

---

## Versão e histórico
→ Ver [estrategia-budget-distribuicao.changelog.md](estrategia-budget-distribuicao.changelog.md)
