# Outros Canais: TikTok Ads

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 04-outros-canais

---

## Quando usar / Quando não usar

**Usar quando:**
- Público-alvo está na faixa 18-35 anos — maior concentração de usuários ativos
- Produto visual ou com demonstração natural em vídeo curto (beleza, moda, alimentação, fitness, tech)
- Testando novo canal com 10% do budget (ver estrategia-budget-distribuicao)
- Quer alcançar público que não usa tanto Instagram/Facebook

**Não usar quando:**
- Público é B2B sênior (40+) — penetração ainda baixa nesse segmento no Brasil
- Sem capacidade de produzir vídeo vertical nativo regularmente — TikTok exige volume criativo alto
- Budget < R$ 50/dia — mínimo da plataforma por Ad Group
- Produto com baixo apelo visual ou muito técnico

---

## Pré-requisitos

```
- Conta no TikTok Ads Manager (ads.tiktok.com)
- Pixel do TikTok instalado no site (ou integração via parceiro como Shopify)
- Vídeos verticais 9:16 em 1080×1920px prontos — não adaptar criativo horizontal
- Budget mínimo: R$ 50/dia por Ad Group (restrição da plataforma)
- Para Spark Ads: conta orgânica no TikTok com posts publicados
```

---

## Padrões e convenções

### Hierarquia de conta — Campaign → Ad Group → Ad

```
CAMPAIGN:
  → Define: Objetivo, Budget de campanha (se Campaign Budget Optimization)
  → Objetivos disponíveis:
     Awareness: Reach, Video Views
     Consideration: Traffic, App Installs, Video Views (engagement)
     Conversion: Conversions, Catalog Sales, Lead Generation

AD GROUP:
  → Define: Público, Posicionamentos, Budget, Otimização, Prazo
  → Budget mínimo: R$ 50/dia (mínimo absoluto da plataforma)
  → Budget recomendado: R$ 100-200/dia para conversão (fase de aprendizado)

AD:
  → Define: Vídeo, Copy (texto), CTA, URL de destino
  → 3-5 vídeos por Ad Group para o algoritmo testar
```

### Formatos de anúncio

```
IN-FEED ADS (mais comum):
  → Aparece no feed "Para Você" do usuário — aparência de post orgânico
  → Duração: 5-60s (recomendado 9-15s para conversão, 15-30s para educação)
  → Proporção: 9:16 (vertical) — único formato que performa bem
  → Cobrança: CPM, CPC ou CPV (depende do objetivo)
  → Chave: deve parecer um TikTok orgânico — não um anúncio tradicional

SPARK ADS:
  → Amplificar um post orgânico existente (próprio ou de criador)
  → Próprio: pegar post do perfil da marca e colocar budget de anúncio
  → De criador: solicitar permissão de uso do vídeo do criador e usar como anúncio
  → Vantagem: comentários, curtidas e seguidores do post orgânico aparecem no anúncio
         → Prova social acumulada aumenta credibilidade
  → Como usar criadores: TikTok Creator Marketplace → solicitar autorização de Spark

TOPVIEW:
  → Primeiro vídeo que o usuário vê ao abrir o app — tela cheia por até 60s
  → Alta visibilidade, alto custo — reservado via equipe comercial TikTok
  → Usar para: lançamentos, Black Friday, campanhas de alto impacto

BRAND HASHTAG CHALLENGE:
  → Criar hashtag de desafio — usuários criam vídeos com a hashtag da marca
  → Alto potencial de viralização — UGC (conteúdo gerado por usuários)
  → Custo elevado — pacote especial com equipe TikTok
  → Métricas: vídeos criados, views da hashtag, participações

BRANDED EFFECTS (filtros e efeitos):
  → Criar efeito/filtro personalizado da marca no TikTok
  → Usuários aplicam o efeito em seus próprios vídeos
  → Complemento a Branded Hashtag Challenge
```

### Criativo nativo — a regra mais importante do TikTok Ads

