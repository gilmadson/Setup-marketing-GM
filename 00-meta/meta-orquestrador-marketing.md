# Meta — Orquestrador de Marketing Digital

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 00-meta

---

## O que é esta skill

Skill especial que conduz o ciclo completo de uma campanha de marketing digital em conversa com o cliente:
**Fase 0 (Briefing) → Fase 1 (Planejamento) → Fase 2 (Execução) → Fase 3 (Análise e Otimização)**

O Claude faz as perguntas em conversa livre, interpreta as respostas, seleciona quais canais e skills aplicar e em qual ordem. Quando o cliente não sabe decidir, o orquestrador escolhe com critérios simples e explícitos.

---

## Fase 0 — Briefing (perguntas ao cliente)

Fazer as perguntas uma a uma em conversa, não como formulário. Aguardar resposta antes da próxima.

```
P1. Qual é o objetivo principal desta campanha?
    a) Gerar brand awareness (alcance, reconhecimento de marca)
    b) Gerar leads (cadastros, contatos, orçamentos)
    c) Gerar vendas diretas (e-commerce, D2C)
    d) Reter e reengajar clientes existentes (CRM, LTV)
    e) Lançar um produto ou serviço novo
    → Se não souber: "O que você quer que aconteça após alguém ver o anúncio?"

P2. Quem é o público-alvo?
    → Descrever em termos de comportamento, não só demografia
    → Exemplos: "donos de PME que buscam software de gestão", "mães de 25-40 anos interessadas em alimentação saudável"
    → Se não souber: usar a skill estrategia-personas-comprador antes de avançar

P3. Qual é o budget mensal disponível?
    a) Até R$ 3.000/mês — micro (1-2 canais, escopo reduzido)
    b) R$ 3.000–15.000/mês — pequeno (2-3 canais, testes estruturados)
    c) R$ 15.000–50.000/mês — médio (multicanal com otimização contínua)
    d) Acima de R$ 50.000/mês — grande (full-funnel, todos os canais relevantes)
    → Se não souber: "Quanto você está disposto a investir para adquirir um cliente?"

P4. Qual é o prazo da campanha?
    a) Pontual (evento, lançamento) — 1 a 4 semanas
    b) Trimestral — 3 meses com revisão de resultados
    c) Contínua — sem data de encerramento, otimização mensal
    → Impacta: escolha de canais (SEO não funciona em campanhas pontuais)

P5. Qual é o produto ou serviço anunciado?
    → Preço, ticket médio, ciclo de venda (imediato ou longo)
    → Produto digital ou físico? Local ou nacional?
    → Venda direta ou geração de lead para equipe comercial?

P6. Quais canais já foram testados? Quais resultados tiveram?
    → Identificar o que funcionou e o que não funcionou
    → Se nunca anunciou: começar pelos canais de menor risco (ver árvore de decisão)

P7. Existe presença digital já estruturada?
    □ Site com domínio próprio e velocidade ok
    □ Pixel do Meta instalado e com dados históricos
    □ Google Tag Manager configurado
    □ Google Analytics 4 com conversões mapeadas
    □ Perfis nas redes sociais ativos
    □ Lista de e-mails / CRM com contatos
```

---

## Árvores de decisão

### Canal principal por objetivo

```
Objetivo → Canal primário recomendado:

  Brand Awareness (alcance máximo)
    → Budget < R$5k: Instagram orgânico + Meta Ads (alcance/CPM)
    → Budget > R$5k: Meta Ads + YouTube Ads (vídeo) + TikTok

  Geração de Leads (B2C)
    → Produto de decisão rápida (< R$500): Meta Ads (Leads) + landing page
    → Produto de decisão longa (> R$500): Google Search + remarketing Meta

  Geração de Leads (B2B)
    → Ticket < R$5k/mês: Google Search (palavras de intenção) + Meta
    → Ticket > R$5k/mês: LinkedIn Ads + Google Search + email marketing

  Vendas Diretas (e-commerce)
    → Loja com histórico: Meta Ads Advantage+ Shopping + Google PMax
    → Loja nova (sem dados): Google Search + Meta conversão → depois PMax

  Lançamento de Produto
    → Sequência: Teaser orgânico → Meta Ads aquecimento (7d) → Google Search (busca pela marca) → E-mail para base

  Retenção / Reengajamento
    → E-mail marketing + WhatsApp para base existente
    → Meta Ads para Custom Audience de clientes
```

### Canal por budget mensal

```
Até R$ 3.000/mês:
  → 1 canal principal: Meta Ads (mais acessível) OU Google Search (mais intenção)
  → Não distribuir — concentrar para aprender

R$ 3.000–15.000/mês:
  → 2 canais: canal de intenção (Google Search) + canal de descoberta (Meta Ads)
  → 70% no canal com melhor resultado histórico, 30% testando

R$ 15.000–50.000/mês:
  → 3-4 canais: Search + Social + Remarketing + E-mail
  → Funil completo: TOFU (awareness) + MOFU (consideração) + BOFU (conversão)

Acima de R$ 50.000/mês:
  → Full-funnel com todos os canais relevantes
  → SEO orgânico em paralelo como investimento de longo prazo
  → Influenciadores/UGC para TOFU
  → Afiliados para BOFU
```

### Prazo vs canal

