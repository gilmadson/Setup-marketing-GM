# Google Ads: Search (Rede de Pesquisa)

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 03-google-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- Público tem intenção de busca clara — pesquisa ativamente uma solução ("contratar agência de marketing", "comprar notebook gamer")
- BOFU prioritário — capturar demanda existente com menor desperdício de budget
- Concorrentes aparecem nas buscas do seu produto — estar presente é proteção de mercado

**Não usar quando:**
- Produto sem demanda de busca (novo mercado, produto sem nome) — sem busca, sem tráfego
- Budget < R$ 30/dia — CPC alto de palavras competitivas consome sem volume suficiente para aprender
- Campanha de awareness puro — para alcance e reconhecimento, usar Display ou YouTube

---

## Pré-requisitos

```
- Google Ads account criada e vinculada ao Google Analytics 4
- Conversões configuradas no Google Ads (importadas do GA4 ou tag direta)
- Keyword research realizado (Google Keyword Planner, SEMrush, Ahrefs)
- Landing page relevante para as keywords — sem LP otimizada, Quality Score cai e CPC sobe
- Budget mínimo: R$ 50-80/dia por campanha (depende do CPC médio das palavras)
```

---

## Padrões e convenções

### Tipos de correspondência — match types

```
[Exact Match] — palavra-chave exata:
  Sintaxe: [comprar notebook]
  Dispara: apenas "comprar notebook" e variantes muito próximas (erros de ortografia, plurais)
  Não dispara: "notebook para comprar", "onde comprar notebook barato"
  Usar: palavras de alta intenção onde cada clique conta — menor volume, maior qualidade

"Phrase Match" — correspondência de frase:
  Sintaxe: "notebook gamer"
  Dispara: qualquer busca que contenha o sentido de "notebook gamer" em ordem
  Inclui: "notebook gamer barato", "melhor notebook gamer 2026", "notebook gamer i7"
  Não inclui: "gamer notebook" (ordem invertida com sentido diferente)
  Usar: equilíbrio entre volume e relevância — padrão para a maioria das campanhas

Broad Match — correspondência ampla:
  Sintaxe: notebook (sem colchetes ou aspas)
  Dispara: qualquer busca semanticamente relacionada — "computador portátil", "laptop para trabalho"
  Usar: apenas com Smart Bidding (Target CPA/ROAS) e quando tem histórico sólido de conversões
  Nunca usar: em campanhas novas sem Smart Bidding — gera tráfego irrelevante e desperdiça budget

Hierarquia de controle:
  [Exact] → mais controle, menos volume
  "Phrase" → controle médio, volume médio
  Broad → menos controle, mais volume (perigoso sem Smart Bidding)
```

### Negative Keywords — lista de exclusão

```
Por que são críticas:
  → Cada busca irrelevante que dispara o anúncio = dinheiro desperdiçado
  → Campanha de "agência de marketing" sem negativar "emprego" e "estágio" vai aparecer para quem busca vaga

Onde aplicar:
  Nível de conta: negativos universais (nunca relevantes para nenhuma campanha)
  Nível de campanha: negativos específicos do produto/serviço
  Nível de grupo de anúncios: negativos que são relevantes para outro grupo mas não este

Listas de negativos obrigatórias (iniciar com estas):

  Intenção errada — quem não quer comprar:
    grátis, free, gratuito, de graça
    como fazer, tutorial, passo a passo, aprenda
    o que é, definição, significado, conceito
    emprego, vaga, estágio, trainee, salário
    curso, faculdade, universidade, formação

  Geolocalização incorreta (se campanha local):
    [países/estados/cidades] que não atende

  Produto diferente:
    [competidor com produto diferente do seu]
    [palavras de outros segmentos que rimam com o seu produto]

Processo de revisão de Search Terms:
  → Semanal (primeiros 30 dias): acessar Palavras-chave → Search Terms → Adicionar negativos
  → Quinzenal (campanha madura): varrer search terms e negativar o que não converteu
  → Nunca pausar essa revisão — Broad e Phrase sempre geram novos termos irrelevantes
```

### Quality Score — componentes e como melhorar