```
"Não faça anúncios. Faça TikToks."
— Diretriz oficial do TikTok for Business

O que significa na prática:
  → Vídeo deve parecer conteúdo orgânico do feed "Para Você"
  → Evitar: logos grandes, texto corporativo, locução formal, cortes de edição "de comercial"
  → Usar: vídeo filmado no celular (ou com aparência de celular), narração informal, trending sounds
  → Texto na tela: captions em cima do vídeo como TikTok orgânico (não like: banners estáticos)

Hook nos primeiros 3 segundos (mais crítico que no Meta):
  → TikTok tem scroll mais rápido que qualquer outra plataforma
  → Se não prender em 3s, usuário já foi
  → Técnicas:
     Pergunta direta à câmera: "Você sabia que dá pra ganhar R$ 5k/mês com isso?"
     Resultado visual imediato: mostrar o before/after direto no início
     Texto de gancho: "POV: você descobriu o erro que todo mundo comete"
     Som/música trending: usar áudio popular aumenta entrega orgânica

Elementos de TikTok nativo:
  → Texto sobreposto (caption style) nos momentos-chave do vídeo
  → Música ou som do TikTok (usar da biblioteca de áudios comerciais do TikTok)
  → Velocidade de edição rápida — TikTok tem ritmo de corte mais acelerado
  → Trending formats: POV, "coisas que ninguém te conta sobre X", before/after

Tipos de criativo por objetivo:
  TOFU: trend native (usar formato de tendência do momento), challenge-style
  MOFU: educational (tutorial, explicação, comparativo)
  BOFU: testimonial, demo do produto, oferta com urgência
```

### TikTok Pixel — configuração

```
Instalação:
  → TikTok Ads Manager → Ativos → Eventos → Criar Pixel
  → Opções: código manual, Google Tag Manager (parceiro), integração nativa (Shopify, WooCommerce)

Eventos padrão (mesmo conceito do Meta):
  ViewContent → usuário viu página de produto
  AddToCart → produto adicionado ao carrinho
  InitiateCheckout → início do checkout
  PlaceAnOrder → pedido realizado (equivale ao Purchase do Meta)
  CompletePayment → pagamento confirmado
  SubmitForm → formulário enviado (lead)

Parâmetros do evento PlaceAnOrder:
  {
    "content_id": "SKU-123",
    "content_type": "product",
    "currency": "BRL",
    "value": 297.00,
    "order_id": "pedido-456"
  }

Teste do Pixel:
  → Ads Manager → Eventos → Pixel → Test Events
  → Testar cada evento antes de lançar campanha de conversão

TikTok Events API (equivale ao CAPI do Meta):
  → Envio de eventos server-side para contornar bloqueio de cookies
  → Configurar em paralelo com o Pixel para máxima cobertura
```

### Segmentação de público

```
Audiências de interesse:
  → Categorias de interesse (Beleza, Fitness, Tecnologia, Negócios...)
  → Interações com conteúdo: quem curtiu/comentou/compartilhou vídeos de determinada categoria

Audiências comportamentais:
  → Comportamento de compra online
  → Comportamento de uso do app

Custom Audiences:
  → Visitantes do site (via Pixel) — últimos 7/14/30/60/90/180 dias
  → Lista de clientes (upload de e-mail/telefone)
  → Engajadores do perfil TikTok (visualizações, curtidas, seguidores)

Lookalike Audiences:
  → A partir de Custom Audiences — 1%/2%/5% de similaridade
  → Funciona similar ao Meta LAL

Hashtag Targeting (diferencial do TikTok):
  → Segmentar usuários que interagem com hashtags específicas
  → Exemplo: usuários que interagem com #empreendedorismo, #marketingdigital

Creator Targeting:
  → Segmentar seguidores de criadores específicos (concorrentes, influenciadores do nicho)

Tamanho ideal de público:
  → Mínimo: 1.000 usuários (Custom Audience)
  → Ideal para testes: 500k-2M
  → Para escala: 2M+
```

