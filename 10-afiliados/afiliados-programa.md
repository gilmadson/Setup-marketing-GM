# Afiliados: Estrutura de Programa

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 10-afiliados

---

## Quando usar / Quando não usar

**Usar quando:**
- Produto digital (curso, software, infoproduto) — canal de afiliados é nativo nesse mercado
- Produto físico com margem suficiente para pagar comissão (> 20% de margem bruta)
- Objetivo de escalar vendas sem escalar proporcionalmente o orçamento de mídia
- Negócio que quer canal de distribuição via criadores de conteúdo e parceiros

**Não usar quando:**
- Margem bruta < 20% — comissão + custo de plataforma inviabilizam o modelo
- Produto com ticket muito baixo (< R$50) — comissão absoluta é pequena demais para atrair afiliados
- Sem estrutura para pagar comissões, gerar relatórios e suportar afiliados — programa sem gestão morre

---

## Pré-requisitos

```
- Produto com margem suficiente para comissão (calcular: ver abaixo)
- Plataforma de afiliados ou plugin de rastreamento configurado
- Materiais para afiliados: banners, copy pronto, links rastreáveis
- Processo de pagamento de comissões (recorrência mensal ou quinzenal)
- Definição clara de regras: o que é permitido/proibido na divulgação
```

---

## Padrões e convenções

### Modelos de comissão — tipos e quando usar

```
CPS — Cost per Sale (Custo por Venda):
  → Afiliado recebe % da venda somente quando conversão acontece
  → Modelo mais comum para infoprodutos e e-commerce
  → Vantagem: risco zero para a marca — só paga quando vende
  → Comissão típica:
     Infoprodutos (cursos, ebooks): 30-50% do valor
     SaaS: 20-30% do MRR ou valor do plano, recorrente
     E-commerce físico: 5-15% do valor do pedido (margem menor)

CPA — Cost per Acquisition:
  → Afiliado recebe valor fixo por cada cliente adquirido
  → Usar quando ticket médio é previsível
  → Exemplo: R$50 por cliente que assinou o plano básico
  → Vantagem: previsível para o afiliado (não depende de variação de ticket)

CPL — Cost per Lead:
  → Afiliado recebe valor fixo por lead qualificado gerado
  → Comum em B2B, imóveis, seguros
  → Define o que é "lead qualificado" no contrato (preencheu formulário? Agendou reunião?)
  → Risco: fraude de leads — afiliado pode enviar leads não qualificados para receber comissão

Comissão recorrente (SaaS):
  → Afiliado recebe % enquanto o cliente indicado continua pagando
  → Modelo mais atraente para afiliado — receita passiva
  → Exemplo: 20% do plano mensal por 12 meses, ou enquanto o cliente ficar
  → Vantagem competitiva: poucos programas oferecem recorrência

Como calcular a comissão máxima viável:
  Fórmula: Comissão Máxima = Margem Bruta × % destinada a afiliados
  
  Exemplo:
    Produto: R$297
    Custo do produto: R$50
    Margem bruta: R$247 (83%)
    % destinada a afiliados: 30%
    Comissão máxima: R$297 × 30% = R$89/venda
    
  Regra prática:
    Infoproduto: destinar 30-50% da margem para comissão
    E-commerce: 5-15% do valor do pedido (depende da margem de cada produto)
    SaaS: 20-30% do MRR do cliente indicado
```

### Rastreamento — como atribuir a venda ao afiliado correto

