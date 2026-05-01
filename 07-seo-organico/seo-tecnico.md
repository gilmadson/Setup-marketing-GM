# SEO: Técnico

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 07-seo-organico

---

## Quando usar / Quando não usar

**Usar quando:**
- Site novo antes de lançar — corrigir problemas técnicos antes de qualquer conteúdo
- Site com tráfego orgânico caindo sem motivo aparente — pode ser problema técnico
- Migrações de domínio ou plataforma — sem cuidado técnico, perde-se ranking

**Não usar quando:**
- Site muito novo (< 3 meses) sem conteúdo — SEO técnico perfeito sem conteúdo não rankeia nada
- Budget de marketing todo em paid — SEO técnico tem ROI no longo prazo (6-12 meses)

---

## Pré-requisitos

```
- Acesso ao servidor ou CMS (para sitemap, robots.txt, redirecionamentos)
- Google Search Console configurado e verificado
- Google Analytics 4 vinculado ao Search Console
- Ferramenta de auditoria: Screaming Frog (gratuito até 500 URLs), Ahrefs ou SEMrush (pago)
- Para Schema: acesso ao código HTML ou GTM para injeção de JSON-LD
```

---

## Padrões e convenções

### Indexação — controlar o que o Google vê

```
robots.txt:
  → Arquivo de texto em /robots.txt que instrui crawlers sobre o que rastrear
  → Não confundir com noindex: robots.txt bloqueia o RASTREAMENTO, noindex bloqueia a INDEXAÇÃO

  Estrutura básica:
  User-agent: *
  Disallow: /admin/
  Disallow: /checkout/
  Disallow: /?s=          (busca interna — não indexar resultados de busca)
  Disallow: /tag/         (páginas de tag do WordPress — thin content)
  Allow: /

  Importante: bloquear pelo robots.txt NÃO remove do índice — só impede rastreamento futuro.
  Para remover do índice: usar noindex meta tag ou URL Removal no Search Console.

Meta robots (noindex, nofollow):
  Noindex: não indexar esta página
    <meta name="robots" content="noindex">
    Usar em: páginas de agradecimento, páginas de login, parâmetros de URL (paginação desnecessária)

  Nofollow: não seguir os links desta página
    <meta name="robots" content="nofollow">
    Raro — usar só em páginas de login ou muito privadas

  Noindex + Nofollow combinado:
    <meta name="robots" content="noindex, nofollow">

Sitemap.xml:
  → Mapa de todas as URLs importantes do site para o Google indexar
  → Localização: /sitemap.xml ou /sitemap_index.xml (para sites grandes)
  → Como gerar:
     WordPress: plugin Yoast SEO ou Rank Math gera automaticamente
     Outros CMSs: gerar via Screaming Frog ou ferramenta online
     Shopify: gerado automaticamente
  → Submeter no Search Console: Google Search Console → Sitemaps → Adicionar URL

  Regras:
  → Incluir apenas URLs que você quer indexar (não incluir noindex, 404, redirecionadas)
  → Atualizar automaticamente quando publicar novo conteúdo
  → Limite: 50.000 URLs por sitemap (usar sitemap index para sites maiores)

Forçar reindexação (Search Console):
  → Search Console → URL Inspection → Solicitar indexação
  → Usar após: publicar página nova, atualizar conteúdo importante, corrigir erro
  → Limite: ~10-12 solicitações manuais por dia por propriedade
```

### Redirects — preservar ranking nas mudanças

```
Tipos de redirect:
  301 (Permanent Redirect):
    → Redirect permanente — transfere ~90% do link equity (PageRank) para a nova URL
    → Usar para: mudança de URL definitiva, migração de domínio, HTTPS redirect
    → Configuração Apache (.htaccess): Redirect 301 /pagina-antiga/ https://site.com/pagina-nova/
    → Nginx: return 301 https://seusite.com$request_uri;

  302 (Temporary Redirect):
    → Redirect temporário — não transfere link equity
    → Usar para: teste A/B de URL, manutenção temporária
    → Nunca usar 302 para redirecionamentos permanentes (perda de ranking)

  Meta Refresh (obsoleto):
    → Redirect no HTML da página — não usar para SEO
    → Bots podem não seguir, perda de link equity

Redirect chains (evitar):
  → URL A → redireciona para B → redireciona para C
  → Cada hop perde parte do link equity e aumenta tempo de resposta
  → Auditar e corrigir: URL A → diretamente para C (redirect direto)

Redirect durante migração de domínio:
  → 301 de cada URL antiga para URL nova equivalente
  → Não redirecionar tudo para a home (perde link equity específico por página)
  → Manter redirects por pelo menos 1 ano após a migração
  → Notificar no Search Console: Configurações → Mudança de endereço

Canonical tag — evitar conteúdo duplicado:
  <link rel="canonical" href="https://seusite.com/pagina-original/">
  → Indica ao Google qual é a URL "oficial" quando existem variantes
  → Usar em: páginas com parâmetros de URL, conteúdo sindicado, versões mobile/desktop separadas
  → Exemplos de duplicação:
     https://site.com/produto/ vs https://site.com/produto?cor=azul
     http:// vs https:// (resolver com redirect 301, não canonical)
     www vs não-www (resolver com redirect 301)
```

