# Outros Canais: Email Marketing

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 04-outros-canais

---

## Quando usar / Quando não usar

**Usar quando:**
- Nutrição de leads com ciclo de venda longo (> 1 semana) — email mantém presença sem custo por envio
- Retenção de clientes e recompra — canal mais barato e eficiente para base existente
- Carrinho abandonado em e-commerce — sequência de 3 emails recupera 5-15% dos abandonos
- Base de emails própria (opt-in) com pelo menos 500 contatos para ter dados significativos

**Não usar quando:**
- Lista comprada — viola LGPD, gera spam, derruba reputação de domínio permanentemente
- Base sem segmentação e sem histórico de abertura — enviar para lista fria gera hard bounces e bloqueia o domínio
- Produto de compra por impulso com ciclo imediato — email não é o canal certo para urgência de minutos

---

## Pré-requisitos

```
- Domínio próprio configurado com SPF, DKIM e DMARC (sem isso, emails vão para spam)
- Ferramenta de email marketing contratada (ver seção de ferramentas)
- Lista de emails coletada com consentimento (opt-in) — LGPD obrigatório
- Formulário de captação integrado ao site ou landing page
- Definição das automações antes de começar a enviar broadcasts manuais
```

---

## Padrões e convenções

### Deliverability — chegar na caixa de entrada, não no spam

```
SPF (Sender Policy Framework):
  → Registro DNS que autoriza quais servidores podem enviar email pelo seu domínio
  → Como adicionar: no painel DNS do domínio, criar registro TXT:
     v=spf1 include:_spf.google.com include:sendgrid.net ~all
     (substituir pelos servidores da sua ferramenta)

DKIM (DomainKeys Identified Mail):
  → Assinatura criptográfica nos emails — prova que foi enviado pelo domínio legítimo
  → Gerar na ferramenta de email → copiar registro CNAME → adicionar no DNS do domínio

DMARC (Domain-based Message Authentication):
  → Política que instrui o que fazer com emails que falham SPF/DKIM
  → Registro TXT mínimo:
     v=DMARC1; p=none; rua=mailto:dmarc@seudominio.com
  → p=none (monitorar), p=quarantine (spam), p=reject (bloquear) — iniciar com none

Aquecimento de domínio novo:
  → Domínio novo tem reputação zero — começar com volume baixo
  → Semana 1: 100 emails/dia para lista mais engajada (quem abriu nos últimos 30d)
  → Semana 2: 500/dia
  → Semana 3: 2.000/dia
  → Semana 4+: volume total desejado
  → Nunca pular etapas — provedores (Gmail, Outlook) marcam domínio novo com alto volume como spam

Métricas de reputação:
  Bounce rate: < 2% hard bounce (email inválido) → acima disso, bloquear domínio
  Spam rate: < 0.1% (Google Postmaster Tool) → acima disso, entrega cai drasticamente
  Taxa de abertura: benchmark varia por setor — 20-30% é bom para B2B, 15-25% B2C
  Limpar lista: a cada 6 meses remover quem não abriu em 90 dias (reativação antes de remover)
```

### Automações essenciais — configurar antes de qualquer broadcast

