# Outros Canais: LinkedIn Ads

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 04-outros-canais

---

## Quando usar / Quando não usar

**Usar quando:**
- B2B com público segmentado por cargo, setor ou empresa — segmentação profissional sem equivalente em outra plataforma
- Ticket de venda > R$ 5.000/mês ou produto de decisão corporativa — CPL alto do LinkedIn é justificado pelo valor do lead
- Account-Based Marketing (ABM) — segmentar empresas específicas da lista de prospects

**Não usar quando:**
- Produto B2C ou ticket baixo — CPL de R$ 150-500 não fecha a conta para a maioria dos produtos de consumo
- Budget < R$ 150/dia — sem volume mínimo, o algoritmo não aprende e os dados são insuficientes
- Público-alvo está em cargos de entrada (CLT junior, estudantes) — maior concentração em Meta/TikTok com custo muito menor

---

## Pré-requisitos

```
- Página da empresa no LinkedIn (obrigatório — anúncios saem da Página, não do perfil pessoal)
- LinkedIn Campaign Manager criado e vinculado à Página
- LinkedIn Insight Tag instalada no site (pixel equivalente)
- Budget mínimo: R$ 150-200/dia para ter volume suficiente de dados
- Para Lead Gen Forms: formulário criado dentro do Campaign Manager
- Para ABM: lista de domínios ou empresas no LinkedIn para segmentação
```

---

## Padrões e convenções

### Hierarquia de conta — Campaign Group → Campaign → Ad

```
CAMPAIGN GROUP:
  → Organização lógica por produto, mercado ou objetivo
  → Exemplo: "Produto SaaS — Brasil", "Serviço Consultoria — Enterprise"

CAMPAIGN:
  → Define: Objetivo, Público, Budget, Lance
  → 1 objetivo por campanha

AD:
  → Criativo (imagem/vídeo/texto) vinculado à campanha

Objetivos disponíveis:
  Brand Awareness → CPM, impressões
  Website Visits → CPC, tráfego
  Engagement → interações com o conteúdo
  Video Views → CPV
  Lead Generation → Lead Gen Forms (formulário nativo)
  Website Conversions → via Insight Tag
  Job Applicants → para recrutamento (não marketing)
```

### Formatos de anúncio

```
SPONSORED CONTENT (mais comum):
  → Aparece no feed do LinkedIn como post patrocinado
  → Formatos dentro de Sponsored Content:
     Single Image Ad: imagem + texto + link
     Video Ad: vídeo + texto
     Carousel Ad: 2-10 cards
     Document Ad: PDF/apresentação para download (ótimo para lead magnet B2B)
     Event Ad: promover evento LinkedIn

  Specs Single Image:
    → Imagem: mín 552×289px, recomendado 1200×627px (1.91:1) ou 1200×1200px (1:1)
    → Headline: máx 200 chars (visível: ~70 chars antes do "ver mais")
    → Texto intro: máx 600 chars (visível: ~150 chars antes do "ver mais")
    → CTA: Learn More, Download, Sign Up, Register, Apply, Request Demo

LEAD GEN FORMS (LinkedIn nativo):
  → Formulário que abre dentro do LinkedIn com dados pré-preenchidos do perfil
  → Vantagem: conversão muito maior que redirecionar para site externo (dados profissionais já estão lá)
  → Campos disponíveis pré-preenchidos: nome, email (profissional), cargo, empresa, telefone, localização
  → Campos customizados: perguntas específicas para qualificação (até 3 customizadas)
  → Usar com: Sponsored Content ou Message Ads
  → CPL geralmente menor que levar para LP externa — elimina fricção

MESSAGE ADS (InMail):
  → Mensagem direta na caixa de entrada do LinkedIn
  → Aparece apenas quando o destinatário está online (não fica na caixa como email normal)
  → Cobrança: por envio (CPS — cost per send), não por clique
  → Limite: usuário recebe no máx 1 Message Ad a cada 30 dias
  → Usar para: ABM (mensagem personalizada para decision-makers), demos, eventos exclusivos
  → Tom: mais pessoal, menos "ad" — parece mensagem de networking

CONVERSATION ADS:
  → Evolução do Message Ad — múltiplos botões de resposta (CTA tree)
  → Usuário escolhe o caminho: "Quero saber mais" → "Agendar demo" / "Ver cases"
  → Bom para: qualificação de lead por auto-seleção

TEXT ADS:
  → Banner de texto + pequena imagem na sidebar e topo do LinkedIn (desktop only)
  → CPM/CPC muito baixo, mas CTR muito baixo também (< 0.1%)
  → Usar apenas para retargeting de marca ou complementar campanha principal

DYNAMIC ADS:
  → Personalizado com foto de perfil do usuário (efeito de destaque visual)
  → Formatos: Follower Ad (ganhar seguidores da Página), Spotlight Ad (CTA para site), Content Ad
  → CTR geralmente maior que Text Ads por ser personalizado
```

