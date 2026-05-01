# Analytics: GA4 e Conversões

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 06-analytics

---

## Quando usar / Quando não usar

**Usar quando:**
- Configurando rastreamento de qualquer campanha digital — GA4 é a base de analytics de marketing
- Importando conversões para Google Ads — GA4 é a fonte mais precisa para Smart Bidding
- Analisando qual canal e conteúdo gera mais conversões

**Não usar quando:**
- Apenas analytics de produto (comportamento interno do usuário logado) — considerar ferramentas complementares como PostHog ou Mixpanel para análise de produto

---

## Pré-requisitos

```
- Acesso ao Google Analytics 4 (criar em analytics.google.com)
- Google Tag Manager instalado no site (recomendado para eventos customizados)
- Acesso ao Google Ads (para vincular e importar conversões)
- Para e-commerce: integração GA4 com a plataforma (Shopify, WooCommerce, VTEX)
```

---

## Padrões e convenções

### GA4 vs Universal Analytics — mudanças principais

```
Universal Analytics (descontinuado em julho 2023):
  → Baseado em sessões e pageviews
  → Hits de evento com Category/Action/Label
  → Bounce rate como métrica principal

GA4 (atual):
  → Baseado em eventos — tudo é um evento
  → Modelo de dados: event_name + parameters
  → Engaged sessions (30s+ ou 2+ páginas) substituem Bounce Rate
  → User-centric: segue o usuário entre sessões e dispositivos
  → Machine Learning nativo: predictive audiences, anomaly detection

Mudança na estrutura de dados:
  UA: Session → Hit (pageview/event)
  GA4: User → Session → Event (com parâmetros)
```

### Tipos de eventos no GA4

```
1. EVENTOS AUTOMÁTICOS (coletados sem configuração):
  page_view, session_start, first_visit, user_engagement
  scroll (90% da página)
  click (links externos)
  file_download
  video_start, video_progress, video_complete (YouTube embeds)

2. EVENTOS RECOMENDADOS (configurar para e-commerce e lead gen):
  Padrão para e-commerce:
    view_item_list → usuário viu lista de produtos
    view_item → usuário viu página do produto
    add_to_cart → adicionou ao carrinho
    begin_checkout → iniciou checkout
    add_payment_info → inseriu dados de pagamento
    purchase → compra concluída (OBRIGATÓRIO com revenue, transaction_id)

  Padrão para lead gen:
    generate_lead → formulário enviado / lead criado
    sign_up → cadastro novo

  Padrão para engajamento:
    search → pesquisa interna no site
    select_content → clique em conteúdo

3. EVENTOS CUSTOMIZADOS (criar conforme necessidade):
  Nomenclatura: snake_case, descritivo, consistente
  Exemplos:
    form_submit_contact → envio do formulário de contato
    cta_click_header → clique no CTA do header
    video_play_depoimento → play no vídeo de depoimento
    whatsapp_click → clique no botão do WhatsApp

  Como criar via GTM:
    → Trigger: clique em elemento / submissão de formulário / visualização de página
    → Tag: GA4 Event Tag → event_name + parameters
    → Testar: GTM Preview Mode → verificar se evento dispara
```

### Configuração de conversões

```
O que é conversão no GA4:
  → Qualquer evento marcado como conversão
  → Pode ter múltiplas conversões por sessão (diferente do UA)
  → Conversão ≠ objetivo — Goals foram substituídos por conversões

Como marcar evento como conversão:
  GA4 → Admin → Conversões → Novo evento de conversão → digitar o nome exato do evento

Eventos que DEVEM ser conversão:
  → generate_lead (ou form_submit equivalente)
  → purchase
  → Para B2B: schedule_call, demo_request, contact_form_submit
  → Para e-commerce: purchase com revenue obrigatório

Parâmetros obrigatórios no evento purchase:
  {
    event_name: "purchase",
    transaction_id: "T-12345",     // único por compra — evita duplicação
    value: 297.00,                  // receita desta transação
    currency: "BRL",
    items: [{
      item_id: "SKU-001",
      item_name: "Curso Marketing Digital",
      price: 297.00,
      quantity: 1
    }]
  }

Conversões de valor para e-commerce:
  → SEMPRE incluir parâmetro value e currency
  → Sem esses parâmetros: GA4 conta a conversão mas não sabe o valor → relatórios de receita vazios
  → Google Ads não consegue otimizar por Target ROAS sem dados de valor
```