```
1. WELCOME SEQUENCE (boas-vindas — ativar novo lead):
   Email 1 (imediato — 0-5 min após cadastro):
     → Confirmar inscrição, entregar o prometido (lead magnet, desconto, acesso)
     → Tom: caloroso, pessoal, expectativas do que virá
   
   Email 2 (dia 2):
     → Apresentar a empresa/marca — história, por que existe, quem ajuda
     → CTA: ver o conteúdo mais popular / case de sucesso
   
   Email 3 (dia 4):
     → Conteúdo de valor — resolver a dor principal da persona
     → Sem pitch de venda ainda — construir confiança
   
   Email 4 (dia 7):
     → Prova social — depoimento, número de clientes, resultado obtido
     → CTA suave para o produto/serviço

2. NURTURING SEQUENCE (educação e aquecimento — MOFU):
   → Série de 4-8 emails enviados 1-2x/semana
   → Conteúdo progressivo: problema → causa → solução → produto
   → Gatilho: quem não converteu após a welcome sequence
   → CTA cresce gradualmente: "Baixe o guia" → "Veja um caso" → "Fale com especialista"

3. CARRINHO ABANDONADO (e-commerce — BOFU crítico):
   Email 1 (1 hora após abandono):
     → Assunto: "Você esqueceu algo?" ou "Seu [produto] está te esperando"
     → Mostrar o produto abandonado + imagem + preço
     → CTA: "Continuar minha compra"
   
   Email 2 (24 horas após abandono):
     → Superar objeção: "Tem dúvidas? Estamos aqui" ou FAQ sobre o produto
     → Oferecer suporte / chat
   
   Email 3 (72 horas após abandono):
     → Urgência/escassez: "Últimas unidades" ou cupom de desconto por tempo limitado
     → Não usar desconto logo no email 1 — treina o cliente a sempre abandonar para ganhar desconto

4. REENGAJAMENTO (lista fria — 90+ dias sem abrir):
   Email 1: "Ainda está por aqui?" — tom pessoal, perguntar se ainda tem interesse
   Email 2 (7 dias depois se não abriu): assunto provocativo, oferta especial
   Email 3 (7 dias depois se não abriu): "Vou remover seu email da lista"
     → Quem não abre esse terceiro: remover da lista ativa (melhor para deliverability)
```

### Assunto do email — o fator mais importante para abertura

```
Boas práticas:
  → Tamanho ideal: 6-10 palavras / 30-50 caracteres (visível no mobile)
  → Personalização: [Nome], você... → +26% de abertura
  → Número específico: "3 erros que...", "R$ 12.450 economizados em..."
  → Curiosidade: "Nunca faça isso antes de anunciar"
  → Urgência real (não falsa): "Último dia para garantir o preço"
  → Emojis com moderação: 1 emoji relevante pode aumentar abertura, 3+ parece spam

O que evitar:
  → Palavras que ativam filtros de spam: GRÁTIS, CLIQUE AQUI, OFERTA, 100% GARANTIDO
  → Todo em maiúsculo: SEU DESCONTO EXCLUSIVO ← parece spam
  → Assuntos enganosos: "Re: nossa conversa" quando não houve conversa
  → Assuntos genéricos: "Newsletter de maio" (zero razão para abrir)

Pré-header (preview text):
  → Texto que aparece ao lado/abaixo do assunto no mobile
  → Configurar sempre — sem pré-header, cliente de email puxa o início do email (geralmente feio)
  → Complementar o assunto, não repetir: assunto "3 erros de anúncio" + pré-header "o terceiro é o que mais faz perder dinheiro"

Teste A/B de assunto:
  → Ferramenta nativa de quase todas as plataformas
  → Enviar versão A para 20%, versão B para 20%, aguardar 4h, enviar vencedora para 60%
```

### Segmentação de lista — enviar para quem é relevante

```
Por comportamento:
  → Abriu os últimos 5 emails vs não abriu em 90 dias → listas completamente diferentes
  → Clicou em link sobre [produto X] → interessado no tema → segmentar com conteúdo relacionado
  → Comprou produto A → não enviar oferta do produto A → enviar cross-sell de produto B

Por estágio do funil:
  → Lead novo (<7 dias): welcome sequence
  → Lead quente (abriu 3+ emails da semana): oferta direta, CTA de conversão
  → Lead frio (90+ dias sem abrir): campanha de reengajamento antes de remover

Por produto de interesse:
  → Quem baixou material sobre X vs quem baixou sobre Y → conteúdo diferente
  → Tags automáticas no clique de links para segmentar por interesse

Ferramentas de email marketing — quando usar qual:

  Mailchimp:
    → Plano grátis até 500 contatos
    → Bom para: iniciantes, listas pequenas, newsletters
    → Limitação: automações básicas no plano gratuito

  ActiveCampaign:
    → Melhor automação do mercado (CRM + email integrado)
    → Bom para: B2B com ciclo longo, lead scoring, sequências complexas
    → Preço: a partir de USD 29/mês

  Klaviyo:
    → Especializado em e-commerce (Shopify, WooCommerce nativo)
    → Bom para: carrinho abandonado, browsing abandonment, segmentação por compra
    → Preço: freemium até 250 contatos, depois por volume

  RD Station Marketing:
    → Principal plataforma brasileira — em português
    → Bom para: mercado brasileiro, suporte local, integração com RD CRM
    → Preço: a partir de R$ 399/mês

  Brevo (ex-Sendinblue):
    → Bom custo-benefício — cobra por envio, não por contato
    → Bom para: listas grandes com baixa frequência
```

