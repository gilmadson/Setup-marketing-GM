# Analytics: Métricas Fundamentais

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 06-analytics

---

## Quando usar / Quando não usar

**Usar quando:**
- Definindo KPIs antes de lançar campanha — sem métricas definidas, não há critério de sucesso
- Apresentando resultados para o cliente — traduzir dados em linguagem de negócio
- Diagnosticando performance ruim — identificar qual métrica está quebrando o funil

**Não usar quando:**
- Campanha com menos de 7 dias — dados insuficientes para conclusões (exceto alertas de entrega)

---

## Pré-requisitos

```
- Objetivo da campanha definido (ver estrategia-briefing-campanha)
- Funil mapeado por etapa (ver estrategia-funil-marketing)
- GA4 e pixels de plataforma instalados e com conversões configuradas
```

---

## Padrões e convenções

### Métricas por etapa do funil — o que medir em cada fase

```
TOFU — Awareness (o que o dinheiro está comprando):
  Alcance (Reach)
    → Pessoas únicas que viram o anúncio pelo menos 1 vez
    → Objetivo: maximizar com CPM controlado

  Impressões
    → Quantas vezes o anúncio foi exibido (1 pessoa pode gerar múltiplas impressões)
    → Frequência = Impressões / Alcance

  CPM — Custo por Mil Impressões
    → Fórmula: (Investimento / Impressões) × 1.000
    → Benchmark Brasil: Meta Ads R$ 8-25, YouTube R$ 10-30, TikTok R$ 5-15
    → CPM alto sem resultado = público errado ou criativo rejeitado

  Frequência
    → Quantas vezes em média cada pessoa viu o anúncio
    → Benchmark: 2-4x/semana para awareness | > 3x para conversão = saturação

  View Rate / VTR (vídeo)
    → % que assistiu 30s+ ou o fim do vídeo
    → Benchmark: > 25% para in-stream skippable

MOFU — Consideration:
  CTR — Click-Through Rate
    → Fórmula: (Cliques / Impressões) × 100
    → Benchmark: Meta Feed 0.8-1.5% | Google Search 3-8% | Display 0.1-0.3%
    → CTR baixo = criativo não chama atenção ou público não tem interesse

  CPC — Custo por Clique
    → Fórmula: Investimento / Cliques
    → Benchmark Brasil: Meta R$ 0,50-2,00 | Google Search R$ 2-10 (varia por nicho)
    → CPC alto + CTR baixo = leilão competitivo, melhorar QS (Google) ou criativo (Meta)

  Taxa de engajamento
    → (Curtidas + Comentários + Compartilhamentos + Saves) / Alcance
    → Relevante para campanhas orgânicas e de awareness social

BOFU — Conversion (o que realmente importa para o negócio):
  Taxa de conversão (CVR — Conversion Rate)
    → Fórmula: (Conversões / Cliques) × 100
    → Benchmark LP de lead: 5-20% | E-commerce: 1-3% | Demo B2B: 3-8%
    → CVR baixa com CTR bom = problema na landing page

  CPL — Custo por Lead
    → Fórmula: Investimento / Leads gerados
    → Benchmark por setor: ver estrategia-briefing-campanha
    → CPL máximo = Ticket médio × Taxa de fechamento × Margem (ver estrategia-budget-distribuicao)

  CPA — Custo por Aquisição (custo por cliente adquirido)
    → Fórmula: Investimento / Clientes novos
    → CPA = CPL / Taxa de fechamento
    → CPA é o custo real do cliente, não do lead

  ROAS — Return on Ad Spend
    → Fórmula: Receita gerada / Investimento em anúncios
    → Exemplo: R$ 10.000 em anúncios gerou R$ 40.000 em vendas → ROAS = 4x (ou 400%)
    → ROAS mínimo = 1 / Margem bruta (ver estrategia-budget-distribuicao)
    → ROAS vs ROI: ROAS considera só o gasto em anúncio; ROI considera todos os custos

POST-VENDA — Retention:
  LTV — Lifetime Value (valor vitalício do cliente)
    → Fórmula básica: Ticket médio × Frequência de compra por ano × Anos de retenção
    → Exemplo: R$ 500/compra × 4x/ano × 3 anos = LTV R$ 6.000
    → Para assinatura: LTV = Receita mensal × Duração média da assinatura em meses

  CAC — Custo de Aquisição de Cliente
    → Fórmula: Total investido em marketing e vendas / Clientes novos adquiridos
    → Diferença de CPA: CAC inclui salários, ferramentas, agência — CPA é só o gasto em mídia

  LTV:CAC Ratio
    → Fórmula: LTV / CAC
    → < 1:1: você perde dinheiro adquirindo clientes — modelo não sustentável
    → 1:1 a 3:1: margem apertada — viável mas precisa melhorar
    → > 3:1: saudável — escalar
    → > 5:1: pode estar sub-investindo em aquisição — testar crescimento mais rápido

  Churn Rate
    → % de clientes que cancelam ou param de comprar no período
    → Fórmula: Clientes perdidos no período / Clientes no início do período
    → Churn alto anula qualquer esforço de aquisição

  Payback Period (tempo para recuperar o CAC)
    → Fórmula: CAC / Receita mensal por cliente
    → Exemplo: CAC R$ 1.200 | receita mensal R$ 400 → Payback = 3 meses
    → Meta: < 12 meses para SaaS | < 6 meses para e-commerce
```