```
Mecanismos de rastreamento:

Cookie de afiliado:
  → Quando usuário clica no link do afiliado, cookie é salvo no navegador
  → Se o usuário comprar dentro da janela do cookie, venda é atribuída ao afiliado
  → Janela de cookie: 30 dias (padrão) | 60 dias | 90 dias | sessão apenas
  → Regra: janela mais longa = afiliado mais atraído (mais justo para produtos de consideração longa)
  → Problema: usuário troca de navegador ou device → cookie perdido

UTM por afiliado:
  → Link exclusivo com UTM identificando o afiliado
  → Rastreado no GA4: utm_source=[afiliado] / utm_medium=afiliado / utm_campaign=[programa]
  → Complementar ao cookie — garante atribuição via GA4 mesmo com limitações de cookie

Sub-ID / Parâmetro adicional:
  → Afiliado adiciona parâmetro ao link para rastrear qual canal gerou cada venda
  → Exemplo: link base + ?sub=instagram_reel ou ?sub=email_lista
  → Útil para afiliados com múltiplos canais — entendem de onde vem o resultado

Plataformas de afiliados (rastreamento nativo):
  → Hotmart, Eduzz, Monetizze: rastreamento por cookie + relatórios automáticos
  → Impact, PartnerStack, Refersion: para programas próprios mais sofisticados (SaaS, e-commerce)
  → WooCommerce + plugin (AffiliateWP): para e-commerce próprio
  → Shopify + app (UpPromote, Refersion): para Shopify

Multi-touch attribution no programa de afiliados:
  → First click: afiliado que trouxe o primeiro toque recebe a comissão
  → Last click: afiliado do último clique recebe (padrão da maioria das plataformas)
  → Conflito: usuário clicou no link do Afiliado A, depois no do Afiliado B → quem recebe?
  → Definir regra no contrato e ser transparente com afiliados
```

### Plataformas — qual usar

```
Para infoprodutos (cursos, ebooks, mentorias):

  Hotmart:
    → Líder no mercado brasileiro
    → Comissão da plataforma: 9,9% + R$1 por venda (variável por plano)
    → Rastreamento: cookie 30 dias padrão
    → Funcionalidades: clube de afiliados, material de divulgação, pagamentos automáticos
    → Melhor para: infoprodutos com ticket R$100-2.000

  Eduzz:
    → Similar ao Hotmart, mercado menor
    → Comissão da plataforma: varia por plano
    → Diferencial: funcionalidade de assinatura e recorrência

  Monetizze:
    → Forte em produtos físicos e suplementos
    → Integração com e-commerce
    → Usado por marcas de saúde/beleza

Para SaaS e software:
  PartnerStack:
    → Especializado em SaaS B2B
    → Funcionalidades: portal do parceiro, comissão recorrente, sub-parceiros
    → Custo: a partir de US$500/mês

  Impact:
    → Plataforma enterprise para programas de afiliados, parceiros e influenciadores
    → Mais caro, melhor para empresas com volume

Para e-commerce próprio:
  AffiliateWP (WordPress/WooCommerce):
    → Plugin nativo para WooCommerce
    → A partir de US$149/ano
    → Rastreamento por cookie + relatórios no WP

  UpPromote / Refersion (Shopify):
    → Apps nativos do Shopify App Store
    → Fácil configuração, rastreamento automatizado

Programa próprio (sem plataforma):
  → Possível com: cupons de desconto rastreáveis + planilha de controle
  → Custo zero de plataforma, mas trabalho manual de rastreamento e pagamento
  → Viável para: programas pequenos (< 20 afiliados), produtos digitais simples
```

### Recrutamento de afiliados — como encontrar

