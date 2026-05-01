# Google Ads: Performance Max e Shopping

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 03-google-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- E-commerce com catálogo de produtos e histórico de conversões — PMax + Shopping é o padrão atual
- Quer alcançar todos os canais Google (Search, Display, YouTube, Gmail, Maps, Discover) com 1 campanha
- Conta com pelo menos 30-50 conversões/mês — algoritmo precisa de dados para otimizar

**Não usar quando:**
- Conta nova sem histórico de conversões — algoritmo não tem dados para aprender; iniciar com Search
- Produto de nicho muito específico (B2B técnico) — PMax vai exibir em canais irrelevantes
- Budget < R$ 100/dia — volume insuficiente para o algoritmo distribuir bem entre os canais
- Quer controle granular de keywords — PMax não permite exclusões de keywords (apenas negativos de conta/campanha)

---

## Pré-requisitos

```
- Google Merchant Center configurado e vinculado ao Google Ads (para e-commerce com feed)
- Feed de produtos aprovado no Merchant Center (sem erros críticos)
- Conversões configuradas com valor (Purchase + valor) — obrigatório para Target ROAS
- Google Analytics 4 vinculado ao Google Ads
- Assets de criativo prontos: imagens, headlines, descriptions, logotipo, vídeo (opcional)
- Histórico mínimo recomendado: 30+ conversões nos últimos 30 dias
```

---

## Padrões e convenções

### Performance Max — o que é e como funciona

```
O que é:
  → Campanha que distribui budget automaticamente em TODOS os canais Google:
     Search, Display, YouTube, Gmail, Maps, Discover
  → 1 campanha substituindo potencialmente múltiplas campanhas separadas
  → Algoritmo controla: quem vê, quando, em qual canal, com qual criativo

Como o algoritmo decide:
  → Usa Machine Learning com os dados de conversão da conta
  → Asset Groups: você fornece os assets — Google monta os anúncios
  → Audience Signals: você dá dicas de quem deve converter (não limita, só guia)
  → Quanto mais dados de conversão, melhor o algoritmo escolhe

PMax vs Search:
  PMax → escala em múltiplos canais, menos controle, melhor para e-commerce
  Search → controle de keyword, ideal para intenção específica, serviços B2B
  Recomendação: rodar PMax + Search em paralelo — Search para keywords exatas, PMax para escala
```

### Asset Groups — estrutura de criativos

```
O que é:
  → Conjunto de assets (imagens, textos, vídeos) que o Google combina para criar anúncios
  → Criar 1 Asset Group por tema/categoria de produto ou ângulo de mensagem

Assets obrigatórios por Asset Group:
  Imagens:
    → Horizontal (1.91:1): mín 600×314px, recomendado 1200×628px — OBRIGATÓRIO (mín 1, máx 20)
    → Quadrada (1:1): mín 300×300px, recomendado 1200×1200px — OBRIGATÓRIO (mín 1, máx 20)
    → Vertical (4:5 ou 9:16): recomendado para YouTube/Stories
  
  Logotipo:
    → Quadrado (1:1): mín 128×128px — OBRIGATÓRIO
    → Horizontal (4:1): opcional, mín 512×128px
  
  Headlines (máx 30 chars cada):
    → OBRIGATÓRIO: mín 3, máx 5
    → Incluir keyword principal, benefício, CTA
  
  Headlines longos (máx 90 chars):
    → OBRIGATÓRIO: mín 1, máx 5
  
  Descriptions (máx 90 chars):
    → OBRIGATÓRIO: mín 2, máx 5
  
  Vídeo:
    → Opcional mas recomendado — PMax sem vídeo cria automaticamente um vídeo básico com os assets
    → Formatos: YouTube URL, mín 10 segundos
    → Dica: sempre subir vídeo próprio — o gerado automaticamente é genérico

Asset Group por tema (exemplo — loja de calçados):
  Asset Group 1: Tênis Esportivo (tema + imagens específicas de tênis)
  Asset Group 2: Sapatos Sociais (tema + imagens específicas de social)
  Asset Group 3: Promoção Black Friday (tema sazonal com assets de oferta)

Asset Strength:
  → "Fraco" / "Bom" / "Excelente" — Google avalia variedade e qualidade
  → Meta: "Bom" ou "Excelente" antes de lançar
```

