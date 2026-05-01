# SEO: Conteúdo e Palavras-chave

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 07-seo-organico

---

## Quando usar / Quando não usar

**Usar quando:**
- Criando estratégia de conteúdo para site novo — keywords definem o que escrever
- Site com tráfego estagnado — pesquisa de keyword revela oportunidades não exploradas
- Planejando blog, canal ou hub de conteúdo — topic clusters organizam autoridade temática

**Não usar quando:**
- Sem capacidade de produzir conteúdo regularmente — keyword research sem publicação não gera ranking
- Nicho de interesse altíssimo (advogado/médico/financeiro) sem equipe especialista — E-E-A-T exigente torna concorrência muito difícil sem investimento sério

---

## Pré-requisitos

```
- Google Search Console configurado (ver seo-tecnico)
- Ferramenta de keyword research: Ahrefs, SEMrush, Ubersuggest ou Keyword Planner gratuito
- Acesso ao CMS para editar metadados (title, meta description, H1, alt text)
- Definição do nicho e persona (ver estrategia-personas-comprador)
```

---

## Padrões e convenções

### Pesquisa de palavras-chave — o que analisar

```
Métricas essenciais por keyword:

  Volume mensal:
    → Número médio de buscas por mês (Google BR)
    → Volume alto ≠ melhor — keyword com 200 buscas/mês e baixa dificuldade pode gerar mais resultado que 10.000 com dificuldade alta
    → Ferramentas: Keyword Planner (gratuito, dados aproximados), Ahrefs/SEMrush (pagos, dados precisos)

  Dificuldade de keyword (KD):
    → Score de 0-100 que indica quão difícil é ranquear na 1ª página
    → Ahrefs KD: baseado em quantidade e qualidade de backlinks das páginas ranqueando
    → Regra prática:
       Site novo (DA < 20): focar em KD < 20
       Site médio (DA 20-50): KD < 40
       Site autoridade (DA 50+): pode atacar KD 40-70

  Intenção de busca (Search Intent) — o mais importante:
    → Informacional: "como fazer X", "o que é Y" → usuário quer aprender → formato: artigo/guia
    → Navegacional: "site da empresa X", "login X" → usuário quer ir a lugar específico → não atacar
    → Transacional: "comprar X", "preço Y", "contratar Z" → usuário quer comprar → formato: LP/produto
    → Comercial: "melhor X", "X vs Y", "reviews de Z" → pesquisa antes de comprar → formato: comparativo/review
    → CRÍTICO: conteúdo que não satisfaz a intenção não rankeia — o Google analisa qual tipo de página está na 1ª página para entender a intenção

  CPC (Custo por Clique):
    → Keywords com CPC alto = valor comercial alto → interessam a anunciantes = concorrentes com budget
    → CPC alto + KD médio = oportunidade de SEO: anunciantes pagam por algo que você pode conseguir orgânico
```

### Topic Clusters — estrutura de autoridade temática

```
O que é:
  → Modelo de arquitetura de conteúdo onde 1 página pilar cobre um tema amplo
    e múltiplas páginas cluster cobrem subtópicos específicos, interligadas
  → Google trata clusters como sinal de autoridade no tópico — não apenas a página individual

Estrutura:
  Página Pilar (Pillar Page):
    → Cobre o tema principal de forma abrangente (2.000-5.000 palavras)
    → Keyword alvo: alta volume, mais genérica ("Marketing Digital")
    → Liga para todas as páginas cluster
    → Exemplo: "Guia Completo de Marketing Digital"

  Páginas Cluster:
    → Cobrem subtópicos com mais profundidade (1.000-2.500 palavras)
    → Keywords alvo: mais específicas, cauda longa ("como criar campanha no Meta Ads")
    → Todas ligam de volta para a página pilar
    → Exemplos: "Meta Ads para Iniciantes", "Como Calcular ROAS", "Google Ads vs Meta Ads"

Benefícios:
  → Conteúdo duplicado evitado — cada cluster cobre 1 ângulo único
  → Link equity circula entre pillar e clusters
  → Google reconhece cobertura completa do tema = autoridade

Planejamento de cluster:
  1. Definir 3-5 temas pilar (alinhados ao negócio)
  2. Para cada tema: listar 10-20 subtópicos (keyword research)
  3. Priorizar subtópicos por: intenção transacional > KD baixo > volume relevante
  4. Publicar 1 pilar + 5-10 clusters antes de atacar tema novo
```

