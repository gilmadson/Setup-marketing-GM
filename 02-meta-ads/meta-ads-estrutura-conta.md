# Meta Ads: Estrutura de Conta

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 02-meta-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- Criando uma conta de anúncios do zero — estrutura errada desde o início prejudica o aprendizado do algoritmo
- Conta existente com performance caindo — estrutura fragmentada pode ser a causa
- Escalando budget — estrutura precisa suportar escala sem confundir o algoritmo

**Não usar quando:**
- Conta já estruturada e performando bem — não reorganizar o que funciona
- Boost de post isolado — não há estrutura a seguir, apenas impulsionar

---

## Pré-requisitos

```
- Business Manager criado (business.facebook.com) — não anunciar com conta pessoal
- Pixel do Meta instalado no site antes de criar campanhas de conversão
- Catálogo de produtos configurado (para e-commerce com Shopping/Collection)
- Método de pagamento adicionado e aprovado
- Domínio verificado no Business Manager (obrigatório após iOS 14)
```

---

## Padrões e convenções

### Hierarquia da conta — 3 níveis

```
CAMPAIGN (Campanha)
  ↳ Define: Objetivo, Budget (se CBO), Limite de gasto
  ↳ Regra: 1 objetivo por campanha — nunca misturar Leads e Sales na mesma campanha

    AD SET (Conjunto de Anúncios)
      ↳ Define: Público, Posicionamentos, Budget (se ABO), Otimização, Prazo
      ↳ Regra: 1 hipótese de público por Ad Set

        AD (Anúncio)
          ↳ Define: Criativo (imagem/vídeo), Copy, CTA, URL de destino
          ↳ Regra: 3-5 anúncios por Ad Set para o algoritmo testar e otimizar
```

### Objetivos de campanha — escolha correta

```
AWARENESS (Conscientização):
  Reconhecimento de Marca  → CPM otimizado, máxima frequência — TOFU
  Alcance                  → máximo de pessoas únicas, frequência baixa — TOFU grande

TRAFFIC (Tráfego):
  Tráfego para site        → CPC, otimiza para cliques — MOFU
  Tráfego para perfil      → seguidores, engajamento — MOFU social

ENGAGEMENT (Engajamento):
  Engajamento com post     → curtidas, comentários, compartilhamentos
  Visualizações de vídeo   → ThruPlay (15s+) ou 2 segundos — TOFU/MOFU

LEADS:
  Geração de Leads (Lead Ads) → formulário nativo no Meta — sem site próprio
  Leads (site)                → conversão no site via pixel — com landing page

SALES (Vendas):
  Vendas (catálogo)        → remarketing dinâmico, Shopping — e-commerce
  Vendas (site)            → conversão via pixel — D2C, B2B

Regra de escolha:
  → Não tem site ou landing page → Lead Ads
  → E-commerce com catálogo → Vendas com catálogo (remarketing dinâmico)
  → Lead generation com LP → Leads (site) ou Vendas (site)
  → Awareness puro → Reconhecimento de Marca ou Alcance
```

### CBO vs ABO — quando usar cada um

```
CBO — Campaign Budget Optimization (budget na campanha):
  Algoritmo distribui o budget entre os Ad Sets automaticamente
  → Usar quando: 3+ Ad Sets validados, budget > R$ 300/dia, escala
  → Vantagem: eficiência — mais dinheiro vai para quem está performando
  → Desvantagem: pode concentrar tudo em 1 Ad Set e não testar os outros
  → Budget mínimo CBO: R$ 100/dia por Ad Set ativo (ex: 3 Ad Sets = R$ 300+/dia)

ABO — Ad Set Budget Optimization (budget no conjunto de anúncios):
  Você controla quanto cada Ad Set recebe
  → Usar quando: testando novos públicos, fase inicial, budget baixo
  → Vantagem: controle — garante que cada público seja testado
  → Desvantagem: menos eficiente que CBO em escala

Regra: começar com ABO para testar, migrar para CBO quando souber o que funciona
```

### Nomenclatura padrão

```
Campanha:
  [Produto/Serviço] | [Objetivo] | [Público] | [Data Início]
  Exemplos:
    CursoMarketing | Leads | MOFU-Interesses | 2026-05
    LojaXYZ | Vendas | BOFU-Remarketing | 2026-05

Ad Set:
  [Tipo de Público] | [Detalhe] | [Faixa Etária]
  Exemplos:
    Interesse | Empreendedorismo-PME | 25-45
    Custom | VisitanteSite-30d | Todos
    LAL | Compradores-1% | 25-55

Ad:
  [Formato] | [Ângulo de Copy] | [Versão]
  Exemplos:
    Video | Dor-RetornoInvestimento | v1
    Img-1x1 | Prova-Social-Depoimento | v2
    Carrossel | Beneficios-3cards | v1

Por que nomenclatura importa:
  → Filtrar por relatório rapidamente
  → Identificar o que está rodando sem abrir cada um
  → Replicar estruturas que funcionaram
```

