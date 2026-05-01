# Analytics: Dashboard e Relatório

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 06-analytics

---

## Quando usar / Quando não usar

**Usar quando:**
- Apresentando resultados para o cliente mensalmente — relatório estruturado evita mal-entendidos
- Monitorando campanha em tempo real — dashboard automatizado economiza horas de extração manual
- Tomando decisão de redistribuição de budget — dados consolidados em 1 lugar

**Não usar quando:**
- Campanha com menos de 2 semanas — sem dados suficientes para relatório significativo
- Cliente que só quer 1 número (ROAS) — dashboard completo é overhead desnecessário

---

## Pré-requisitos

```
- GA4 configurado com conversões (ver analytics-ga4-conversoes)
- Acesso de leitura às contas de anúncios (Google Ads, Meta Ads) para conectar ao Looker Studio
- Looker Studio (lookerstudio.google.com) — gratuito, login com Google
- Métricas e metas definidas com o cliente antes do primeiro relatório
```

---

## Padrões e convenções

### Looker Studio — configuração de dashboard

```
O que é:
  → Ferramenta gratuita do Google para dashboards interativos e compartilháveis
  → Conecta a: GA4, Google Ads, Google Search Console, Google Sheets, planilhas de dados externos
  → Para Meta Ads: usar conector de terceiro (Supermetrics, Power My Analytics, Porter Metrics)

Configuração básica:
  1. Criar relatório → Add Data → Google Analytics 4 → selecionar propriedade
  2. Add Data → Google Ads → selecionar conta
  3. Para Meta: Add Data → [conector pago] → autenticar conta Meta

Estrutura recomendada do dashboard:

  PÁGINA 1 — VISÃO GERAL (1 olhada, entende tudo):
    → Cards de KPIs: Investimento total | Leads/Vendas | CPL/CPA | ROAS
    → Gráfico de linha: evolução semanal de CPL/ROAS no período
    → Tabela: performance por canal (investimento, resultado, CPL, status)
    → Controle de data: filtro de período editável pelo cliente

  PÁGINA 2 — META ADS (detalhe):
    → Gráfico de barras: CTR e CPL por campanha
    → Tabela: Ad Sets ativos com investimento, impressões, CTR, CPL, frequência
    → Gráfico de tendência: frequência ao longo do tempo (alerta de saturação)

  PÁGINA 3 — GOOGLE ADS (detalhe):
    → Tabela: campanhas com investimento, cliques, CTR, CPC, conversões, CPA
    → Gráfico: impressões vs cliques vs conversões (funil visual)
    → Tabela: Search Terms principais (do Google Ads Report)

  PÁGINA 4 — SEO / ORGÂNICO:
    → Conectar Google Search Console
    → Impressões, cliques, CTR, posição média por keyword
    → Evolução do tráfego orgânico (GA4 → Organic Search)

  PÁGINA 5 — FUNIL DE CONVERSÃO:
    → Dados do GA4: sessões → engajados → clicou CTA → converteu
    → Taxas de conversão por etapa
    → Comparação com período anterior
```

### Estrutura do relatório mensal para o cliente

```
RELATÓRIO MENSAL — estrutura narrativa (não só números):

1. RESUMO EXECUTIVO (1 parágrafo — o que aconteceu em palavras):
   → "Em abril geramos X leads a R$ Y/lead, Z% abaixo da meta de R$ W.
      O canal X foi o destaque, enquanto Y precisa de ajuste."
   → O cliente lê isso primeiro — se não entender em 30 segundos, o relatório falhou.

2. RESULTADOS DO MÊS (tabela consolidada):
   | Canal | Investimento | Leads/Vendas | CPL/CPA | Meta | Status |
   | Meta Ads | R$ X.000 | XX | R$ XX | R$ XX | ✅ |
   | Google Search | R$ X.000 | XX | R$ XX | R$ XX | ⚠️ |
   | Total | R$ XX.000 | XXX | R$ XX | R$ XX | ✅ |

3. O QUE FUNCIONOU (com dados):
   → "Campanha Y teve CPL R$ 28 — 30% abaixo da meta. Criativo Z teve CTR 2.4%, acima da média."
   → Mostrar o criativo vencedor se possível

4. O QUE NÃO FUNCIONOU E POR QUÊ:
   → "Campanha X teve CPL R$ 67 — acima da meta. Diagnóstico: frequência chegou a 6x, público saturou."
   → Não esconder problemas — antecipar e explicar

5. AJUSTES REALIZADOS NO MÊS:
   → Lista do que foi mudado durante o mês e por quê
   → "Semana 2: pausamos Ad Set Y por frequência alta. Criamos nova segmentação Z."

6. PLANO PARA O PRÓXIMO MÊS:
   → 3-5 ações concretas (não genéricas)
   → "1. Criar 3 novos criativos com ângulo de prova social. 2. Testar LAL 2% de compradores. 3. Aumentar budget de Meta em 20% dado o CPL estável."

7. MÉTRICAS DE VAIDADE (opcional — se o cliente pede):
   → Alcance, impressões, seguidores (deixar por último, após as métricas de negócio)
```

### Comparação de período — como apresentar evolução

