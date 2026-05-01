# Criativos: Landing Pages e CRO

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 05-criativos

---

## Quando usar / Quando não usar

**Usar quando:**
- Criando ou revisando LP para receber tráfego de anúncios — antes de subir qualquer campanha
- Taxa de conversão da LP abaixo do benchmark (< 5% para leads, < 2% para vendas diretas)
- Aumentando budget — antes de escalar, a LP precisa estar otimizada

**Não usar quando:**
- Usando Lead Ads ou Lead Gen Forms (Meta/LinkedIn) — sem LP externa no fluxo
- E-commerce com páginas de produto no Shopify/WooCommerce otimizadas pela plataforma — princípios se aplicam mas a execução é diferente

---

## Pré-requisitos

```
- Objetivo da LP definido: 1 objetivo por página (lead / compra / demo)
- Persona que vai acessar a LP (ver estrategia-personas-comprador)
- Message match: saber qual anúncio vai levar para essa LP (headline do anúncio = headline da LP)
- Ferramentas de análise instaladas: Google Analytics 4 + heatmap (Hotjar ou Microsoft Clarity)
- Ferramenta de criação: Webflow, WordPress (Elementor/Bricks), Unbounce, RD Station LP
```

---

## Padrões e convenções

### Estrutura de LP — sequência de seções

```
ABOVE THE FOLD (o que aparece sem rolar — crítico):
  → H1 (headline): proposta de valor em 1 frase — o que você oferece e para quem
     Fórmula: [Resultado desejado] para [persona] [sem/em/com diferencial]
     Exemplo: "Leads qualificados para PMEs sem desperdiçar budget em anúncios"
  → Subheadline: contexto adicional — como entrega o resultado (1-2 frases)
  → CTA primário: botão grande, acima da dobra, cor contrastante
  → Elemento visual: imagem/vídeo do produto, resultado ou persona usando o produto
  → Prova rápida: "4.9★ de 312 clientes" ou logos de clientes ou "Usado por +2.400 empresas"

Regra do above the fold:
  → 80% dos usuários que não convertem saem sem rolar
  → O above the fold precisa responder: O QUÊ? PARA QUEM? POR QUÊ AGORA?
  → Testar se um novo visitante entende a proposta de valor em 5 segundos (teste dos 5 segundos)

PROBLEMA / DOR (seção 2):
  → Descrever o problema que a persona enfrenta — ela deve se reconhecer
  → Linguagem dela, não do especialista
  → "Você já [situação frustrante]? Você não está sozinho."

SOLUÇÃO (seção 3):
  → Apresentar o produto/serviço como a solução natural
  → Não listar features — listar resultados que as features proporcionam
  → Estrutura: Feature → "o que significa" → Benefício para você
     "Pixel + CAPI configurados por nós" → "Você para de perder conversões por dados incompletos"

BENEFÍCIOS (seção 4):
  → 3-5 benefícios principais — não uma lista de 15 itens
  → Cada benefício: ícone + título em 1 linha + 1-2 frases de explicação
  → Priorizar benefícios emocionais sobre técnicos: "paz de ter o rastreamento correto" > "configuração CAPI"

PROVA SOCIAL (seção 5 — a mais importante para conversão):
  → Depoimentos: foto real + nome completo + cargo/empresa + resultado específico
     "Saímos de R$ 80/lead para R$ 31/lead em 6 semanas" — Mariana S., Gerente de Marketing, Empresa X
  → Logos de clientes (se B2B com marcas reconhecíveis)
  → Número de clientes ou projetos
  → Prêmios, certificações, aparições em mídia
  → Vídeo depoimento: converte 2-3x mais que texto

OFERTA / PROPOSTA COMERCIAL (seção 6):
  → Especificar claramente o que está sendo oferecido
  → Preço (se possível) — preço oculto cria desconfiança e traz leads desqualificados
  → O que está incluído (lista de entregáveis)
  → Garantia (se houver): "Se não gerar X leads em 60 dias, devolvemos o investimento"
  → CTA principal repetido

FAQ (seção 7 — opcional mas reduz objeções):
  → 5-8 perguntas frequentes reais — não inventar perguntas
  → Cada pergunta é uma objeção em forma de dúvida
  → "Funciona para o meu nicho?", "Quanto tempo até ver resultado?", "Tem contrato de fidelidade?"

CTA FINAL (rodapé da LP):
  → Repetir o CTA com ângulo de urgência ou reforço de benefício
  → "Ainda pensando? Fale com a gente primeiro — sem compromisso"
```

### Message match — alinhamento anúncio → LP