```
O que é:
  → Score de 1-10 que o Google atribui a cada palavra-chave
  → Impacta diretamente o Ad Rank e o CPC real (maior QS = CPC menor)

3 componentes (peso aproximado):
  1. Ad Relevance (relevância do anúncio para a keyword) — 30%
     → Keyword no headline do anúncio → Ad Relevance sobe
  2. Landing Page Experience (relevância da LP) — 40%
     → Keyword na LP, carregamento rápido (<3s), conteúdo relevante
  3. Expected CTR (histórico de cliques esperado) — 30%
     → Histórico da conta e do anúncio influenciam

Como melhorar:
  → Grupos de anúncios temáticos: 1 tema por grupo, 5-15 keywords max
  → Ad copy: headline 1 contém a keyword principal
  → LP match: landing page fala especificamente do que a keyword promete
  → CTR: extensões preenchem mais espaço → mais chances de clique

Referência de QS:
  1-3: péssimo — pagar muito mais que o concorrente pelo mesmo Ad Rank
  4-6: médio — melhorar copy e LP
  7-10: bom — CPC otimizado
```

### Ad Rank e Smart Bidding

```
Ad Rank (determina posição e CPC real):
  Ad Rank = QS × Lance × Fator de extensões + Contexto (hora, dispositivo, local)
  → Alto QS compensa lance menor — não é só sobre quem paga mais

Estratégias de lance (Smart Bidding):

  Maximizar Conversões (sem meta):
    → Google gasta o budget inteiro buscando máximo de conversões
    → Usar: campanha nova sem histórico, quer dados rápidos
    → Risco: CPA pode ser alto no início

  Meta de CPA (Target CPA):
    → Google tenta manter CPA próximo do valor definido
    → Usar: quando tem histórico de pelo menos 30 conversões/mês
    → Configurar: 10-20% acima do CPA médio atual para não travar entrega

  Meta de ROAS (Target ROAS):
    → Google otimiza para retorno em receita
    → Usar: e-commerce com valores de conversão configurados
    → Requer: histórico de pelo menos 30 conversões com valor no último mês

  Maximizar Cliques:
    → Não recomendado para campanha de conversão — otimiza clique, não resultado

  CPC Manual / Enhanced CPC:
    → Controle manual do lance por keyword
    → Usar: contas muito novas sem dados para Smart Bidding aprender
    → Migrar para Smart Bidding após 30+ conversões
```

### RSA — Responsive Search Ads

```
O que é:
  → Anúncio que combina automaticamente headlines e descriptions para maximizar CTR
  → Algoritmo testa combinações e aprende qual funciona melhor

Limites:
  → Até 15 headlines (cada um máx 30 chars)
  → Até 4 descriptions (cada um máx 90 chars)
  → Google exibe: 2-3 headlines + 1-2 descriptions por vez

Regras de criação:
  → Headlines 1-3: incluir keyword principal (Ad Relevance)
  → Headlines 4-6: benefícios principais ("Resultados em 30 dias", "Atendimento 24h")
  → Headlines 7-10: diferenciais e CTAs ("Peça orçamento grátis", "Frete grátis > R$ 200")
  → Headlines 11-15: provas sociais, números ("+ de 500 clientes", "Avaliação 4.9★")
  → Descriptions: usar as 4 vagas com mensagens diferentes, não repetir

Pinning (fixar posição):
  → Pin = forçar headline/description a aparecer sempre em determinada posição
  → Usar com moderação — pinning reduz variedade de combinações testadas
  → Quando usar: aviso legal obrigatório, mensagem de urgência com prazo específico

Ad Strength:
  → Google avalia de "Fraco" a "Excelente"
  → Meta: "Bom" ou "Excelente" — headlines variados, keywords incluídas, sem repetição
```

### Extensões de anúncio — obrigatórias

```
Sitelinks (links adicionais abaixo do anúncio):
  → Adicionar 4-6 sitelinks por campanha
  → Exemplos: "Planos e Preços", "Sobre nós", "Cases de Sucesso", "Fale Conosco"
  → Aumentam área do anúncio → maior CTR sem custo adicional por extensão

Callouts (frases de destaque):
  → Textos curtos sem link: "Sem contrato", "Suporte incluso", "Resultado garantido"
  → Adicionar 4-6 por campanha

Snippets estruturados:
  → Categorizar serviços: "Serviços: SEO, Google Ads, Meta Ads, CRO"
  → Obrigatório para contas de serviços

Extensão de chamada (Call):
  → Número de telefone — usuário mobile pode ligar com 1 toque
  → Para negócios que recebem leads por telefone

Extensão de local (Location):
  → Mostrar endereço — fundamental para negócios locais
  → Vincular ao Google Meu Negócio

Extensão de preço:
  → Exibir tabela de preços/planos diretamente no anúncio
  → Filtra leads — quem clica já sabe o preço

Regra: adicionar TODAS as extensões relevantes — mais espaço na SERP = mais CTR
```