### Limites e boas práticas de estrutura

```
Por campanha:
  Máximo recomendado: 5-10 Ad Sets ativos (mais = fragmentação de dados)
  Máximo de Ads por Ad Set: 50 (mas testar com 3-5 ativos)
  
Fase de aprendizado — regras para não resetar:
  → A Meta precisa de 50 eventos de otimização por Ad Set por semana
  → Qualquer alteração significativa reseta o aprendizado:
     - Mudança de público
     - Mudança de orçamento > 30% em menos de 7 dias
     - Pausar e reativar Ad Set
     - Mudança de evento de otimização
  → Não alterar nada nos primeiros 7 dias de uma campanha nova
  → Se for testar algo novo: criar nova campanha — não alterar a que está aprendendo

Estrutura para campanha de leads (exemplo prático):
  CAMPANHA: CursoX | Leads | Frio | 2026-05 [ABO / Objetivo: Leads]
    AD SET 1: Interesse | Marketing-Empreendedorismo | 25-45 [R$ 50/dia]
      → Ad 1: Video | Dor-GastosAds | v1
      → Ad 2: Img | Proposta-Método | v1
      → Ad 3: Carrossel | Beneficios | v1
    AD SET 2: Interesse | Gestao-PME | 30-50 [R$ 50/dia]
      → Ad 1: Video | Dor-GastosAds | v1
      → Ad 2: Img | Proposta-Método | v1
    AD SET 3: LAL | Compradores-1% | 25-55 [R$ 50/dia]
      → Ad 1: Depoimento-Video | v1
      → Ad 2: Oferta-Urgencia | v1
```

---

## Templates prontos

### Estrutura de campanha por objetivo

```markdown
## Estrutura Meta Ads — [Produto] — [Mês/Ano]

### Campanha 1: TOFU Awareness
- **Objetivo:** Reconhecimento de Marca
- **Budget:** R$ [valor]/dia (ABO)
- **Ad Set 1:** [público frio amplo] | R$ [valor]/dia
  - Ad 1: [formato] | [ângulo]
  - Ad 2: [formato] | [ângulo]

### Campanha 2: MOFU Consideration
- **Objetivo:** Tráfego / Leads
- **Budget:** R$ [valor]/dia (ABO)
- **Ad Set 1:** [público morno — interesses específicos] | R$ [valor]/dia
  - Ad 1: [formato] | [ângulo]
- **Ad Set 2:** [engajadores do perfil — Custom Audience] | R$ [valor]/dia
  - Ad 1: [formato] | [ângulo]

### Campanha 3: BOFU Conversion
- **Objetivo:** Leads (site) ou Vendas
- **Budget:** R$ [valor]/dia (CBO — se > 3 Ad Sets validados)
- **Ad Set 1:** Remarketing visitantes site 30d
- **Ad Set 2:** Custom Audience lista de leads
- **Ad Set 3:** LAL 1% de compradores
```

---

## Checklist de qualidade

- [ ] Business Manager configurado — não anunciar com conta pessoal
- [ ] Domínio verificado no Business Manager
- [ ] 1 objetivo por campanha — não misturar
- [ ] Nomenclatura padronizada (campanha / ad set / ad)
- [ ] Budget compatível com número de Ad Sets (mín R$ 50-100/dia por Ad Set)
- [ ] Pixel instalado e testado antes de criar campanha de conversão
- [ ] 3-5 criativos por Ad Set para o algoritmo testar
- [ ] Campanha nova: não alterar nos primeiros 7 dias

---

## Armadilhas comuns

**Muitos Ad Sets com pouco budget:** 5 Ad Sets com R$ 20/dia cada = R$ 100/dia total. Nenhum aprende. Menos Ad Sets, mais budget por Ad Set.

**Objetivo de campanha errado:** usar "Tráfego" quando quer leads — o algoritmo vai otimizar para cliques, não para conversões. Sempre usar o objetivo que representa a ação real desejada.

**Alterar campanha na fase de aprendizado:** mudar público, budget ou criativo nos primeiros 7 dias reseta o aprendizado. Criar nova campanha para testar, nunca mexer na que está em aprendizado.

**Misturar TOFU e BOFU na mesma campanha:** públicos frios e de remarketing no mesmo Ad Set competem entre si. Separar em campanhas diferentes.

**Não usar nomenclatura:** 30 campanhas sem nome padronizado impossibilitam análise. Adotar convenção desde o primeiro anúncio.

---

## Referências confiáveis

- [Meta — Estrutura de conta de anúncios](https://www.facebook.com/business/help/1438417539786378) — verificado 2026-05-01
- [Meta — Campaign Budget Optimization](https://www.facebook.com/business/help/153514848493595) — verificado 2026-05-01
- [Meta — Fase de aprendizado](https://www.facebook.com/business/help/112167992830700) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [meta-ads-estrutura-conta.changelog.md](meta-ads-estrutura-conta.changelog.md)