### Relatórios de aquisição — entender de onde vêm os usuários

```
Relatório principal:
  GA4 → Relatórios → Aquisição → Aquisição de tráfego

  Dimensões:
    Session default channel group: Organic Search | Direct | Paid Search | Organic Social | Paid Social | Email | Referral
    Session source/medium: google/cpc | facebook/cpc | email/newsletter | (direct)/(none)
    Session campaign: nome da campanha UTM

  Métricas-chave:
    Sessões → volume de tráfego
    Taxa de conversão de sessão (%) → eficiência do canal
    Receita (para e-commerce) → valor gerado por canal

Parâmetros UTM — marcar links de campanhas:
  utm_source: de onde veio (google, facebook, email, instagram)
  utm_medium: tipo de mídia (cpc, email, social, organic)
  utm_campaign: nome da campanha (black-friday-2026, lancamento-produto-x)
  utm_content: variação do criativo (video-v1, imagem-v2) — para A/B
  utm_term: keyword (para Google Search manual)

  URL com UTM:
  https://seusite.com/lp?utm_source=facebook&utm_medium=cpc&utm_campaign=leads-junho&utm_content=video-v1

  Regras de UTM:
  → Sempre lowercase (Facebook ≠ facebook no GA4)
  → Sem espaços (usar hífen ou underscore)
  → Consistente: não mudar nomes a cada campanha (dificulta comparação histórica)
  → Não usar UTM em links internos do próprio site (confunde atribuição de sessão)
```

### Explorations — análises avançadas

```
GA4 → Explorar

Funil de Conversão (Funnel Exploration):
  → Mapear etapas do funil e ver onde os usuários saem
  → Configurar: Etapa 1 = page_view /produto → Etapa 2 = add_to_cart → Etapa 3 = purchase
  → Resultado: % que passou de cada etapa para a próxima
  → Gargalo: etapa com maior queda = prioridade de otimização

Caminho (Path Exploration):
  → Ver o fluxo de páginas que os usuários percorrem antes de converter
  → Identificar páginas que precedem conversões vs páginas que levam a saída

Sobreposição de Segmentos (Segment Overlap):
  → Ver quantos usuários estão em múltiplos segmentos ao mesmo tempo
  → Exemplo: "usuários vindos de Meta E que viram a página /precos E converteram"

Coorte (Cohort Exploration):
  → Analisar comportamento ao longo do tempo por coorte de aquisição
  → Exemplo: usuários que vieram em janeiro — quantos voltaram em fevereiro, março?
  → Útil para medir retenção e LTV por canal de aquisição
```

### Vinculação com Google Ads e importação de conversões

```
Por que vincular GA4 ao Google Ads:
  → Google Ads Smart Bidding usa dados de conversão do GA4 (mais preciso que tag direta)
  → Importar audiences do GA4 para Google Ads para remarketing
  → Ver dados de GA4 dentro do Google Ads (sessões, bounce, tempo no site por campanha)

Como vincular:
  GA4 → Admin → Vinculações de produto → Google Ads → Vincular

Importar conversões GA4 → Google Ads:
  Google Ads → Ferramentas → Conversões → Importar → Google Analytics 4 → selecionar conversões

  Priorizar:
  → Se usar GA4 como fonte: desativar a tag de conversão direta do Google Ads (evitar dupla contagem)
  → Verificar: em Google Ads, as conversões importadas do GA4 têm tag "GA4 import"

Audiences (públicos para remarketing no Google Ads):
  GA4 → Admin → Audience → Criar audiences com condições avançadas
  Exemplos de audiences úteis:
    Visitantes LP produto (30d): page_location contains "/produto"
    Compradores (90d): evento purchase concluído
    Leads (60d): evento generate_lead concluído
    Alto engajamento (30d): engaged_sessions > 3
  → Publicar no Google Ads para usar em Display, Search (RLSA) e YouTube
```