```
Campanha pontual (1-4 semanas):
  ✅ Meta Ads, Google Search, TikTok Ads, e-mail para base
  ❌ SEO (leva 3-6 meses), LinkedIn orgânico, YouTube orgânico

Campanha trimestral (3 meses):
  ✅ Todos os canais de mídia paga + testes A/B estruturados
  ✅ Início de SEO técnico e de conteúdo
  ❌ Resultado de SEO ainda não maduro

Campanha contínua (sem prazo):
  ✅ Todos os canais — paid + orgânico em paralelo
  ✅ SEO cresce e reduz dependência de paid ao longo do tempo
  ✅ Influenciadores e afiliados para diversificar tráfego
```

---

## Fase 1 — Planejamento

```
SEMPRE executar:
  1. estrategia-briefing-campanha    → formalizar objetivo, KPIs, público, budget
  2. estrategia-personas-comprador   → quem é o comprador, dores, gatilhos, objeções
  3. estrategia-funil-marketing      → mapear etapas e canais por etapa
  4. estrategia-budget-distribuicao  → alocar budget por canal e funil

SE campanha paga (Meta, Google, TikTok, LinkedIn):
  5. criativos-copy-anuncios         → copies dos anúncios antes de subir
  6. criativos-landing-page-cro      → validar landing page antes de enviar tráfego

SE campanha de conteúdo/orgânico:
  7. social-estrategia-conteudo      → calendário editorial e pilares
  8. seo-conteudo                    → keyword research antes de produzir
```

---

## Fase 2 — Execução

```
META ADS:
  → meta-ads-estrutura-conta         → criar estrutura Campaign/Ad Set/Ad
  → meta-ads-segmentacao             → configurar públicos
  → meta-ads-pixel-api               → verificar pixel e eventos
  → meta-ads-criativos               → subir criativos nos formatos corretos
  → meta-ads-otimizacao              → configurar regras automáticas de otimização

GOOGLE ADS:
  → google-search                    → campanhas de pesquisa com keywords de intenção
  → google-display                   → remarketing para quem visitou o site
  → google-pmax                      → Performance Max para e-commerce

OUTROS CANAIS (conforme briefing):
  → outros-tiktok-ads, outros-linkedin-ads, outros-email-marketing, outros-sms-whatsapp

ANALYTICS (sempre — configurar antes de lançar):
  → analytics-ga4-conversoes         → rastrear conversões antes de gastar
  → analytics-metricas-fundamentais  → definir KPIs e meta por canal
```

---

## Fase 3 — Análise e Otimização

```
SEMANAL (primeiros 30 dias):
  → analytics-metricas-fundamentais  → revisar CTR, CPC, CPA, ROAS por canal
  → meta-ads-otimizacao              → ajustar lances, pausar anúncios ruins
  → analytics-attribution-models     → entender qual canal está convertendo

MENSAL:
  → analytics-dashboard-relatorio    → gerar relatório para cliente
  → estrategia-budget-distribuicao   → redistribuir budget baseado em performance
  → testes A/B em criativos e copies

TRIMESTRAL:
  → revisar personas (mudou o público que converte?)
  → revisar funil (onde está o maior gargalo?)
  → avaliar novos canais
```

---

## Resumo executivo — saída do briefing

Após o briefing, gerar este bloco:

```markdown
## Campanha: [Nome]
**Data:** YYYY-MM-DD | **Cliente:** [Nome]

### Objetivo
- Tipo: [awareness / leads / vendas / retenção / lançamento]
- Meta: [ex: 200 leads/mês a R$ 30/lead]
- Prazo: [pontual X semanas / trimestral / contínua]

### Público-alvo
- Persona principal: [nome + descrição em 1 frase]
- Segmentação digital: [interesses, cargo, comportamento]
- Geolocalização: [nacional / regional / local]

### Budget
- Total mensal: R$ [valor]
- Distribuição: [canal A: X% / canal B: Y% / testes: Z%]

### Canais selecionados
- Principal: [canal + justificativa]
- Suporte: [canal + justificativa]
- Descartados: [canal + motivo]

### KPIs por canal
| Canal | Métrica | Meta |
|-------|---------|------|
| [canal 1] | CPA / CPL / ROAS | [valor] |
| [canal 2] | CPA / CPL / ROAS | [valor] |

### Skills a executar (em ordem)
Fase 1: [lista]
Fase 2: [lista]
Fase 3: [lista]
```

---

## Checklist de qualidade do briefing

- [ ] Objetivo definido (não "quero aparecer mais" — quero X leads a R$ Y cada)
- [ ] Persona do comprador documentada com dores e gatilhos
- [ ] Budget mensal confirmado e distribuição definida
- [ ] Canais escolhidos com justificativa alinhada ao objetivo e prazo
- [ ] KPIs por canal definidos ANTES de lançar a campanha
- [ ] Analytics configurado (pixel, GA4, conversões) ANTES de gastar
- [ ] Landing page validada (velocidade, copy, CTA) ANTES de enviar tráfego
- [ ] Resumo executivo gerado e aprovado pelo cliente

---

## Referências confiáveis

- Skills do repositório setup-marketing-GM — fonte primária de padrões de marketing digital
- [Google Ads Help Center](https://support.google.com/google-ads/) — verificado 2026-05-01
- [Meta for Business](https://www.facebook.com/business/help) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [meta-orquestrador-marketing.changelog.md](meta-orquestrador-marketing.changelog.md)