### Segmentação B2B — o diferencial do LinkedIn

```
Atributos de segmentação disponíveis:

  Empresa:
    → Company Name: segmentar por empresas específicas (ABM)
    → Company Size: 1-10, 11-50, 51-200, 201-500, 501-1k, 1k-5k, 5k-10k, 10k+
    → Company Industry: setor da empresa (ex: Tecnologia, Financeiro, Saúde)
    → Company Revenue: faturamento estimado da empresa
    → Company Growth Rate: empresas em crescimento acelerado

  Cargo e função:
    → Job Title: cargo exato (ex: "Gerente de Marketing", "CFO", "Head of Sales")
    → Job Function: área (ex: Marketing, Finanças, TI, Operações)
    → Seniority: Estagiário / Júnior / Pleno / Sênior / Gerência / Diretoria / C-Level / Dono
    → Years of Experience: anos de experiência total

  Educação:
    → Grau de formação
    → Área de estudo
    → Escola/Universidade

  Interesses e Skills:
    → Member Skills: habilidades no perfil (ex: "Gestão de Projetos", "Salesforce", "Python")
    → Member Interests: tópicos que seguem e engajam

  Grupos do LinkedIn:
    → Membros de grupos específicos (comunidades profissionais do nicho)

Combinações recomendadas por objetivo:
  SaaS B2B (PME):
    → Company Size: 11-200 + Job Function: TI/Operações + Seniority: Gerência+
  
  Consultoria Enterprise:
    → Company Size: 500+ + Job Title: [C-Level específico] + Industry: [setor]
  
  ABM (Account-Based):
    → Company Name: [lista de empresas alvo] + Seniority: Diretoria+

Tamanho de público:
  → Mínimo para rodar: 50.000 membros
  → Ideal para testes: 50k-500k
  → Para escala: 500k+
  → Público muito pequeno (<50k): entrega muito limitada, CPM explode
```

### CPL e benchmarks — LinkedIn B2B Brasil

```
CPL esperado por produto (referência 2025):
  SaaS B2B (ticket R$ 500-2k/mês) → R$ 150-300/lead
  Consultoria/Serviços Enterprise → R$ 200-500/lead
  Evento/Webinar (lead de baixo comprometimento) → R$ 50-120/lead
  Financeiro/Investimentos B2B → R$ 200-400/lead

Por que o CPL é tão alto:
  → CPM do LinkedIn é o mais caro entre as plataformas sociais
  → CTR médio < 0.5% (vs 1-3% no Meta)
  → Compensa quando o valor vitalício do cliente (LTV) é alto

Como calcular se vale a pena:
  CPL aceito = LTV × Taxa de fechamento × Margem
  Exemplo: LTV R$ 50k, fechamento 10%, margem 40%
    CPL máximo = R$ 50.000 × 10% × 40% = R$ 2.000
    → Um lead de R$ 400 seria excelente neste caso

Estratégia de custo:
  → Lead Gen Forms reduz CPL vs LP externa em 30-50%
  → Message Ads para ABM podem ter CPS de R$ 5-15 mas conversão maior para contas específicas
  → Complementar LinkedIn com retargeting em Meta (mais barato) para os leads que vieram do LinkedIn
```

### LinkedIn Insight Tag — rastreamento

