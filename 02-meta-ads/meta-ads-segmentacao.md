# Meta Ads: Segmentação de Público

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 02-meta-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- Criando Ad Sets novos — segmentação define quem vai ver o anúncio
- CPL ou CPA alto sem explicação óbvia — público errado é causa frequente
- Testando novos mercados ou nichos — segmentação para explorar

**Não usar quando:**
- Usando Advantage+ Shopping Campaigns (ASC) — o algoritmo controla o público automaticamente
- Remarketing de lista de clientes existente (Custom Audience de lista) — sem segmentação adicional, só a lista

---

## Pré-requisitos

```
- Pixel instalado e com histórico de eventos (para Custom Audiences de site)
- Lista de e-mails ou telefones de clientes existentes (para Custom Audience de lista)
- Persona do comprador definida (ver estrategia-personas-comprador)
- Pelo menos 1.000 clientes para criar Lookalike útil (mínimo 100, mas < 1k gera LAL fraco)
```

---

## Padrões e convenções

### Tipos de público — hierarquia de qualidade

```
1. Custom Audience (melhor qualidade — mais quente)
   → Dados próprios: pessoas que já interagiram com a marca
   
2. Lookalike Audience (qualidade média-alta)
   → Pessoas semelhantes às suas Custom Audiences
   
3. Core Audience / Interesses (menor qualidade — público frio)
   → Segmentação por interesses, comportamentos e demografia
   
4. Advantage+ Audience (IA da Meta — qualidade variável)
   → Meta escolhe o público com base nos criativos e objetivo
```

### Custom Audiences — tipos e usos

```
De lista (upload de dados):
  → Fontes: e-mail, telefone, ID de usuário Meta
  → Hashing automático: Meta faz SHA-256 antes de enviar
  → Taxa de correspondência esperada: 30-60% (e-mail) / 50-70% (telefone celular)
  → Uso: remarketing de base de leads, base de clientes (excluir de campanhas de aquisição)
  → Mínimo: 100 correspondências (útil com 1.000+)

De site (via Pixel):
  → Visitantes de todas as páginas — últimos X dias (1, 7, 14, 30, 60, 90, 180)
  → Visitantes de página específica (ex: /obrigado = leads, /checkout = quase-compradores)
  → Eventos: quem disparou AddToCart, InitiateCheckout, Purchase
  → Mais úteis: VisitanteSite-30d, AbandonouCheckout-14d, Compradores-90d

De engajamento (no Meta):
  → Pessoas que interagiram com a Página nos últimos 365 dias
  → Quem assistiu X% do vídeo (25%, 50%, 75%, 95%) — nurturing por etapa
  → Quem abriu Lead Ad mas não enviou — follow-up quente
  → Quem enviou mensagem para a página

De WhatsApp Business:
  → Quem enviou mensagem nos últimos 365 dias — público quente

Janelas de tempo recomendadas por etapa:
  BOFU (mais quente): 7-14 dias
  MOFU: 30-60 dias
  TOFU remarketing: 90-180 dias
```

### Lookalike Audiences — configuração

```
Percentual e tamanho:
  1% → mais semelhante à fonte, menor público, mais qualidade
  2-3% → equilíbrio entre qualidade e volume
  5-10% → mais volume, menos semelhante — usar para escala quando 1% saturou

Melhores fontes para Lookalike (em ordem de qualidade):
  1. Lookalike de Compradores (valor = Purchase) — LAL de clientes reais
  2. Lookalike de Leads qualificados (MQL/SQL do CRM)
  3. Lookalike de VisitanteSite-30d — usuários engajados
  4. Lookalike de Engajadores da página — público mais frio

Value-Based Lookalike (LAL por valor):
  → Upload de lista de clientes com coluna "value" (quanto cada cliente pagou)
  → Meta prioriza encontrar quem se parece com os clientes de maior valor
  → Usar quando tem variação de ticket médio entre clientes

Stacking de LAL (como testar):
  LAL 1% | LAL 2-3% | LAL 4-5% — 3 Ad Sets separados, mesmo criativo
  → Ver qual percentual gera melhor CPL/CPA antes de escalar
```

### Core Audiences — interesses e comportamentos

```
Quando usar:
  → Público frio sem dados históricos (conta nova, produto novo)
  → Descobrir novos segmentos ainda não cobertos pelas Custom Audiences
  → TOFU awareness com alcance amplo

Como configurar:
  Localização: cidade, estado, raio (ex: 20km de São Paulo) ou país
  Idade: sempre questionar se o corte de idade é real — limite estreito reduz público sem necessidade
  Interesses: categorias temáticas (ex: Empreendedorismo, Marketing Digital, Finanças)
  Comportamentos: "Frequentemente viaja a negócios", "Pequena empresa — proprietário"
  Cargo/Empregador: útil para B2B (ex: Gerente de Marketing, Diretor Financeiro)

Regras de combinação:
  → Não usar "Estreitar Público" (AND entre interesses) — reduz muito o tamanho
  → Usar "Excluir Pessoas" para remover compradores recentes, concorrentes
  → Tamanho ideal: 500k - 3M (menor = poucos dados para o algoritmo, maior = muito frio)

Interesses úteis por nicho (exemplos):
  Empreendedorismo: Marketing, Empreendedorismo, SEBRAE, Gestão de negócios
  Saúde/Estética: Saúde e bem-estar, Beleza, Fitness, Nutrição
  Imóveis: Imóveis, Decoração de interiores, Reforma, CAIXA Econômica Federal
  Educação: Cursos online, Educação, Carreira profissional
```