```
O que é:
  → O headline e a promessa do anúncio devem aparecer na LP imediatamente
  → Usuário clicou no anúncio por uma razão → LP deve confirmar que chegou no lugar certo

Por que importa:
  → Sem match: usuário chega na LP, não vê o que o anúncio prometeu, sai em 3 segundos
  → Com match: usuário reconhece a continuidade → confiança → fica → converte

Exemplos:
  ❌ Anúncio: "Gere 47 leads por semana com R$ 1.500 de budget"
     LP H1: "Bem-vindo à Agência XYZ — Especialistas em Marketing Digital"
     → Quebra total. Usuário não vê o que prometeu.

  ✅ Anúncio: "Gere 47 leads por semana com R$ 1.500 de budget"
     LP H1: "Gere leads qualificados toda semana com o budget que você tem"
     → Match. Mesma promessa, confirmada.

Para campanhas com segmentos diferentes:
  → Criar LP específica por segmento de anúncio
  → Não usar 1 LP genérica para anúncios com mensagens diferentes
```

### Velocidade — Core Web Vitals

```
Por que velocidade importa:
  → 53% dos usuários mobile abandonam se a página leva > 3 segundos
  → Google usa velocidade para Quality Score (impacta CPC)
  → 1 segundo a mais de carregamento = -7% de conversão (Akamai research)

Core Web Vitals — metas (Google 2024+):
  LCP (Largest Contentful Paint) < 2.5s
    → Quanto tempo para o maior elemento visual da tela aparecer
    → Otimizar: imagens comprimidas (WebP), CDN, preload da imagem hero

  CLS (Cumulative Layout Shift) < 0.1
    → Quanto a página "pula" enquanto carrega (botões que se movem)
    → Otimizar: definir width/height de imagens e iframes no HTML, fonts com font-display: swap

  INP (Interaction to Next Paint) < 200ms
    → Tempo de resposta após clique
    → Otimizar: reduzir JavaScript pesado no main thread

Ferramentas de medição:
  → PageSpeed Insights (pagespeed.web.dev) — teste por URL, recomendações automáticas
  → Google Search Console → Core Web Vitals (dados reais de usuários)
  → GTmetrix — análise detalhada com waterfall de carregamento

Otimizações de impacto rápido:
  → Converter imagens para WebP (reduz 30-50% do tamanho sem perda visual)
  → Lazy loading em imagens abaixo da dobra (loading="lazy")
  → Remover scripts de terceiros desnecessários (chat, pixels não prioritários)
  → Usar CDN (Cloudflare grátis ou CloudFront)
```

### CRO — Conversion Rate Optimization

```
Benchmarks de taxa de conversão:
  Lead (formulário simples — nome + email): 15-35%
  Lead (formulário com qualificação — 4+ campos): 5-15%
  Venda direta (produto < R$ 200): 1-3%
  Venda direta (produto > R$ 500): 0.5-2%
  Demo B2B agendada: 3-8%

Onde investigar quando CR está baixo:

  Heatmaps (Hotjar ou Microsoft Clarity — grátis):
    → Scroll map: até onde os usuários rolam (se não chegam na oferta, ela não existe para eles)
    → Click map: o que as pessoas clicam (se clicam em elementos que não são links, há confusão)
    → Session recordings: gravar sessões reais e ver onde os usuários travam ou saem
    → Form analytics: qual campo do formulário as pessoas abandonam

  Funil de eventos no GA4:
    → Medir: acesso à LP → scroll 50% → clique no CTA → chegou na página de obrigado
    → Onde a maior queda acontece = onde está o problema

O que testar primeiro (maior impacto):
  1. Headline (H1) — maior variância de resultado
  2. Oferta (o que está sendo prometido)
  3. CTA — texto, cor, posição
  4. Prova social — tipo e posição
  5. Formulário — número de campos

Ferramentas de A/B test de LP:
  → Google Optimize (descontinuado — alternativas: VWO, Optimizely, AB Tasty)
  → VWO: plano gratuito para até 1.000 visitantes/mês testados
  → Unbounce: LP builder com A/B test nativo
  → Simples: criar 2 versões de URL e dividir tráfego manualmente entre elas (50/50 no Ads Manager)
```

### Formulário — reduzir fricção