```
Quem recrutar:

  Criadores de conteúdo do nicho:
    → Blogs, canais YouTube, podcasts que têm audiência da persona
    → Já produzem conteúdo sobre o tema — afiliação é extensão natural
    → Como contatar: email direto, LinkedIn, Instagram DM com proposta clara

  Micro-influenciadores do segmento:
    → Já fazem parcerias pagas — abertos a programa de afiliados recorrente
    → Proposta: ao invés de cachê único, comissão recorrente (potencial maior)

  Clientes satisfeitos:
    → Já conhecem e aprovam o produto — o mais fácil de recrutar
    → Automação: email pós-compra com convite para o programa de afiliados
    → Taxa de adesão: 2-10% dos clientes convidados

  Parceiros complementares:
    → Empresas/profissionais que atendem a mesma persona mas não concorrem
    → Exemplo: agência de tráfego pago recomendando ferramenta de analytics
    → Parceria win-win: cliente deles é lead qualificado para você

  Afiliados de plataforma:
    → Hotmart/Eduzz têm marketplace onde afiliados buscam produtos para promover
    → Listar o produto com comissão competitiva = afiliados chegam organicamente
    → Risco: afiliados de plataforma geralmente têm qualidade variável

Proposta de valor para o afiliado (o que comunicar no recrutamento):
  → Comissão e modelo (CPS, recorrente, valor absoluto)
  → Janela de cookie
  → Materiais disponíveis (banners, copy, links rastreáveis)
  → Suporte e contato direto
  → Histórico de conversão do produto (taxa de conversão da LP)
  → Ticket médio (para estimar ganho por indicação)
```

### Prevenção de fraude

```
Tipos de fraude comuns em programas de afiliados:

  Cookie stuffing:
    → Afiliado injeta cookie sem clique real (usuário visita um site e o afiliado "injeta" o cookie)
    → Recebe comissão de venda que não gerou
    → Prevenção: monitorar relatórios de conversão + verificar padrões anormais de cliques vs vendas
    → Sinal: afiliado com 5.000 cliques e 50% de conversão (anormalmente alto)

  Auto-afiliação:
    → Afiliado compra usando o próprio link para receber desconto equivalente à comissão
    → Prevenção: bloquear compras com o próprio email/CPF ou mesmo IP

  Leads falsos (programas CPL):
    → Afiliado gera leads com dados falsos ou de baixa qualidade para acumular comissão
    → Prevenção: definir "lead qualificado" claramente (preencheu + respondeu ao contato), pagar com delay após qualificação

  Violação de termos de tráfego:
    → Afiliado usa Google Ads com palavras-chave da sua marca (brand bidding proibido)
    → Afiliado promete resultados que a marca não pode garantir
    → Prevenção: monitorar Google Search "seu produto" + buscas de branded + lista de termos proibidos

  Como monitorar:
    → Relatório semanal de cliques vs conversões por afiliado — CR acima de 15% = revisar
    → Comparar IP de clique com IP de compra — IPs iguais = possível auto-afiliação
    → Amostras aleatórias de leads (CPL): ligar/contatar para verificar qualidade
    → Ferramentas: a maioria das plataformas tem detecção automática básica
```

### Gestão do programa — operação contínua

```
Materiais para afiliados (kit de divulgação):
  → Links rastreáveis por afiliado (plataforma gera automaticamente)
  → Banners em múltiplos tamanhos (feed Instagram, YouTube, blog, email)
  → Copy pronto: post de Instagram, email de recomendação, legenda de vídeo
  → Landing page exclusiva para afiliados (com conversão otimizada para tráfego frio)
  → FAQ de objeções (para o afiliado responder perguntas dos seguidores)

Comunicação com afiliados:
  → Newsletter mensal: resultados do programa, novos materiais, promoções em destaque
  → Grupo privado (WhatsApp ou Slack): para afiliados top — respostas rápidas + senso de comunidade
  → Ranking de top afiliados: reconhecimento público + incentivo competitivo
  → Suporte: email ou WhatsApp para dúvidas sobre links, comissões, materiais

Pagamento de comissões:
  → Frequência: mensal ou quinzenal (mensal é padrão)
  → Plataformas de infoproduto: pagamento automático pela plataforma (Hotmart paga direto)
  → Programa próprio: planilha de controle + PIX na data acordada
  → Mínimo para saque: R$50-100 (evita micro-transações)
  → Nota fiscal: exigir NF de afiliados PJ; para PF, desconto de IR conforme legislação

Métricas do programa:
  → Número de afiliados ativos (que geraram ao menos 1 venda no mês)
  → EPC — Earnings Per Click: receita total / cliques totais do programa
    → Métrica que o afiliado usa para comparar programas — quanto ganha por clique
  → Taxa de conversão do programa: vendas / cliques
  → Ticket médio das vendas de afiliados vs venda direta
  → Top 20% de afiliados: geralmente são 80% das vendas — focar neles
```