### Audience Signals — guiar o algoritmo

```
O que é:
  → Dicas para o algoritmo de quem tem mais chance de converter
  → Não limita o público — o Google pode alcançar pessoas fora do signal se achar que convertem
  → Pensa como: "Comece por aqui, mas não fique limitado a isso"

Melhores Audience Signals (por qualidade):
  1. Seus dados (Custom Segments):
     → Lista de clientes (Customer Match) — quem já comprou
     → Visitantes do site (pixel) — quem já considerou
     → Segmentos de conversão — quem fez AddToCart ou Lead

  2. Segmentos In-Market:
     → Usuários que o Google classifica como em busca ativa da categoria
     → Exemplo: "In-market: Calçados esportivos"

  3. Interesses e comportamentos:
     → Categorias de interesse relacionadas ao produto

Como configurar:
  → Criar Asset Group → seção Audience Signals
  → Adicionar: Customer Match + Visitantes do site + In-Market relevante
  → Não adicionar sinais demais (5-7 no máximo) — qualidade > quantidade
```

### Google Shopping — Merchant Center e feed de produtos

```
Merchant Center:
  → Plataforma onde fica o catálogo de produtos para Shopping e PMax
  → Vincular ao Google Ads: Merchant Center → Configurações → Vinculações

Feed de produtos — atributos obrigatórios:
  id         → SKU único do produto
  title      → Nome do produto com keyword principal (título é o mais importante para match)
  description → Descrição detalhada com keywords secundárias
  link       → URL do produto (deve corresponder exatamente à página)
  image_link → URL da imagem (mín 100×100px, recomendado 800×800px)
  price      → Preço com moeda: "297.00 BRL"
  availability → in stock / out of stock / preorder
  brand      → Marca do produto
  gtin       → Código de barras EAN/UPC (obrigatório para produtos com código)
  google_product_category → Categoria do Google (usar taxonomia oficial)
  condition  → new / used / refurbished

Atributos opcionais mas que melhoram performance:
  sale_price → Preço promocional (exibe tachado no anúncio)
  color, size, material → Para vestuário/calçados (obrigatório nessas categorias)
  custom_label_0 a 4 → Labels personalizados para segmentar produtos no PMax

Manter feed saudável:
  → Aprovação no Merchant Center > 95% dos produtos
  → Atualizar feed diariamente (preços e disponibilidade mudam)
  → Resolver erros críticos antes de lançar: "Título ausente", "Preço não correspondente"
  → Suplementar título com keywords: "Nike Air Max 270 React Preto Masculino" > "Tênis Nike"
```

### Smart Bidding para PMax

```
Target ROAS (recomendado para e-commerce):
  → Definir o ROAS mínimo desejado
  → Exemplo: "Para cada R$ 1 investido, quero R$ 4 de receita" → Target ROAS = 400%
  → Configurar: 10-20% abaixo do ROAS atual para não travar entrega
  → Aumentar gradualmente à medida que o algoritmo aprende

Target CPA:
  → Para e-commerce que prefere controlar custo por conversão
  → Mais indicado para lead gen via PMax

Maximizar Valor de Conversão (sem meta):
  → Google maximiza receita total sem restrição de ROAS
  → Usar: para descobrir qual ROAS o algoritmo consegue entregar naturalmente
  → Migrar para Target ROAS após 2-4 semanas de dados
```

### Visibilidade limitada do PMax — como contornar