```
Comparações úteis:
  MoM (Month over Month): comparar com mês anterior
    → Mostra tendência imediata — subiu ou caiu?
    → Problema: sazonalidade distorce (janeiro sempre cai vs dezembro)

  YoY (Year over Year): comparar com mesmo mês do ano anterior
    → Elimina sazonalidade — comparação mais justa
    → Problema: precisa de 1 ano de histórico

  vs Meta: comparar resultado real vs meta acordada
    → A mais importante para o cliente — atingimos o que prometemos?

Como apresentar no Looker Studio:
  → Adicionar "Período de comparação" em cada scorecard
  → Looker Studio mostra automaticamente: valor atual + seta para cima/baixo + % de diferença
  → Usar código de cores: verde (acima da meta), amarelo (próximo), vermelho (abaixo)
```

### Tom e storytelling — como apresentar para o cliente

```
Princípios de apresentação:

  1. Contexto antes de número:
     ❌ "O CTR foi 1.2%"
     ✅ "O CTR foi 1.2% — acima do benchmark do setor (0.8%) e 40% melhor que o mês passado"

  2. Causa antes de dado:
     ❌ "O CPL subiu R$ 12 em março"
     ✅ "O CPL subiu R$ 12 em março porque a frequência chegou a 5x na semana 3 — já corrigimos com novos criativos"

  3. Problema com solução:
     Nunca apresentar problema sem o próximo passo.
     "Campanha X não atingiu a meta. Diagnóstico: LP com tempo de carregamento de 6s. Plano: otimizar imagens até dia 15."

  4. Resultado ruim — como apresentar:
     → Proativo: contar antes que o cliente pergunte
     → Com diagnóstico: mostrar que você sabe por que aconteceu
     → Com plano: mostrar o que você vai fazer
     → Nunca: esconder dado ruim esperando melhorar sozinho no próximo mês

Frequência de relatório:
  Semanal (primeiros 30 dias): relatório simplificado — só KPIs e alertas
  Mensal (campanha madura): relatório completo com análise e plano
  Trimestral: revisão estratégica — personas, funil, canais, metas do próximo trimestre
```

---

## Templates prontos

### Template de relatório mensal (resumo executivo)

```markdown
## Relatório de Performance — [Mês/Ano]
**Cliente:** [Nome] | **Período:** [DD/MM] a [DD/MM] | **Responsável:** [Nome]

---

### Resumo Executivo
[1-2 parágrafos em linguagem clara: o que aconteceu, o principal destaque positivo e o principal ponto de atenção]

---

### Resultados do Mês

| Canal | Investimento | Resultado | CPL / CPA | Meta | Status |
|-------|-------------|-----------|-----------|------|--------|
| Meta Ads | R$ | | R$ | R$ | ✅ ⚠️ ❌ |
| Google Search | R$ | | R$ | R$ | ✅ ⚠️ ❌ |
| **Total** | **R$** | | **R$** | **R$** | |

---

### Destaques Positivos
- [Resultado específico com dado: "Criativo Z gerou CPL 40% abaixo da média"]

### Pontos de Atenção
- [Problema + diagnóstico + o que foi feito ou será feito]

### Ajustes Realizados no Mês
- [Semana X: ação tomada + motivo]

### Plano para [Próximo Mês]
1. [Ação concreta 1]
2. [Ação concreta 2]
3. [Ação concreta 3]

---
*Dashboard completo disponível em: [link Looker Studio]*
```

---

## Checklist de qualidade

- [ ] Resumo executivo em linguagem não técnica (cliente entende sem abrir o dashboard)
- [ ] Resultados vs metas — não só resultados absolutos
- [ ] Problema apresentado com diagnóstico + plano de ação
- [ ] Comparação com período anterior documentada
- [ ] Dashboard atualizado automaticamente (não extração manual)
- [ ] Frequência de relatório alinhada com o cliente antes de começar

---

## Armadilhas comuns

**Relatório de dados sem insights:** tabela com 50 números mas nenhuma conclusão. Cliente olha e pergunta "e aí, está bom?". Relatório deve responder essa pergunta sem que ele precise perguntar.

**Métricas de vaidade primeiro:** abrindo com "tivemos 2 milhões de impressões" antes de falar em leads e CPL. Cliente valoriza resultado de negócio. Começar sempre com o que gerou (ou não gerou) receita.

**Esconder dado ruim:** não mencionar o canal que não performou esperando melhorar no próximo mês. Cliente descobre no dia 30, pergunta por que não foi avisado antes. Proatividade gera confiança, omissão gera desconfiança.

**Dashboard manual:** extrair dados do Meta, Google e GA4 toda semana para planilha. Horas de trabalho improdutivo. Looker Studio com conectores automáticos — 1 vez de setup, zero trabalho manual depois.

**Sem acesso ao cliente:** dashboard bonito que só o gestor consegue abrir. Compartilhar link do Looker Studio com o cliente e ensinar a usar os filtros de data.

---

## Referências confiáveis

- [Looker Studio — Conectores de dados](https://lookerstudio.google.com/data) — verificado 2026-05-01
- [Google — Relatórios do GA4](https://support.google.com/analytics/answer/9212670) — verificado 2026-05-01
- [Porter Metrics — Conector Meta Ads para Looker Studio](https://portermetrics.com/) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [analytics-dashboard-relatorio.changelog.md](analytics-dashboard-relatorio.changelog.md)