### Core Web Vitals — SEO e experiência do usuário

```
Google usa Core Web Vitals como fator de ranking desde 2021.
(Para detalhes técnicos de cada métrica e como otimizar, ver criativos-landing-page-cro)

Impacto no ranking:
  → Não é fator dominante (conteúdo e links ainda importam mais)
  → Desempata entre páginas de qualidade similar
  → Critical em: e-commerce (cada segundo = conversões perdidas) e sites de notícia

Ferramentas de medição específicas para SEO:
  Google Search Console → Core Web Vitals:
    → Dados REAIS de usuários (não teste de laboratório)
    → Separa mobile e desktop
    → Mostra URLs com "Necessita de melhoria" e "Ruim"
    → Priorizar: mobile (maioria do tráfego de busca)

  CrUX (Chrome User Experience Report):
    → Dataset público do Google com dados reais de CWV por domínio
    → Consultar em: PageSpeed Insights ou diretamente via BigQuery
```

### Structured Data — Schema.org

```
O que é:
  → Marcação de dados estruturados que ajuda o Google a entender o conteúdo da página
  → Não muda o visual para o usuário — é código invisível para o browser
  → Benefício: pode gerar Rich Results (estrelas, FAQ, preço) nos resultados de busca

Como implementar (JSON-LD — método recomendado pelo Google):
  → Bloco de script com tipo application/ld+json no <head> ou <body>
  → Não requer alteração do HTML existente

Tipos mais úteis por tipo de site:

  Organization (todas as empresas):
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Organization",
    "name": "Nome da Empresa",
    "url": "https://seusite.com",
    "logo": "https://seusite.com/logo.png",
    "contactPoint": {
      "@type": "ContactPoint",
      "telephone": "+55-11-1234-5678",
      "contactType": "customer service"
    },
    "sameAs": [
      "https://www.instagram.com/seusite",
      "https://www.linkedin.com/company/seusite"
    ]
  }
  </script>

  Product (e-commerce):
  {
    "@type": "Product",
    "name": "Nome do Produto",
    "image": "https://seusite.com/produto.jpg",
    "description": "Descrição do produto",
    "brand": {"@type": "Brand", "name": "Marca"},
    "offers": {
      "@type": "Offer",
      "price": "297.00",
      "priceCurrency": "BRL",
      "availability": "https://schema.org/InStock"
    },
    "aggregateRating": {
      "@type": "AggregateRating",
      "ratingValue": "4.8",
      "reviewCount": "312"
    }
  }

  FAQ (gera resultado expandido com perguntas visíveis na SERP):
  {
    "@type": "FAQPage",
    "mainEntity": [{
      "@type": "Question",
      "name": "Quanto tempo para ver resultados com tráfego pago?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Geralmente 30-60 dias para sair da fase de aprendizado..."
      }
    }]
  }

  LocalBusiness (negócios com endereço físico):
  {
    "@type": "LocalBusiness",
    "name": "Nome do Negócio",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Rua X, 123",
      "addressLocality": "São Paulo",
      "addressRegion": "SP",
      "postalCode": "01234-000",
      "addressCountry": "BR"
    },
    "telephone": "+55-11-1234-5678",
    "openingHours": "Mo-Fr 09:00-18:00"
  }

Teste de validação:
  → Google Rich Results Test: search.google.com/test/rich-results
  → Schema.org Validator: validator.schema.org
  → Após implementar, verificar no Search Console se erros aparecem
```

### Auditoria técnica — o que checar regularmente