```
O que é:
  → Pixel de rastreamento do LinkedIn — instalar em todas as páginas do site
  → Permite: retargeting de visitantes, conversões, demographic insights

Como instalar:
  → Campaign Manager → Assets → Insight Tag → copiar e colar antes de </body>
  → Ou via Google Tag Manager: tag de HTML personalizado com o código

Públicos de retargeting:
  → Visitantes do site (últimos 30/90/180 dias)
  → Visitantes de página específica (ex: /demo, /precos)
  → Quem preencheu Lead Gen Form
  → Quem assistiu % do vídeo

Matched Audiences (equivalente ao Customer Match):
  → Upload de lista de e-mails para segmentar no LinkedIn
  → Correspondência menor que Meta (~30%) — e-mail pessoal vs e-mail profissional no LinkedIn
  → Melhor usar lista de domínios de empresa (ABM) para maior correspondência
```

---

## Templates prontos

### Brief de campanha LinkedIn B2B

```markdown
## Campanha LinkedIn Ads — [Produto/Serviço]

**Objetivo:** [Lead Generation / Website Conversions / Awareness]
**Budget:** R$ [valor]/dia
**Duração:** [X semanas/meses]

### Segmentação
- Company Size: [tamanho]
- Job Function: [área]
- Seniority: [nível]
- Industry: [setor]
Tamanho estimado do público: [X mil membros]

### Formato de anúncio
- Principal: [Sponsored Content + Lead Gen Form]
- CPL meta: R$ [valor]

### Mensagem central
Para [cargo/função] em [tipo de empresa] que enfrenta [dor],
o [Produto] oferece [benefício] diferente de [alternativa],
porque [diferencial único].

### Lead Gen Form
- Campos coletados: nome, email profissional, cargo, empresa, telefone
- Pergunta de qualificação: [ex: "Qual é o maior desafio em X?"]
- Política de privacidade: [URL]

### KPIs
- CPL meta: R$ [valor]
- Volume de leads/mês: [X leads]
- Taxa de MQL esperada: [%]
```

---

## Checklist de qualidade

- [ ] Página da empresa no LinkedIn com pelo menos logo e descrição completos
- [ ] LinkedIn Insight Tag instalada e verificada
- [ ] Público verificado: > 50.000 membros antes de lançar
- [ ] Lead Gen Form com campos de qualificação (não só nome e email)
- [ ] Budget mínimo R$ 150/dia (abaixo não tem volume para aprender)
- [ ] CPL máximo calculado com base no LTV e taxa de fechamento da equipe comercial
- [ ] Retargeting configurado para visitantes do site (/demo, /precos)
- [ ] Processo de follow-up de lead definido ANTES de lançar (LinkedIn gera leads quentes — resposta em < 2h)

---

## Armadilhas comuns

**Budget abaixo do mínimo:** R$ 50/dia no LinkedIn gera CPM de R$ 80-120 → 0,5 impressões/dia. Sem volume, sem dados, sem aprendizado. Mínimo real: R$ 150/dia.

**Segmentação muito estreita:** Cargo "VP de Marketing" + Company Size "1000+" + Industry "Tecnologia" = 3.000 membros no Brasil. Entrega impossível. Flexibilizar 1-2 dimensões.

**Não usar Lead Gen Forms:** levar para LP externa sem formulário nativo. Taxa de conversão cai 30-50%. LinkedIn sabe que os dados profissionais do usuário já estão ali — LGF aproveita isso.

**Nenhum follow-up ativo:** lead preencheu formulário e ficou esperando email automático por 24h. LinkedIn gera leads quentes — resposta em até 2h dobra taxa de fechamento. Integrar LGF ao CRM ou notificação instantânea.

**Esperar resultado imediato:** LinkedIn tem ciclo de decisão mais longo. Campanha precisa de 4-8 semanas para ciclo completo. Não pausar após 1 semana porque CPL pareceu alto.

---

## Referências confiáveis

- [LinkedIn — Formatos de anúncio](https://business.linkedin.com/marketing-solutions/ad-formats) — verificado 2026-05-01
- [LinkedIn — Lead Gen Forms](https://business.linkedin.com/marketing-solutions/native-advertising/lead-gen-forms) — verificado 2026-05-01
- [LinkedIn — Segmentação](https://business.linkedin.com/marketing-solutions/targeting) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [outros-linkedin-ads.changelog.md](outros-linkedin-ads.changelog.md)