---

## Templates prontos

### Checklist de configuração GA4 para campanha

```markdown
## GA4 — Checklist de Configuração — [Projeto]

### Propriedade
- [ ] GA4 criado e tag instalada em todas as páginas (via GTM)
- [ ] Domínio do site verificado nas configurações
- [ ] Filtro de IP interno adicionado (IP do escritório — não contaminar dados com visitas internas)
- [ ] Retenção de dados: ajustada para 14 meses (padrão é 2 meses)

### Eventos
- [ ] page_view disparando em todas as páginas
- [ ] Eventos de e-commerce configurados: view_item, add_to_cart, begin_checkout, purchase
- [ ] OU generate_lead configurado na página de obrigado/formulário (lead gen)
- [ ] Parâmetro transaction_id único no purchase (sem duplicação)
- [ ] Parâmetros value e currency presentes no purchase/lead (se aplicável)

### Conversões
- [ ] Evento de conversão principal marcado como conversão (purchase ou generate_lead)
- [ ] Valor de conversão configurado (para e-commerce e lead gen com ticket definido)

### UTMs
- [ ] Padrão de UTM definido e documentado
- [ ] Campanhas de Meta Ads com UTMs automáticos ou manuais
- [ ] Campanhas de Google Ads com auto-tagging ativado (gclid)
- [ ] Links de email com UTMs manuais

### Vinculações
- [ ] Google Ads vinculado
- [ ] Conversões importadas do GA4 para o Google Ads
- [ ] Search Console vinculado (para dados de SEO)
```

---

## Checklist de qualidade

- [ ] GA4 instalado via GTM (não código direto — mais fácil de manter)
- [ ] Evento purchase com transaction_id único (sem duplicação de compras)
- [ ] Parâmetro value presente em todos os eventos de conversão com valor
- [ ] UTMs padronizados e documentados antes da primeira campanha
- [ ] Conversões importadas do GA4 para o Google Ads (não duplicar com tag direta)
- [ ] Funil de conversão configurado no Explorations para diagnóstico contínuo

---

## Armadilhas comuns

**Sem filtro de IP interno:** dev e equipe acessam o site centenas de vezes por semana. Dados contaminados com visitas internas. Taxa de conversão aparece artificial. Adicionar IP do escritório como filtro.

**Transaction_id duplicado:** loja que regenera o mesmo ID de pedido em retentativas de compra. GA4 conta 2 compras para 1 real. Usar ID único e imutável por pedido.

**UTMs sem padronização:** "Facebook" em uma campanha, "facebook" em outra, "fb" em outra. GA4 cria 3 canais diferentes. Definir padrão com minúsculas e manter rigoroso.

**Conversão sem valor:** generate_lead marcado como conversão sem parâmetro de value. GA4 conta os leads mas relatório de receita fica zerado. Smart Bidding do Google Ads não consegue otimizar por valor. Sempre incluir value estimado (mesmo que seja CPL meta estimado).

**Retenção de dados padrão:** GA4 vem com 2 meses de retenção. Após 2 meses, dados de usuário somem das Explorations. Mudar para 14 meses imediatamente após criar a propriedade.

---

## Referências confiáveis

- [Google — GA4 Event Reference](https://developers.google.com/analytics/devguides/collection/ga4/reference/events) — verificado 2026-05-01
- [Google — GA4 e-commerce](https://developers.google.com/analytics/devguides/collection/ga4/ecommerce) — verificado 2026-05-01
- [Google — Vincular GA4 ao Google Ads](https://support.google.com/analytics/answer/9379420) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [analytics-ga4-conversoes.changelog.md](analytics-ga4-conversoes.changelog.md)