```
Problema: PMax tem pouca transparência
  → Não mostra quais keywords de Search dispararam os anúncios
  → Não mostra performance por canal (Search vs Display vs YouTube)
  → Não permite exclusão de keywords no nível de campanha

Contornos:
  1. Search Terms Report (parcial):
     → Insights → Termos de pesquisa → mostra os principais, não todos
     → Negativar termos ruins: nível de conta → Palavras-chave negativas

  2. Asset Report:
     → Dentro do Asset Group, ver quais assets têm melhor performance (Low/Good/Best)
     → Pausar assets com "Low" e adicionar novos

  3. Campanhas Search em paralelo:
     → Campanhas Search com [Exact] e "Phrase" das melhores keywords
     → Configurar prioridade: Search tem prioridade sobre PMax para aquelas keywords
     → Google prioriza Search quando as keywords são mais específicas

  4. Budget Allocation Insight:
     → Google fornece breakdown aproximado de onde o budget foi — checar mensalmente
```

---

## Templates prontos

### Checklist de lançamento PMax

```markdown
## Lançamento Performance Max — [E-commerce/Produto]

### Merchant Center
- [ ] Feed aprovado > 95%
- [ ] Títulos otimizados com keywords
- [ ] Imagens em alta resolução (mín 800×800px)
- [ ] Preços e disponibilidade corretos e atualizados

### Google Ads
- [ ] Conversões com valor configuradas (Purchase + value)
- [ ] Merchant Center vinculado ao Google Ads
- [ ] Asset Group criado com Asset Strength "Bom" ou "Excelente"
- [ ] Audience Signals configurados (Customer Match + Visitantes)
- [ ] Target ROAS definido (10-20% abaixo do ROAS médio atual)
- [ ] Budget mínimo R$ 100/dia
- [ ] Negative keywords de conta adicionadas

### Monitoramento
- [ ] Revisão semanal: Asset Report → pausar "Low", adicionar novos
- [ ] Revisão semanal: Search Terms Insights → negativar irrelevantes
- [ ] Revisão mensal: ROAS por produto (via supplemental feed custom labels)
```

---

## Checklist de qualidade

- [ ] Merchant Center vinculado e feed aprovado > 95%
- [ ] Conversão com valor configurada antes de lançar
- [ ] Asset Group com Asset Strength "Bom" ou "Excelente"
- [ ] Audience Signals configurados com dados próprios (Customer Match + remarketing)
- [ ] Budget mínimo R$ 100/dia
- [ ] Target ROAS configurado após 2 semanas de dados (não no lançamento)
- [ ] Campanhas Search em paralelo para keywords exatas prioritárias
- [ ] Negative keywords de conta configuradas

---

## Armadilhas comuns

**PMax em conta sem histórico:** algoritmo não tem dados para otimizar. Começa gastando em canais fracos (Display genérico). Iniciar com Search para construir histórico, depois adicionar PMax.

**Feed com títulos ruins:** "Produto 001 Azul" vs "Tênis Nike Air Max 270 Azul Masculino 42". O título é o principal sinal de match para Shopping — investir tempo em otimização.

**Target ROAS muito alto no início:** configurar ROAS 800% quando o histórico é 350%. Google não consegue entregar — underspend. Começar com meta próxima do atual e aumentar progressivamente.

**Confiar 100% no PMax sem Search:** PMax pode pegar buscas de brand do concorrente sem controle. Campanhas Search exatas em paralelo garantem presença nas keywords prioritárias.

**Não negativar irrelevantes:** sem revisão de Search Terms do PMax, vai aparecer em buscas completamente fora do nicho. Verificar Insights → Termos semanalmente e negativar no nível de conta.

---

## Referências confiáveis

- [Google — Performance Max](https://support.google.com/google-ads/answer/10724817) — verificado 2026-05-01
- [Google — Merchant Center — Feed specs](https://support.google.com/merchants/answer/7052112) — verificado 2026-05-01
- [Google — Asset Groups](https://support.google.com/google-ads/answer/11452218) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [google-pmax.changelog.md](google-pmax.changelog.md)