### Advantage+ Audience — quando usar

```
O que é:
  → Meta usa IA para encontrar o público ideal sem segmentação manual
  → Você pode dar uma "sugestão de público" mas a Meta pode expandir além
  → Integrado nas Advantage+ Shopping Campaigns (ASC)

Quando usar:
  → Conta com histórico sólido de conversões (>100 conversões/mês)
  → Produto de massa sem nicho muito específico
  → Quando interesses manuais já saturaram e quer expandir
  → ASC para e-commerce — Advantage+ é obrigatório nesse formato

Quando NÃO usar:
  → Produto de nicho muito específico (B2B técnico, produto regulado)
  → Conta nova sem dados históricos — sem dados, a IA não tem referência
  → Budget baixo (< R$ 100/dia) — sem volume suficiente para a IA aprender
```

### Exclusões — obrigatórias e recomendadas

```
SEMPRE excluir:
  → Compradores recentes (últimos 30-60 dias) de campanhas de aquisição
     → Por quê: pagar para anunciar para quem já comprou = desperdício
  → Funcionários e sócios (se relevante pelo tamanho de público)

RECOMENDADO excluir de campanhas de aquisição (TOFU):
  → Engajadores da página (já te conhecem — jogar para MOFU)
  → Visitantes do site (já te conhecem — jogar para MOFU/BOFU)
  → Lista de e-mails da base (remarketing separado)

Exclusões de concorrentes:
  → Excluir interesses dos concorrentes diretos — reduz público que já escolheu outra marca
  → Útil quando concorrente tem marca forte (ex: no segmento de software — excluir interesse no concorrente A e B)
```

---

## Templates prontos

### Estrutura de públicos por etapa do funil

```markdown
## Públicos — [Campanha] — [Mês/Ano]

### TOFU (Público Frio — Aquisição)
- Core Audience: [interesses] | [faixa etária] | [localização]
  Tamanho estimado: [X milhões]
- LAL 1% de Compradores | [tamanho]
- LAL 2-3% de VisitanteSite-30d | [tamanho]
Exclusão: Compradores-60d + Base de Leads

### MOFU (Público Morno — Nurturing)
- Custom Audience: Engajadores da Página 180d
- Custom Audience: Visitantes do Site 60d (excl. compradores)
- Custom Audience: 50% Vídeo Views 90d
Exclusão: Compradores-60d

### BOFU (Público Quente — Conversão)
- Custom Audience: AbandonouCheckout 14d
- Custom Audience: VisitanteSite 14d (excl. compradores)
- Custom Audience: Base de Leads (CRM) que não comprou
Sem exclusão adicional — público já é pequeno e qualificado
```

---

## Checklist de qualidade

- [ ] Custom Audiences criadas antes de lançar remarketing (site precisa de Pixel ativo)
- [ ] Tamanho do público verificado (mín 500k para TOFU frio, não há mínimo para remarketing)
- [ ] Compradores excluídos de campanhas de aquisição
- [ ] Ad Sets separados por temperatura de público (frio / morno / quente)
- [ ] LAL criado a partir da melhor fonte disponível (compradores > leads > visitantes)
- [ ] Advantage+ usado apenas quando conta tem histórico de conversões
- [ ] Janela de tempo dos Custom Audiences adequada à etapa do funil

---

## Armadilhas comuns

**Segmentação muito estreita:** múltiplos filtros de interesse + comportamento + restrição de idade + localização → público de 50k. O algoritmo não tem dados suficientes. Remover filtros até chegar em 500k+.

**Não excluir compradores:** gastar budget para mostrar anúncio de "Compre agora" para quem já comprou. Criar Custom Audience de compradores e excluir em todas as campanhas de aquisição.

**LAL de fonte ruim:** LAL de seguidores da página (engajamento de qualidade desconhecida). LAL de compradores reais é sempre mais preciso. Priorizar a melhor fonte.

**Audience overlap (sobreposição):** dois Ad Sets com públicos semelhantes competem entre si no leilão, elevando o CPM. Usar Audience Overlap tool no Ads Manager para checar antes de publicar.

**Advantage+ sem dados:** usar Advantage+ Audience em conta nova sem histórico de conversões. Sem referência de quem converte, a IA fica no escuro. Usar interesses manuais primeiro, Advantage+ quando tem > 100 conversões/mês.

---

## Referências confiáveis

- [Meta — Custom Audiences](https://www.facebook.com/business/help/744354708981227) — verificado 2026-05-01
- [Meta — Lookalike Audiences](https://www.facebook.com/business/help/164749007013531) — verificado 2026-05-01
- [Meta — Advantage+ Audience](https://www.facebook.com/business/help/1144352526048951) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [meta-ads-segmentacao.changelog.md](meta-ads-segmentacao.changelog.md)