---

## Templates prontos

### Estrutura de email de nutrição

```markdown
## Email — [Assunto] — [Data]

**Segmento:** [quem recebe]
**Posição na sequência:** Email [N] de [total]
**Objetivo:** [educar / converter / reativar]

---

**Assunto:** [assunto — máx 50 chars]
**Pré-header:** [complemento do assunto — máx 90 chars]

---

Oi, [Nome],

[Parágrafo de abertura — conectar com a dor ou situação]

[Conteúdo principal — história, dado, insight]

[Transição para a solução/produto — não forçar, fluir naturalmente]

[CTA único e claro]

[Nome] | [Cargo]
[Empresa]

[Link de descadastro — obrigatório por lei]
```

---

## Checklist de qualidade

- [ ] SPF, DKIM e DMARC configurados antes do primeiro envio
- [ ] Domínio aquecido se for novo (iniciar com volume baixo)
- [ ] Welcome sequence criada antes de começar a captar leads
- [ ] Campos de personalização testados (verificar se [Nome] está sendo substituído corretamente)
- [ ] Link de descadastro presente em todos os emails (LGPD + CAN-SPAM)
- [ ] Pré-header configurado em todos os emails
- [ ] Teste de renderização em mobile antes de disparar (maioria abre no celular)
- [ ] Bounce rate monitorado após cada disparo (> 2% → investigar qualidade da lista)
- [ ] Segmentação: não enviar o mesmo email para toda a lista sem considerar estágio/interesse

---

## Armadilhas comuns

**Lista comprada:** comprar lista de emails de terceiros viola LGPD, gera bounce rate > 20% (emails inválidos ou de domínios mortos), destrói a reputação do domínio permanentemente. Sem recuperação fácil.

**Sem SPF/DKIM:** emails indo direto para spam por falta de autenticação. Taxa de abertura de 2% não é porque o assunto é ruim — é porque ninguém recebeu na caixa de entrada.

**Sem segmentação:** enviar o mesmo email promocional para lead de 1 dia e cliente há 2 anos. Lead novo não tem contexto, cliente sente que é tratado como desconhecido. Segmentar sempre.

**Frequência exagerada:** 5 emails na mesma semana para toda a lista. Taxa de descadastro sobe, spam complaints aparecem, reputação cai. Máx 2-3 emails por semana para base geral.

**Não limpar a lista:** manter 10.000 emails com 8.000 sem abrir em 6 meses. Taxa de abertura aparente de 20% real (20% de 10k) mas o provedor de email vê 80% de inatividade e começa a filtrar. Limpar lista a cada 6 meses.

---

## Referências confiáveis

- [Google Postmaster Tools](https://postmaster.google.com/) — monitorar reputação de domínio no Gmail, verificado 2026-05-01
- [ActiveCampaign — Email deliverability](https://www.activecampaign.com/blog/email-deliverability) — verificado 2026-05-01
- [Mailchimp — Email marketing benchmarks](https://mailchimp.com/resources/email-marketing-benchmarks/) — benchmarks por setor, verificado 2026-05-01

---

## Versão e histórico
→ Ver [outros-email-marketing.changelog.md](outros-email-marketing.changelog.md)