```
Campos por objetivo:
  Lead simples (material, newsletter): Nome + Email → mais volume, menor qualificação
  Lead qualificado (serviço B2B): Nome + Email + Empresa + Cargo + Telefone → menos volume, mais qualidade
  Lead de produto > R$ 1k: adicionar campo de qualificação: "Qual seu maior desafio com X?"

Boas práticas de formulário:
  → Placeholder no campo, não label acima (economiza espaço)
  → Mensagem de privacidade abaixo: "Seus dados são seguros. Sem spam."
  → Botão de submit: não usar "Enviar" — usar o resultado: "Quero meu acesso gratuito"
  → Formulário visível sem rolar (above the fold ou acessível com 1 scroll)
  → Mobile: campos grandes o suficiente para toque (min 44px de altura)

Telefone — coletar ou não:
  → Coletar se o time de vendas vai ligar — sem follow-up ativo, telefone cria fricção sem valor
  → Não coletar se o processo é automatizado — reduz conversão sem necessidade

Multi-step form (formulário em etapas):
  → Dividir formulário longo em 2-3 passos
  → Primeiro passo: pergunta simples (não personal data) → reduz abandono inicial
  → "Qual é seu maior desafio com anúncios?" → [resposta] → "Ótimo! Agora me conta um pouco mais..."
  → Funciona porque o usuário já "começou" — menos provável de abandonar
```

---

## Templates prontos

### Checklist de LP antes de subir tráfego

```markdown
## Validação de Landing Page — [Produto/Campanha]

### Message match
- [ ] Headline da LP contém ou ecoa o headline do anúncio principal
- [ ] A proposta de valor está clara nos primeiros 5 segundos (teste com alguém de fora)

### Above the fold
- [ ] H1 comunica: o quê + para quem + diferencial
- [ ] CTA visível sem rolar (desktop E mobile)
- [ ] Elemento visual relevante (produto, resultado, persona)
- [ ] Prova social rápida presente (número, estrelas, logo)

### Conversão
- [ ] 1 objetivo único na LP (sem múltiplos CTAs divergentes)
- [ ] Formulário com campos mínimos para o objetivo
- [ ] Botão de CTA com linguagem de resultado, não "Enviar"
- [ ] FAQ com objeções principais respondidas

### Técnico
- [ ] PageSpeed Insights: mobile score > 70 (meta: > 85)
- [ ] LCP < 2.5s
- [ ] Pixel do Meta + GA4 instalados e disparando
- [ ] Conversão configurada no GA4 (evento de submit do formulário)
- [ ] Testada em iOS Safari e Android Chrome
- [ ] Descadastro / LGPD: política de privacidade linkada no formulário

### Analytics
- [ ] Google Analytics 4 com evento de conversão mapeado
- [ ] Hotjar ou Clarity instalado para gravar sessões
- [ ] Funil de eventos configurado (acesso → CTA click → obrigado)
```

---

## Checklist de qualidade

- [ ] Above the fold responde: o quê, para quem, por que agora
- [ ] Message match entre anúncio e LP confirmado
- [ ] LCP < 2.5s (testar com PageSpeed Insights antes de lançar)
- [ ] 1 CTA único em toda a LP (sem links de navegação que desviam)
- [ ] Prova social com resultado específico (não genérica)
- [ ] Formulário com mínimo de campos para o objetivo
- [ ] LP testada no mobile (maioria do tráfego de anúncios chega no celular)
- [ ] Pixel de rastreamento e conversão configurados antes de tráfego

---

## Armadilhas comuns

**LP com menu de navegação:** usuário clica em "Sobre nós" ou "Blog" e nunca volta para converter. LP de conversão não tem navegação — apenas o conteúdo que leva ao CTA.

**Headline genérico:** "Bem-vindo à [Empresa] — Soluções em Marketing Digital". Não diz nada para o usuário. Substituir por resultado + público + diferencial.

**Sem message match:** anúncio com promessa específica, LP com mensagem genérica da empresa. Usuário chega e pensa "errei o link". Criar LP por segmento de anúncio.

**Formulário muito longo no início:** 8 campos para quem veio de anúncio frio. Abandonam antes de chegar ao fim. Usar 2-3 campos no topo, coletar o resto após a conversão inicial.

**Testar sem volume:** testar versão A vs B com 50 visitas por semana. Sem significância estatística, a decisão é ruim. Mínimo de 500-1.000 visitantes por variante antes de declarar vencedor.

**LP não rastreada:** lançar campanha sem GA4 nem pixel configurados. Tráfego chegando, conversões acontecendo, mas sem dados. Configurar rastreamento antes do primeiro real gasto.

---

## Referências confiáveis

- [Google — PageSpeed Insights](https://pagespeed.web.dev/) — verificado 2026-05-01
- [Hotjar — LP optimization guide](https://www.hotjar.com/landing-page-optimization/) — verificado 2026-05-01
- [CXL — Landing page best practices](https://cxl.com/blog/landing-page-optimization/) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [criativos-landing-page-cro.changelog.md](criativos-landing-page-cro.changelog.md)