### On-page SEO — otimização dentro da página

```
Tag <title>:
  → 50-60 caracteres (mais: truncado no Google; menos: desperdiça espaço)
  → Keyword principal no início
  → Diferente em cada página
  → Formato recomendado: [Keyword Principal] — [Subtítulo/Benefício] | [Marca]
  → Exemplo: "Como Fazer Anúncios no Meta Ads — Guia Completo | NomeAgência"

Meta description:
  → 150-160 caracteres (não é fator direto de ranking, mas afeta CTR)
  → Incluir keyword (aparece em negrito quando coincide com a busca)
  → Conter proposta de valor + CTA implícito
  → Exemplo: "Aprenda a criar campanhas no Meta Ads do zero: estrutura de conta, segmentação e orçamento. Guia prático atualizado 2026."

H1:
  → 1 único H1 por página
  → Incluir keyword principal
  → Não precisa ser idêntico ao title — pode ser mais longo e descritivo
  → H1 ≠ title: title é para SERP, H1 é para o usuário na página

H2 / H3 (estrutura):
  → H2: seções principais do conteúdo — incluir keywords secundárias e LSI (Latent Semantic Indexing)
  → H3: subsecções dentro de H2
  → Google usa estrutura de headers para entender hierarquia e subtemas

Imagens:
  → Alt text: descrever o que está na imagem com keyword quando natural
  → Nome do arquivo: keyword-separada-por-hifens.jpg (não IMG_1234.jpg)
  → Compressão: WebP ou AVIF para velocidade (impacto em LCP)

Links internos:
  → Link de cada novo artigo para pelo menos 1 página pilar relevante
  → Texto âncora descritivo: "guia de Meta Ads" (não "clique aqui")
  → Links de páginas de maior autoridade para páginas que precisam de boost

Densidade de keyword:
  → Sem fórmula mágica — escrever naturalmente para o leitor
  → Incluir keyword na: introdução (primeiros 100 words), título de algum H2, alt text de imagem, conclusão
  → Evitar keyword stuffing — penalizado pelo Google
```

### E-E-A-T — critério de qualidade do Google

```
Experience (Experiência):
  → Autor tem experiência direta com o assunto? (viveu, testou, usou)
  → Sinal: "Testei esse produto por 6 meses", fotos reais, casos pessoais
  → Como mostrar: autor bio com credenciais, fotos/vídeos de experiência real

Expertise (Especialização):
  → Autor é especialista no tema?
  → Sinal: formação, certificações, anos de experiência no nicho
  → Como mostrar: página "Sobre o autor" detalhada, links para perfis profissionais

Authoritativeness (Autoridade):
  → O site é reconhecido como referência no nicho?
  → Sinal: mencionado em outros sites, backlinks de sites relevantes, citações
  → Como construir: link building (ver seo-offpage), guest posts, presença em mídia

Trustworthiness (Confiabilidade):
  → O site é confiável?
  → Sinal: HTTPS, política de privacidade, termos de uso, informações de contato claras, fontes citadas
  → Para e-commerce: selos de segurança, política de devolução clara

YMYL — Your Money or Your Life:
  → Conteúdo que afeta dinheiro, saúde, segurança ou bem-estar das pessoas
  → Setores: saúde/medicina, finanças/investimentos, jurídico, segurança
  → Para esses temas: E-E-A-T altíssimo exigido — autor deve ser especialista credenciado
  → Regra prática: agência de marketing criando conteúdo de investimentos sem especialista qualificado → não vai ranquear
```

### Ferramentas e processo de keyword research