### Estrutura de campanhas recomendada

```
Campanha 1 — Brand:
  Objetivo: capturar quem já busca a marca
  Keywords: [nome da empresa], [nome do produto]
  Lance: baixo (concorrência mínima, CPC baixo)
  Por que criar: concorrentes podem licitar pelo seu nome — proteger sua marca

Campanha 2 — Concorrentes:
  Objetivo: aparecer quando buscam o concorrente
  Keywords: "concorrente A", "concorrente B preço", "alternativa ao concorrente A"
  Lance: médio-alto
  Copy: "Cansou do [concorrente]? Conheça [seu produto]"

Campanha 3 — Produto/Serviço (BOFU):
  Objetivo: capturar intenção de compra direta
  Keywords: "comprar [produto]", "contratar [serviço]", "[produto] preço"
  Lance: alto (maior valor por conversão)

Campanha 4 — Genéricas/Educacionais (MOFU):
  Objetivo: capturar quem está pesquisando mas ainda não decidiu
  Keywords: "como escolher [produto]", "melhor [serviço]", "[problema que o produto resolve]"
  Lance: médio (conversão mais longa)

Campanha 5 — RLSA (Remarketing para Search):
  Objetivo: lance ajustado para quem já visitou o site e pesquisa novamente
  Configuração: adicionar Audience de "Visitantes do site" e aumentar lance em +30-50%
  Por que: quem já te conhece converte mais — vale pagar mais por esse clique
```

---

## Templates prontos

### Estrutura de grupo de anúncios temático

```markdown
## Grupo de Anúncios — [Tema]

**Campanha:** [nome]
**Tema:** [ex: "agência de tráfego pago"]

### Keywords
- [keyword exata] → [exact match]
- "[keyword principal]" → [phrase match]
- "[keyword variação 1]"
- "[keyword variação 2]"

### Negative keywords deste grupo
- [keyword que pertence a outro grupo]

### RSA
Headline 1 (pin posição 1 — keyword): [keyword principal]
Headline 2: [benefício 1]
Headline 3: [benefício 2]
Headline 4: [diferencial]
Headline 5: [CTA]
...

Description 1: [proposta de valor — 90 chars]
Description 2: [prova social ou detalhe — 90 chars]

### KPIs deste grupo
- CPC médio esperado: R$ [valor]
- CTR esperado: [%]
- CPA meta: R$ [valor]
```

---

## Checklist de qualidade

- [ ] Conversões configuradas no Google Ads antes de lançar
- [ ] 1 tema por grupo de anúncios (5-15 keywords)
- [ ] Negative keywords adicionadas antes de publicar (pelo menos 20)
- [ ] Match type correto para o objetivo (Exact/Phrase para início, Broad só com Smart Bidding)
- [ ] RSA com Ad Strength "Bom" ou "Excelente"
- [ ] Todas as extensões relevantes configuradas (mín: Sitelinks + Callouts + Snippets)
- [ ] Smart Bidding configurado quando há histórico (30+ conversões/mês)
- [ ] Revisão de Search Terms agendada semanalmente

---

## Armadilhas comuns

**Broad Match sem Smart Bidding:** palavra-chave ampla sem Target CPA ou Target ROAS consome budget em buscas irrelevantes. Sempre associar Broad a Smart Bidding com histórico de conversões.

**Grupos de anúncios genéricos demais:** 50 keywords em 1 grupo, anúncio genérico que não menciona nenhuma delas. QS cai, CPC sobe. Máx 15 keywords por grupo, 1 tema, headline com a keyword.

**Não instalar conversões:** campanha rodando sem rastrear conversões. Smart Bidding não funciona, não sabe o que otimizar. Configurar conversões antes do primeiro R$ 1 gasto.

**Ignorar Search Terms:** Phrase e Broad sempre geram termos novos — alguns irrelevantes. Revisar Search Terms semanalmente nos primeiros 30 dias e negativar o que não converte.

**Lance manual em campanha madura:** Google tem mais dados para otimizar do que qualquer gestor humano. Após 30 conversões, migrar para Smart Bidding.

---

## Referências confiáveis

- [Google — Tipos de correspondência](https://support.google.com/google-ads/answer/2497836) — verificado 2026-05-01
- [Google — Responsive Search Ads](https://support.google.com/google-ads/answer/7684791) — verificado 2026-05-01
- [Google — Smart Bidding](https://support.google.com/google-ads/answer/7065882) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [google-search.changelog.md](google-search.changelog.md)