### Métricas de vaidade vs métricas de negócio

```
MÉTRICAS DE VAIDADE (parecem boas, mas não dizem nada sobre resultado):
  → Seguidores no Instagram → não pagam contas
  → Curtidas e comentários → engajamento sem conversão não gera receita
  → Impressões totais → alcance sem contexto de conversão é dado vazio
  → Taxa de abertura de email isolada → abrir não é clicar nem converter

MÉTRICAS DE NEGÓCIO (ligadas a receita):
  → CPL dentro da meta → leads qualificados chegando
  → CPA abaixo do CAC máximo → cliente adquirido de forma lucrativa
  → ROAS acima do mínimo → anúncio gerando mais do que custa
  → LTV:CAC > 3:1 → negócio saudável e escalável
  → Receita atribuída à campanha → impacto real no faturamento

Como apresentar para o cliente:
  ❌ "Tivemos 1.200.000 impressões e 45.000 cliques"
  ✅ "Geramos 187 leads qualificados a R$ 32/lead — 23% abaixo da meta de R$ 42"
```

### Fórmulas de referência rápida

```
CPM  = (Investimento / Impressões) × 1.000
CPC  = Investimento / Cliques
CTR  = (Cliques / Impressões) × 100
CVR  = (Conversões / Cliques) × 100
CPL  = Investimento / Leads
CPA  = Investimento / Clientes
ROAS = Receita / Investimento
ROI  = (Receita - Custo Total) / Custo Total × 100
CAC  = (Investimento Marketing + Vendas) / Clientes Novos
LTV  = Ticket × Frequência × Retenção
LTV:CAC = LTV / CAC
Payback = CAC / Receita Mensal por Cliente
Churn = Clientes Perdidos / Clientes Início do Período
Frequência = Impressões / Alcance
```

---

## Templates prontos

### Tabela de KPIs por campanha

```markdown
## KPIs — [Campanha] — [Mês/Ano]

**Período:** [DD/MM] a [DD/MM]
**Investimento total:** R$ [valor]

| Métrica | Meta | Resultado | Status |
|---------|------|-----------|--------|
| Alcance | [N] | [N] | ✅/⚠️/❌ |
| Impressões | [N] | [N] | ✅/⚠️/❌ |
| Frequência | < [N]x | [N]x | ✅/⚠️/❌ |
| CTR | > [%] | [%] | ✅/⚠️/❌ |
| CPL / CPA | < R$ [valor] | R$ [valor] | ✅/⚠️/❌ |
| ROAS | > [N]x | [N]x | ✅/⚠️/❌ |
| Volume de Leads/Vendas | [N] | [N] | ✅/⚠️/❌ |

**Diagnóstico:** [o que está funcionando e o que precisa de atenção]
**Ação recomendada:** [próximo passo concreto]
```

---

## Checklist de qualidade

- [ ] CPL máximo ou ROAS mínimo calculado antes de lançar (não depois)
- [ ] Métricas de vaidade separadas das métricas de negócio no relatório
- [ ] LTV:CAC calculado trimestralmente (não só olhar CPA)
- [ ] Frequência monitorada semanalmente (> 3x = saturação se conversão)
- [ ] Benchmarks por setor e plataforma usados como referência (não como verdade absoluta)

---

## Armadilhas comuns

**ROAS sem considerar margem:** ROAS 4x parece ótimo, mas margem bruta é 20% → ROAS mínimo é 5x. Está no prejuízo. Calcular sempre o ROAS mínimo antes de interpretar o resultado.

**CPA vs CAC confundidos:** gestor apresenta CPA de R$ 80 (só mídia) como CAC. Cliente descobre que com salário de vendedor + ferramentas, o CAC real é R$ 240. CAC = tudo, CPA = só mídia.

**Olhar CTR sem CVR:** CTR de 3% (ótimo!) mas CVR de 0.3% (péssimo). O problema não é o anúncio — é a landing page. Analisar o funil completo, não 1 métrica isolada.

**Frequência ignorada:** CPL ok, mas frequência 7x na semana para o mesmo público. Daqui 2 semanas o CPL dobra porque o público saturou. Frequência é métrica preditiva — olhar antes do problema aparecer.

---

## Referências confiáveis

- [Google — About conversion tracking](https://support.google.com/google-ads/answer/1722022) — verificado 2026-05-01
- [Meta — Ads Manager metrics](https://www.facebook.com/business/help/metrics) — verificado 2026-05-01
- [Wordstream — PPC benchmarks 2025](https://www.wordstream.com/blog/ws/2016/02/29/google-adwords-industry-benchmarks) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [analytics-metricas-fundamentais.changelog.md](analytics-metricas-fundamentais.changelog.md)