---

## Templates prontos

### Página de recrutamento de afiliados (estrutura)

```markdown
## Programa de Afiliados — [Nome do Produto]

### Por que ser afiliado?
- Comissão de [X]% por venda (R$ [Y] por indicação)
- Cookie de [30/60/90] dias
- [Recorrente: receba toda vez que o cliente renovar]
- Materiais prontos: banners, copy, links rastreáveis
- Pagamento todo dia [5] via PIX

### O produto
[Descrição em 2-3 linhas — o que é, para quem, resultado entregue]

### Números do programa
- Taxa de conversão média da LP: [X]%
- Ticket médio: R$[Y]
- EPC estimado: R$[Z] por clique

### Como funciona
1. [Cadastre-se no programa]
2. [Receba seu link exclusivo]
3. [Divulgue para sua audiência]
4. [Receba sua comissão]

### Regras de divulgação
✅ Permitido: [redes sociais, blog, email, YouTube, ads]
❌ Proibido: [brand bidding no Google, spam, promessas não autorizadas]

[Botão: Quero ser afiliado]
```

---

## Checklist de qualidade

- [ ] Comissão calculada dentro da margem viável (não inviabiliza o produto)
- [ ] Janela de cookie definida e alinhada com o ciclo de decisão do produto
- [ ] Plataforma de rastreamento configurada e testada antes do lançamento
- [ ] Contrato ou termos de programa com regras claras (o que é permitido/proibido)
- [ ] Kit de divulgação criado: links, banners, copy pronto
- [ ] Processo de pagamento configurado (frequência, mínimo, forma)
- [ ] Monitoramento anti-fraude ativo (alertas de CR anormal, auto-afiliação bloqueada)
- [ ] Comunicação regular com afiliados ativos (newsletter ou grupo)
- [ ] Métricas revisadas mensalmente: afiliados ativos, EPC, top performers

---

## Armadilhas comuns

**Comissão inviável:** oferecer 50% de comissão em produto com margem de 30%. Cada venda dá prejuízo. Calcular margem real antes de definir comissão — incluir custo da plataforma e processamento.

**Programa sem materiais:** recrutar afiliados e deixar que "criem tudo sozinhos". Afiliados sem materiais não divulgam ou divulgam de forma que prejudica a marca. Kit de divulgação pronto é obrigatório.

**Sem regras de tráfego:** afiliados usando Google Ads com a brand keyword da empresa (brand bidding). Marca paga 2x pelo mesmo clique (anúncio próprio + comissão do afiliado). Proibir brand bidding explicitamente nos termos.

**Pagar sem verificar qualidade (CPL):** programa de leads que paga por qualquer cadastro. Afiliado enche com leads de baixíssima qualidade. Definir lead qualificado (preencheu + atendeu ao contato inicial) e pagar após validação.

**Ignorar top performers:** tratar todos os afiliados da mesma forma. Os top 3-5 afiliados respondem por 50-80% das vendas. Criar programa VIP com comissão maior, suporte dedicado e acesso antecipado a lançamentos.

---

## Referências confiáveis

- [Hotmart — Como criar programa de afiliados](https://hotmart.com/pt-BR/blog/como-ser-afiliado) — verificado 2026-05-01
- [Receita Federal — Tributação de afiliados](https://www.gov.br/receitafederal/) — verificado 2026-05-01
- [Impact — Affiliate Marketing Best Practices](https://impact.com/affiliate/) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [afiliados-programa.changelog.md](afiliados-programa.changelog.md)
