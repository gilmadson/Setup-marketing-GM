# Analytics: Modelos de Atribuição

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 06-analytics

---

## Quando usar / Quando não usar

**Usar quando:**
- Campanha usa múltiplos canais — entender qual canal realmente contribui para a conversão
- Decisão de redistribuir budget entre canais — modelo errado leva a decisões erradas
- ROAS de um canal parece muito bom ou muito ruim — pode ser efeito do modelo de atribuição

**Não usar quando:**
- Canal único (só Google Search ou só Meta) — com 1 canal, não há dilema de atribuição
- Início de campanha com poucos dados — Data-Driven não funciona sem histórico

---

## Pré-requisitos

```
- GA4 configurado com eventos de conversão (ver analytics-ga4-conversoes)
- Pelo menos 2 canais rodando em paralelo
- Mínimo de 30 dias de dados para comparar modelos
- Para Data-Driven: mínimo 300 conversões nos últimos 30 dias (requisito Google)
```

---

## Padrões e convenções

### O problema de atribuição — por que existe

```
Cenário real de jornada do cliente:
  Dia 1: vê anúncio do Instagram (TOFU — conhece a marca)
  Dia 3: busca no Google "agência de tráfego pago" → clica no anúncio
  Dia 5: recebe email de nutrição → clica
  Dia 7: busca no Google "agência [nome da empresa]" → clica em resultado orgânico
  Dia 8: acessa o site diretamente → converte

Pergunta: qual canal "gerou" a conversão?

  Last Click diz: Orgânico (acessou direto depois da busca)
  First Click diz: Instagram (primeiro contato)
  Linear diz: todos os 4 canais têm 25% cada
  Time Decay diz: email e orgânico têm mais peso (mais recentes)
  Data-Driven diz: pesos baseados em padrões reais de conversão

Cada modelo conta uma história diferente.
O modelo escolhido define quais canais parecem estar funcionando.
```

### Modelos de atribuição — definições e quando usar

```
LAST CLICK (Último Clique):
  → 100% do crédito vai para o último canal tocado antes da conversão
  → Padrão histórico da maioria das plataformas (Meta Ads, Google Ads default antigo)
  → Problema: supervaloriza canais de BOFU (Search brand, remarketing) e ignora TOFU
  → Usar quando: quer medir somente o que fechou — campanha de resposta direta pura

FIRST CLICK (Primeiro Clique):
  → 100% do crédito vai para o primeiro canal que trouxe o usuário
  → Supervaloriza TOFU e ignora o que convenceu o usuário no final
  → Usar quando: quer entender qual canal está gerando descoberta de marca

LINEAR:
  → Crédito distribuído igualmente entre todos os pontos de contato
  → Exemplo: 4 touchpoints → 25% cada
  → Problema: trata todos os pontos de contato como igualmente importantes (não é real)
  → Usar quando: quer uma visão "justa" sem hipótese sobre qual etapa importa mais

TIME DECAY (Decaimento de Tempo):
  → Mais crédito para touchpoints mais recentes (mais próximos da conversão)
  → Touchpoints mais antigos recebem menos crédito (decai exponencialmente)
  → Lógica: o que convenceu o usuário a agir agora importa mais
  → Usar quando: ciclo de venda é longo e o momento da conversão tem mais peso

POSITION-BASED / U-SHAPED:
  → 40% para o primeiro touchpoint, 40% para o último, 20% dividido entre os do meio
  → Valoriza tanto a descoberta (TOFU) quanto o fechamento (BOFU)
  → Usar quando: quer reconhecer tanto o canal que gerou consciência quanto o que converteu

DATA-DRIVEN (Baseado em Dados — Google):
  → Algoritmo de ML analisa TODOS os caminhos que levaram a conversões e a não-conversões
  → Distribui crédito com base em quais touchpoints realmente fazem diferença estatística
  → Melhor modelo disponível — mas exige volume: 300+ conversões/30 dias (Google)
  → Default do Google Ads atualmente (substituiu Last Click em 2023)
  → Usar quando: tem volume suficiente e quer a atribuição mais precisa disponível

CROSS-CHANNEL (Google Analytics 4):
  → GA4 tem modelos próprios: Last Click, First Click, Linear, Time Decay, Data-Driven
  → Comparar modelos no GA4: Admin → Attribution → Exploration → Comparar side by side
  → GA4 Data-Driven: requer 300+ conversões e 3.000+ eventos em 30 dias
```

### Atribuição entre plataformas — o problema real

```
Por que os números não batem:

  Meta Ads relata: 150 conversões
  Google Ads relata: 120 conversões
  GA4 relata: 95 conversões

  Soma das plataformas: 270
  GA4 (fonte única): 95

  Por que a diferença?

  1. Janelas de atribuição diferentes:
     Meta default: 7 dias após clique + 1 dia após visualização
     Google default: 30 dias após clique
     GA4: 30 dias (configurável)
     → Mesma conversão pode ser contada em ambas as plataformas

  2. View-through attribution:
     Meta conta conversões de quem VIU o anúncio mas não clicou
     Google conta conversões de usuário que clicou em Display mas converteu depois
     GA4 conta apenas interações com clique (não view-through)

  3. Cross-device:
     Usuário clicou no Meta pelo celular, comprou pelo computador
     Meta pode associar (login Facebook), GA4 pode não associar (cookies diferentes)

  4. Bloqueio de cookies (iOS 14+, Safari):
     Meta perde parte das conversões sem CAPI
     GA4 perde sessões sem measurement protocol

Como lidar:
  → Escolher 1 fonte de verdade para tomar decisões de budget: GA4 ou MER (Marketing Efficiency Ratio)
  → MER = Receita total / Investimento total em marketing → visão holística sem atribuição individual
  → Não somar conversões de diferentes plataformas — cada uma conta com sua própria janela
  → Usar incrementality tests para saber o impacto real de um canal (pausar e medir queda nas vendas)
```

