# Google Ads: Display e Remarketing

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 03-google-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- Remarketing para quem visitou o site mas não converteu — recuperar usuários quentes
- TOFU/MOFU de awareness visual — alcançar público durante a navegação com custo por impressão baixo
- Nurturing de leads — manter a marca presente durante o ciclo de decisão longo

**Não usar quando:**
- Budget muito limitado — priorizar Search (intenção) antes de Display (interrupção)
- Produto de compra por impulso com ciclo imediato — remarketar quem saiu 1 hora atrás sem sentido
- Sem pixel ou lista de remarketing — Display puro sem remarketing tem qualidade de público muito baixa

---

## Pré-requisitos

```
- Tag do Google Ads instalada no site (Google Tag Manager recomendado)
- Conversões configuradas no Google Ads
- Lista de remarketing com pelo menos 100 usuários (obrigatório para remarketing)
- Imagens nos formatos corretos para Responsive Display Ads
- Pixel ativo há pelo menos 30 dias (para listas de remarketing terem volume)
```

---

## Padrões e convenções

### GDN — Google Display Network

```
O que é:
  → Rede de mais de 2 milhões de sites, apps e YouTube que exibem anúncios do Google
  → CPM geralmente mais baixo que Meta Ads (mas qualidade de audience menor)
  → Formatos: banner estático, responsive display, HTML5

Quando GDN funciona bem:
  → Remarketing (melhor uso) — público já tem contexto sobre a marca
  → Contextual targeting (targeting por conteúdo) — aparecer em conteúdo relevante
  → Awareness de marca com CPM baixo — alcance amplo a baixo custo
```

### Targeting — opções de segmentação

```
1. Audience Segments (Audiências):

  In-Market Audiences:
    → Usuários que o Google identifica como "em busca ativa" de uma categoria
    → Exemplos: "In-market: Serviços de marketing", "In-market: Automóveis usados"
    → Melhor qualidade dentre as audiências de Display puro (fora do remarketing)

  Affinity Audiences:
    → Baseadas em interesses gerais de longo prazo — "Entusiastas de tecnologia", "Viajantes frequentes"
    → CPM mais baixo, menos qualificado — usar para TOFU de alcance amplo

  Custom Audiences (Intent):
    → Criar audiência baseada em keywords que o usuário pesquisou no Google
    → Muito poderoso: segmentar quem buscou [keyword do concorrente] ou [keyword do produto]
    → Como criar: Audience Manager → Custom Audience → Pessoas que pesquisaram esses termos

  Custom Audiences (Interest):
    → Baseadas em URLs que o usuário visita — criar audiência de quem visita sites do nicho
    → Exemplo: audiência de quem visita sites de empreendedorismo

  Similar Audiences:
    → Google gera automaticamente público similar aos seus remarketing lists
    → Qualidade próxima dos LAL do Meta

2. Contextual Targeting:

  Keywords contextuais:
    → Anúncio aparece em páginas cujo conteúdo contém as keywords definidas
    → Sem relação com o usuário — relação com o conteúdo da página
    → Usar para nichos muito específicos onde o conteúdo é muito segmentado

  Topics:
    → Categorias de conteúdo de páginas (Tecnologia, Esportes, Finanças, etc.)
    → Menor controle que keywords contextuais — mais volume, menos precisão

3. Placements (Posicionamentos manuais):
    → Selecionar manualmente sites, canais YouTube ou apps específicos
    → Usar quando conhece exatamente onde o público está
    → Exemplos: "aparecer no site X que meu público lê" ou "canal Y do YouTube"
    → Custo: placements premium geralmente têm CPM mais alto

4. Remarketing (melhor uso de Display):
  → Ver seção específica abaixo
```

### Remarketing — configuração e estratégia

```
Tipos de lista de remarketing:

  Visitantes do site (por URL):
    → Todos os visitantes → últimos 30/60/90/180 dias
    → Visitantes de página específica: /produto, /precos, /obrigado
    → Excluídos: /obrigado (já converteram)

  Usuários que realizaram evento:
    → AddToCart sem Purchase (abandono de carrinho — BOFU mais quente)
    → ViewContent sem Lead (viu produto mas não converteu)
    → InitiateCheckout sem Purchase

  Clientes (Customer Match):
    → Upload de lista de e-mails de clientes para criar audiência
    → Usar para: exclusão de clientes de campanhas de aquisição

  YouTube viewers:
    → Quem assistiu vídeos do canal, se inscreve, comentou

Janelas de tempo por temperatura:
  7 dias → mais quente → lance mais alto, mensagem de urgência
  30 dias → quente → lance médio, lembrete
  90 dias → morno → lance normal, conteúdo de nurturing
  180 dias → frio → lance baixo, awareness

RLSA — Remarketing Lists for Search Ads:
  → Adicionar listas de remarketing a campanhas de Search
  → Não muda quem vê o anúncio — ajusta o lance quando alguém da lista pesquisa
  → Exemplo: +50% de lance para quem já visitou o site e agora busca a keyword
  → Mais impactante que Display remarketing para conversão direta
```

### Responsive Display Ads (RDA) — specs e boas práticas