```
Google Search Console (gratuito):
  → Relatório de Desempenho → ver quais keywords já trazem impressões/cliques
  → Oportunidades: keywords com muitas impressões mas CTR baixo → melhorar title/description
  → Oportunidades: keywords com posição 5-20 → aprofundar conteúdo para chegar ao top 3

Google Keyword Planner (gratuito via Google Ads):
  → Volume mensal por keyword e variações
  → Dados aproximados (intervalos), não exatos
  → Bom para volume, ruim para dificuldade

Ubersuggest (freemium):
  → Volume, dificuldade, ideias de conteúdo
  → Bom custo-benefício para agências pequenas

Ahrefs / SEMrush (pago):
  → Dados precisos de volume, KD, backlinks
  → Site Explorer: ver keywords e backlinks dos concorrentes
  → Content Gap: keywords que concorrentes ranqueiam mas você não

Processo recomendado:
  1. Mapear 5-10 temas principais do negócio
  2. Para cada tema: gerar 50-100 variações de keyword (Keyword Planner ou Ahrefs)
  3. Filtrar por: intenção correta + KD viável para o DA atual
  4. Agrupar por intenção → definir qual página ou artigo atacará cada grupo
  5. Priorizar por: (volume × relevância comercial) / dificuldade
```

---

## Templates prontos

### Template de briefing de conteúdo SEO

```markdown
## Briefing de Conteúdo — [Título do Artigo]

**Keyword principal:** [keyword]
**Volume mensal:** [N] buscas | **KD:** [N]/100
**Intenção de busca:** Informacional / Transacional / Comercial
**URL proposta:** /[slug-da-pagina]

**Keyword pilar vinculada:** [página pilar]

**Keywords secundárias (LSI):**
- [keyword 2]
- [keyword 3]
- [keyword 4]

**Objetivo da página:**
[ ] Gerar lead (CTA para formulário)
[ ] Vender produto (link para LP/produto)
[ ] Construir autoridade (conteúdo educativo puro)

**Estrutura sugerida:**
- H1: [keyword principal + proposta]
- H2: [seção 1]
- H2: [seção 2]
- H2: [seção 3]
- H2: FAQ
- H2: Conclusão + CTA

**Meta title (60 chars):** [...]
**Meta description (160 chars):** [...]

**Referências de concorrentes na 1ª página:**
1. [URL concorrente 1]
2. [URL concorrente 2]

**O que este artigo fará melhor:**
[diferencial do conteúdo]
```

---

## Checklist de qualidade

- [ ] Keyword principal no title tag (início), H1 e introdução
- [ ] Meta description com keyword + proposta de valor + 150-160 chars
- [ ] 1 único H1 por página
- [ ] Alt text em todas as imagens com descrição relevante
- [ ] Pelo menos 1 link interno para a página pilar do cluster
- [ ] Intenção de busca satisfeita — formato e profundidade alinhados com o que a SERP mostra
- [ ] Autor identificado com bio e credenciais (E-E-A-T)
- [ ] Fontes citadas para dados e estatísticas
- [ ] URL amigável com keyword (sem stop words desnecessárias)
- [ ] Submetido para indexação no Search Console após publicação

---

## Armadilhas comuns

**Keyword cannibalization:** duas páginas do mesmo site atacando a mesma keyword. Google não sabe qual ranquear — ambas ficam baixas. Auditar com Screaming Frog e consolidar conteúdo duplicado em 1 página canônica.

**Ignorar a intenção de busca:** escrever artigo informacional para keyword transacional ("comprar X") ou vice-versa. Google vê que o formato não satisfaz a intenção → não rankeia. Sempre analisar o que está na 1ª página antes de definir o formato.

**Otimizar para volume sem avaliar dificuldade:** atacar keyword de 50.000 buscas/mês com KD 90 com site novo. Resultado: posição 100+, zero tráfego. Começar com cauda longa de KD < 20.

**Conteúdo sem atualização:** artigo de 2021 sobre "melhores ferramentas de 2021". Google penaliza conteúdo desatualizado em nichos dinâmicos. Auditar e atualizar conteúdo a cada 12-18 meses (adicionar data de atualização no artigo).

**E-E-A-T ignorado em YMYL:** agência escreve conteúdo financeiro sem citar especialista. Google classifica como baixa qualidade. Incluir revisão de especialista ou parceiro qualificado.

---

## Referências confiáveis

- [Google — Como funciona a Pesquisa Google](https://developers.google.com/search/docs/fundamentals/how-search-works) — verificado 2026-05-01
- [Google — E-E-A-T e Quality Rater Guidelines](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) — verificado 2026-05-01
- [Ahrefs — Keyword Research Guide](https://ahrefs.com/blog/keyword-research/) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [seo-conteudo.changelog.md](seo-conteudo.changelog.md)