### Budget e fase de aprendizado

```
Mínimos da plataforma (2026):
  Campanha: R$ 150/dia (Campaign Budget)
  Ad Group: R$ 50/dia

Fase de aprendizado:
  → Similar ao Meta — algoritmo precisa de dados para otimizar
  → Meta de conversões para sair do aprendizado: ~50 eventos de otimização em 7 dias
  → Não alterar público, budget ou criativo nos primeiros 7 dias

Protocolo de escala:
  → Mesmo princípio do Meta: aumentar 20-30% por vez, aguardar 72h
  → TikTok tende a ter CPMs mais baixos que Meta no início — escalar quando CPA estiver bom
```

---

## Templates prontos

### Brief de criativo TikTok Ads

```markdown
## Brief Criativo — TikTok In-Feed Ad — [Nome]

**Objetivo:** TOFU / MOFU / BOFU
**Duração:** [9-30s]
**Tom:** Informal, como TikTok orgânico

### Hook (0-3s)
[Descrever a cena de abertura + texto sobreposto de hook]
[Deve prender SEM som — legenda/texto é obrigatório]

### Corpo (3s-[fim -5s])
[O que acontece: demonstração / tutorial / depoimento / problema-solução]

### CTA (últimos 3-5s)
[Verbal + texto na tela + CTA visual do anúncio]

### Elementos nativos
- Música/som: [trending sound ou áudio original]
- Texto sobreposto: [estilo caption TikTok]
- Filmagem: [celular / câmera com aparência de celular]

### KPIs
- View Rate (6s) meta: [%]
- CTR meta: [%]
```

---

## Checklist de qualidade

- [ ] Pixel instalado e testado antes de lançar campanha de conversão
- [ ] Vídeo em 9:16 — nunca adaptar horizontal para TikTok
- [ ] Hook nos primeiros 3 segundos
- [ ] Tom nativo — parece TikTok orgânico, não comercial tradicional
- [ ] Legenda/texto sobreposto em todos os vídeos (80% assiste sem som)
- [ ] Música da biblioteca comercial do TikTok (evitar copyright)
- [ ] 3-5 vídeos por Ad Group para testes
- [ ] Budget mínimo R$ 50/dia por Ad Group
- [ ] Não alterar campanha nos primeiros 7 dias (fase de aprendizado)

---

## Armadilhas comuns

**Adaptar criativo do Meta ou TV:** vídeo horizontal cortado para vertical, com locução formal e logo grande. TikTok rejeita criativo que "parece anúncio". Baixa entrega, CPM alto, performance ruim.

**Budget abaixo do mínimo:** tentar rodar com R$ 30/dia por Ad Group. A plataforma exige R$ 50 — abaixo disso, campanha não entrega.

**Um único vídeo por campanha:** TikTok tem fadiga de criativo mais rápida que Meta. Com 1 vídeo, frequência sobe rapidamente. Mínimo de 3-5 vídeos com ângulos diferentes.

**Ignorar trending sounds:** TikTok prioriza na entrega conteúdo com sons populares. Usar áudio trending (da biblioteca comercial — sem copyright) melhora o alcance orgânico mesmo do anúncio.

**Não usar Spark Ads com UGC:** ter depoimento de cliente em vídeo e não usar como Spark Ad. Spark Ad com UGC de criador real converte melhor que vídeo da marca pelo efeito de prova social acumulada.

---

## Referências confiáveis

- [TikTok for Business — Creative Best Practices](https://www.tiktok.com/business/en-US/blog/tiktok-creative-best-practices) — verificado 2026-05-01
- [TikTok — Pixel Setup](https://ads.tiktok.com/help/article/tiktok-pixel) — verificado 2026-05-01
- [TikTok — Spark Ads](https://ads.tiktok.com/help/article/spark-ads) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [outros-tiktok-ads.changelog.md](outros-tiktok-ads.changelog.md)