```
Assets necessários:
  Imagens:
    → Horizontal (1.91:1): mín 600×314px, recomendado 1200×628px
    → Quadrada (1:1): mín 300×300px, recomendado 1200×1200px
    → Carregar pelo menos 5 imagens (máx 15) — Google testa combinações
  
  Logo:
    → Horizontal (4:1): mín 512×128px, recomendado 1200×300px
    → Quadrado (1:1): mín 128×128px, recomendado 1200×1200px
    → Fundo transparente ou branco

  Headlines:
    → Curto (máx 25 chars): 1 obrigatório, até 5
    → Longo (máx 90 chars): 1 obrigatório, até 5
    → Incluir keyword e proposta de valor

  Descriptions (máx 90 chars):
    → 1 obrigatório, até 5
    → Detalhar o benefício, não repetir o headline

  Vídeo (opcional):
    → YouTube URL — adicionar quando disponível
    → Melhora entrega em posicionamentos de vídeo

Boas práticas de imagem:
  → Não usar logo dentro da imagem (Google coloca o logo separado)
  → Imagem sem texto — Google adiciona headline em cima da imagem
  → Alta contraste — imagem com fundo escuro/claro que destaque o produto
  → Produto em uso (lifestyle) converte melhor que produto isolado
```

### Controle de frequência e exclusões

```
Frequência (cap):
  → Configurar limite de impressões por usuário por dia/semana/mês
  → Recomendado: máx 3x/dia ou 15x/semana para remarketing
  → Sem cap: usuário vê o mesmo banner 50x por dia — efeito irritação, CPM sobe

Exclusões de conteúdo (obrigatórias):
  → Configuração de campanha → Exclusões de conteúdo
  → Marcar: Conteúdo sensível, Tragédias e conflitos, Conteúdo adulto
  → Evitar: aparecer em conteúdo que contrasta negativamente com a marca

Exclusões de placement:
  → Listar domínios ou apps onde não quer aparecer
  → Comuns: apps de jogos (muito clique acidental), sites de notícias de baixa qualidade
  → Como identificar: Placement Report → filtrar por CPC alto e 0 conversões → excluir

View-through Conversions:
  → Conversão registrada quando usuário VIU o banner (sem clicar) e depois converteu
  → Janela padrão: 1 dia
  → Atenção: infla o relatório de Display — não contar como conversão real para decisões de budget
  → Usar apenas Click-through Conversions para medir performance real do Display
```

---

## Templates prontos

### Campanha de remarketing multi-janela

```markdown
## Campanha Display — Remarketing — [Produto]

### Targeting por temperatura

**Ad Group 1: Hot (7 dias) — Urgência**
- Audience: AbandonouCheckout 7d + Visitantes LP 7d (excl. convertidos)
- Mensagem: "Ainda pensando? [Oferta especial / prazo limitado]"
- Lance: +50% em relação ao Ad Group base

**Ad Group 2: Warm (30 dias) — Lembrete**
- Audience: VisitanteSite 30d (excl. 7d e convertidos)
- Mensagem: "[Benefício principal] — Quando precisar, estamos aqui"
- Lance: base

**Ad Group 3: Cool (90 dias) — Reengajamento**
- Audience: VisitanteSite 90d (excl. 30d e convertidos)
- Mensagem: "[Novidade ou conteúdo novo desde a última visita]"
- Lance: -20% em relação ao base

### Assets de criativos
- Imagem horizontal 1200×628: [descrição]
- Imagem quadrada 1200×1200: [descrição]
- Logo quadrado 1200×1200: [arquivo]
- Headline curto: [texto]
- Headline longo: [texto]
- Description: [texto]
```

---

## Checklist de qualidade

- [ ] Tag do Google Ads instalada e conversões configuradas
- [ ] Listas de remarketing criadas com pelo menos 100 usuários
- [ ] Frequência cap configurada (máx 3x/dia por usuário)
- [ ] Exclusões de conteúdo sensível ativadas
- [ ] RDA com pelo menos 5 imagens e 5 headlines variados
- [ ] Convertidos excluídos do remarketing de aquisição
- [ ] RLSA configurado nas campanhas de Search para ajustar lances
- [ ] View-through conversions não sendo contadas para decisões de budget

---

## Armadilhas comuns

**Display sem remarketing:** segmentar público frio em Display puro sem dados de quem converteu. Taxa de conversão muito baixa. Usar Display principalmente para remarketing e In-Market audiences.

**Sem exclusões de placement:** aparecer em apps de jogos mobile onde cliques são acidentais (tapping no jogo). CTR alto, conversão zero. Revisar Placement Report e excluir regularmente.

**Sem cap de frequência:** banner exibido 40x para o mesmo usuário em 1 dia. Efeito de banner blindness + associação negativa à marca. Sempre configurar frequência máxima.

**Contar view-through como conversão real:** "Display gerou 200 conversões!" — mas 180 são view-through. Decisão de escalar Display baseada em dado falso. Filtrar apenas click-through para análise real.

**Imagem com texto em cima:** criativo com frase em cima da imagem → Google coloca headline por cima → texto sobreposto confuso. Imagem de Display deve ser visual puro, sem texto — Google adiciona os textos.

---

## Referências confiáveis

- [Google — Remarketing no Google Ads](https://support.google.com/google-ads/answer/2454000) — verificado 2026-05-01
- [Google — Responsive Display Ads](https://support.google.com/google-ads/answer/6363750) — verificado 2026-05-01
- [Google — Custom Audiences](https://support.google.com/google-ads/answer/2497941) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [google-display.changelog.md](google-display.changelog.md)