### MER e Incrementalidade — além da atribuição por clique

```
MER — Marketing Efficiency Ratio:
  Fórmula: Receita Total / Investimento Total em Marketing
  → Não depende de atribuição por clique — mede o impacto total do marketing
  → Exemplo: faturou R$ 500k em outubro com R$ 80k investido → MER = 6.25
  → Comparar mês a mês: se MER caiu mas ROAS de cada canal aumentou → pode ter problema de data

Incrementality Testing (teste de incrementalidade):
  → Medir o impacto real de um canal suspendendo-o temporariamente
  → Método simples: pausar canal por 2 semanas → medir queda nas conversões totais
  → Exemplo: pausa Meta Ads por 2 semanas → vendas caem 15% → Meta tem incrementalidade real de 15%
  → Mais sofisticado: geo holdout test (parar o canal em algumas regiões, manter em outras)
  → Limitação: pausar canal tem custo real — fazer em períodos de baixa sazonalidade

Holdout test no Meta:
  → Meta tem ferramenta nativa de incrementality (Conversion Lift)
  → Divide automaticamente o público em grupo de teste e controle
  → Mede conversões incrementais reais vs o que teria acontecido sem o anúncio
```

### Como escolher o modelo certo

```
Critério 1 — Maturidade da conta:
  Conta nova (<3 meses): Last Click ou Linear — sem dados para Data-Driven
  Conta madura (>3 meses, 300+ conv/30d): Data-Driven sempre que possível

Critério 2 — Objetivo da análise:
  Quer saber qual canal DESCOBRIU o cliente → First Click
  Quer saber qual canal FECHOU → Last Click
  Quer visão equilibrada → Linear ou Position-Based
  Quer precisão máxima com volume → Data-Driven

Critério 3 — Ciclo de venda:
  Ciclo curto (<24h, impulso): Last Click (quase tudo acontece em 1 sessão)
  Ciclo médio (1-7 dias): Time Decay ou Position-Based
  Ciclo longo (>7 dias): Linear ou Data-Driven

Configuração de janela de atribuição (Google Ads):
  Padrão atual: 30 dias para clique, 1 dia para view-through
  Ciclo longo B2B: aumentar para 60-90 dias
  E-commerce de impulso: manter 7-14 dias
```

---

## Templates prontos

### Comparação de modelos no GA4

```markdown
## Comparação de Atribuição — [Período]

Fonte: GA4 → Admin → Attribution → Modelo de Atribuição

| Canal | Last Click | First Click | Linear | Data-Driven |
|-------|-----------|-------------|--------|-------------|
| Google Search (brand) | [N] | [N] | [N] | [N] |
| Google Search (genérico) | [N] | [N] | [N] | [N] |
| Meta Ads | [N] | [N] | [N] | [N] |
| Email | [N] | [N] | [N] | [N] |
| Orgânico | [N] | [N] | [N] | [N] |
| **Total** | [N] | [N] | [N] | [N] |

**Modelo de decisão escolhido:** [Data-Driven / Linear / outro]
**Motivo:** [justificativa]

**Insight principal:**
[Canal X aparece forte no First Click mas fraco no Last Click → TOFU essencial mas não fecha sozinho]
[Canal Y aparece forte no Last Click → papel de conversão, mas depende de outros canais para existir]
```

---

## Checklist de qualidade

- [ ] Modelo de atribuição definido ANTES de analisar os canais
- [ ] Janela de atribuição alinhada ao ciclo de venda do produto
- [ ] Não somar conversões de diferentes plataformas (dupla contagem)
- [ ] GA4 como fonte única de verdade para comparações entre canais
- [ ] MER calculado mensalmente como sanity check das atribuições individuais
- [ ] Data-Driven usado quando tem 300+ conversões/30 dias

---

## Armadilhas comuns

**Last Click como padrão eterno:** gestor nunca questiona o modelo. Campanha de awareness (Meta) parece inútil porque Last Click dá todo o crédito ao Google Search. Meta é pausado. Search começa a piorar porque não tem mais alimentação de TOFU. Avaliar com pelo menos 2 modelos.

**Somar relatórios de plataformas:** Meta diz 150 conversões + Google diz 80 conversões = "230 conversões". GA4 diz 95. A diferença de 135 é dupla contagem e view-through. Usar GA4 como fonte única.

**Data-Driven sem volume:** ativar Data-Driven com 50 conversões/mês. O modelo não tem dados suficientes e fica instável — parece aleatorio. Esperar 300+ conversões antes de confiar.

**Ignorar cross-device:** usuário viu anúncio no celular, comprou no computador. Last Click atribui ao acesso direto no computador. A campanha mobile não recebe crédito. Ativar User ID no GA4 para unificar cross-device quando possível.

---

## Referências confiáveis

- [Google — Modelos de atribuição no GA4](https://support.google.com/analytics/answer/10596866) — verificado 2026-05-01
- [Meta — Conversion Attribution](https://www.facebook.com/business/help/458681590974355) — verificado 2026-05-01
- [Google — Data-Driven Attribution](https://support.google.com/google-ads/answer/6394265) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [analytics-attribution-models.changelog.md](analytics-attribution-models.changelog.md)