```
Ferramentas:
  Screaming Frog (gratuito até 500 URLs):
    → Rastreia o site como o Google — mostra: status codes, títulos, meta descriptions, headers, links
    → Identificar: 404, redirects em cadeia, páginas sem title, conteúdo duplicado, links quebrados

  Google Search Console:
    → Erros de cobertura (páginas excluídas da indexação e por quê)
    → Performance de cliques e impressões por keyword e URL
    → Core Web Vitals por URL
    → Links internos e externos

Auditoria mensal (sites ativos):
  → Search Console → Cobertura → verificar novos erros (404, soft 404, noindex inesperado)
  → Core Web Vitals → verificar se novas páginas têm problemas
  → Screaming Frog → rodar no site a cada 3 meses ou após grandes mudanças

Checklist de problemas técnicos críticos:
  □ Versão HTTPS (não HTTP) com redirect 301 de todas as versões HTTP
  □ www vs não-www: 1 versão canônica com redirect da outra
  □ sitemap.xml submetido e sem erros no Search Console
  □ robots.txt sem bloqueio acidental de páginas importantes
  □ Todas as páginas principais indexadas (verificar via Search Console)
  □ Sem redirect chains > 2 hops
  □ Sem conteúdo duplicado sem canonical
  □ Title e meta description únicos em cada página (verificar com Screaming Frog)
  □ LCP < 2.5s no mobile (PageSpeed Insights)
  □ Schema.org implementado nas páginas principais
```

---

## Templates prontos

### Checklist de lançamento de site novo

```markdown
## SEO Técnico — Checklist de Lançamento — [Site]

### HTTPS e redirecionamentos
- [ ] SSL ativo e renovação automática configurada
- [ ] HTTP → HTTPS redirect 301 (todas as versões)
- [ ] www → não-www (ou vice-versa) com 301

### Indexação
- [ ] sitemap.xml gerado e submetido no Search Console
- [ ] robots.txt sem bloqueio de páginas importantes
- [ ] Nenhuma página relevante com noindex acidental
- [ ] Search Console verificado com a propriedade correta

### On-page técnico
- [ ] Tag <title> única em todas as páginas (50-60 chars)
- [ ] Meta description única em todas as páginas (150-160 chars)
- [ ] H1 único por página, com keyword principal
- [ ] Imagens com atributo alt text descritivo
- [ ] Links internos conectando páginas relacionadas

### Performance
- [ ] PageSpeed Insights mobile score > 70
- [ ] LCP < 2.5s (mobile)
- [ ] Imagens em WebP ou AVIF

### Structured Data
- [ ] Organization schema na home
- [ ] Product schema nas páginas de produto (e-commerce)
- [ ] FAQ schema nas páginas com perguntas frequentes
- [ ] LocalBusiness schema (negócios físicos)
- [ ] Validado no Rich Results Test

### Analytics
- [ ] GA4 instalado e verificado
- [ ] Search Console vinculado ao GA4
```

---

## Checklist de qualidade

- [ ] Search Console com 0 erros críticos de cobertura
- [ ] robots.txt não bloqueia nenhuma página importante
- [ ] sitemap.xml submetido e com 0 erros
- [ ] Redirect 301 de HTTP → HTTPS e www/não-www configurado
- [ ] Nenhum redirect chain com mais de 2 hops
- [ ] Schema.org implementado e validado nas páginas principais
- [ ] Core Web Vitals no verde (mobile) no Search Console

---

## Armadilhas comuns

**Bloquear CSS/JS no robots.txt:** bloqueio herdado de versão antiga que impede o Google de renderizar as páginas. Google precisa ver o CSS e JS para entender a página como usuário. Verificar no Search Console → URL Inspection → ver como o Google renderiza.

**Canonical errado:** página de produto com canonical apontando para a home. Todo o link equity vai para a home, a página do produto nunca rankeia. Verificar canônicos em todas as páginas com Screaming Frog.

**Sitemap com páginas noindex:** incluir no sitemap páginas que têm <meta name="robots" content="noindex">. Confunde o Google — sinal contraditório. Sitemap deve conter apenas URLs indexáveis.

**Schema com dados errados:** preço de produto no Schema diferente do preço na página. Google rejeita e não mostra rich results. Schema deve ser espelho exato do que está visível na página.

**Redirect chain após migração:** migração faz URL A → redirecionar para B, depois edição posterior adiciona B → C. Cadeia A→B→C perde link equity. Auditar e consolidar para A→C diretamente.

---

## Referências confiáveis

- [Google — Search Console Help](https://support.google.com/webmasters/) — verificado 2026-05-01
- [Google — Rich Results Test](https://search.google.com/test/rich-results) — verificado 2026-05-01
- [Schema.org — Full Hierarchy](https://schema.org/docs/full.html) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [seo-tecnico.changelog.md](seo-tecnico.changelog.md)
