# Meta Ads: Otimização e Testes

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 02-meta-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- Campanha rodando há pelo menos 7 dias com dados — otimizar antes disso reseta o aprendizado
- CPA/CPL acima da meta por 2 semanas — ajuste estruturado, não reativo
- Escalando budget — protocolo de escala evita reset de aprendizado

**Não usar quando:**
- Campanha recém-lançada (< 7 dias) — deixar o algoritmo aprender antes de intervir
- Campanha de boost simples sem objetivo de conversão — não há o que otimizar estruturalmente

---

## Pré-requisitos

```
- Pixel + CAPI configurados (ver meta-ads-pixel-api)
- Campanha ativa com pelo menos 7 dias de dados
- Metas de CPL/CPA/ROAS definidas no briefing (ver estrategia-briefing-campanha)
- Acesso ao Ads Manager com permissão de edição
```

---

## Padrões e convenções

### Fase de aprendizado — entender antes de otimizar

```
O que é:
  → Período em que o algoritmo do Meta testa variações para encontrar quem converte
  → Cada Ad Set precisa de 50 eventos de otimização por semana para sair do aprendizado
  → Enquanto em aprendizado: CPA/CPL instável, entrega imprevisível — normal

Como saber se está em aprendizado:
  → Ads Manager → Ad Set → Status = "Aprendizagem" (ícone de livro)
  → Após 50 conversões/semana: status muda para "Ativo"
  → Sem atingir 50/semana: "Aprendizagem limitada" — considerar aumentar budget ou mudar evento

O que RESETA o aprendizado (evitar nos primeiros 7 dias):
  → Mudança de público-alvo
  → Mudança de evento de otimização (ex: de Lead para Purchase)
  → Mudança de budget > 30% em um único ajuste
  → Pausar e reativar o Ad Set
  → Editar o criativo do anúncio
  → Adicionar novo anúncio ao Ad Set

Estratégia: criar novo Ad Set/campanha para testar em vez de editar o que está ativo
```

### Estratégias de lance — quando usar cada uma

```
Custo Mais Baixo (padrão — sem lance manual):
  → Meta gasta o budget buscando o menor CPA possível
  → Usar: fase de aprendizado, campanhas novas, quando não tem referência de CPA
  → Risco: CPA pode ser volátil no início

Meta de Custo (Cost Cap):
  → Define um CPA máximo que o Meta tenta não ultrapassar
  → Usar: quando tem meta de CPL/CPA clara e histórico de pelo menos 2 semanas
  → Risco: se o lance for baixo demais, o algoritmo não consegue entregar volume → delivery baixo
  → Configurar: 10-20% acima do CPL/CPA médio atual para não travar a entrega

Meta de ROAS (ROAS Cap):
  → Meta tenta manter o ROAS acima do valor definido
  → Usar: e-commerce com objetivo de retorno mínimo por real investido
  → Risco: idem ao Cost Cap — lance muito alto trava a entrega
  → Configurar: começar com ROAS mínimo real (não ideal) e aumentar conforme a campanha aprende

Lance de Valor Máximo (Highest Value Bid):
  → Meta prioriza usuários com maior probabilidade de gerar maior receita
  → Usar: e-commerce com grande variação de ticket médio
  → Requer: Purchase com parâmetro value configurado + histórico de conversões com valor
```

### CBO vs ABO — gestão de budget

```
ABO (budget no Ad Set) — controle granular:
  → Usar na fase de testes: garantir que cada público/público receba budget suficiente
  → Budget mínimo por Ad Set: R$ 50-100/dia (abaixo = sem dados para aprender)
  → Aumentar: máx 20-30% por ajuste, aguardar 48-72h antes do próximo aumento

CBO (budget na campanha) — eficiência algorítmica:
  → Usar quando: 3+ Ad Sets já validados, quer escalar para o mais performático
  → Meta distribui automaticamente mais para quem está convertendo melhor
  → Risco: Ad Set novo pode receber pouco budget e não aprender — usar spend limit mínimo

Spend Limit no CBO:
  → Configurar gasto mínimo por Ad Set quando quer garantir que todos recebam budget
  → Ads Manager → Ad Set → Limite de Gasto → Definir mínimo diário
  → Usar para proteger Ad Sets de teste dentro de um CBO

Protocolo de escala de budget:
  SEMANA 1-2: ABO, R$ 50-100/dia por Ad Set, deixar aprender
  SEMANA 3+: migrar para CBO os Ad Sets com CPA dentro da meta
  Aumento: +20-30% por semana → aguardar 72h → analisar → novo aumento se CPA ok
  Nunca: dobrar o budget de uma vez (reseta aprendizado, piora CPM)
```

### Regras automáticas — automatizar otimização rotineira

```
Como criar: Ads Manager → Regras → Criar Regra

Regras recomendadas:

1. Pausar anúncio com CPA muito alto:
   Condição: CPA > [meta × 2] | Janela: últimos 7 dias | Volume: > 100 impressões
   Ação: Pausar anúncio
   Notificação: Email

2. Aumentar budget quando ROAS está bom (e-commerce):
   Condição: ROAS > [meta ROAS × 1.3] | Janela: últimos 3 dias
   Ação: Aumentar budget em 20%
   Frequência: no máximo 1x por dia

3. Alerta de frequência alta:
   Condição: Frequência > 3 (conversão) ou > 5 (awareness) | Janela: últimos 7 dias
   Ação: Notificação por email
   → Não pausar automaticamente — verificar manualmente se é problema de público ou criativo

4. Pausar campanha fora do horário (para produtos com horário pico):
   Condição: hora do dia 00:00-07:00
   Ação: Pausar campanha
   → Usar dayparting para produtos de decisão rápida (ex: delivery, eventos)

Cuidado com regras:
  → Testar regras em período de baixo volume antes de aplicar a tudo
  → Revisar semanalmente se as condições ainda fazem sentido com os dados atuais
  → Regra de pausa muito agressiva pode pausar campanha que estava em fase de aprendizado
```

### Testes A/B — protocolo estruturado

```
O que testar (em ordem de impacto):
  1. Criativo (hook, formato, ângulo de mensagem) — maior variância de resultado
  2. Público (interesses vs LAL vs Advantage+)
  3. Landing page (ver criativos-landing-page-cro)
  4. CTA (Saiba mais vs Comprar agora)
  5. Estratégia de lance (Custo Mais Baixo vs Meta de Custo)

Configuração de teste:
  → Ads Manager → Criar → Teste A/B (ferramenta nativa) OU 2 campanhas idênticas com 1 variável diferente
  → Duração mínima: 7 dias (14 dias para volume menor)
  → Budget igual entre variantes
  → Métrica de decisão definida ANTES: CTR (TOFU), CPL (leads), CPA/ROAS (vendas)
  → Significância estatística: Meta mostra "confiança" — aguardar > 95% de confiança antes de declarar vencedor

Armadilha do teste:
  → Olhar resultados antes de 7 dias e tomar decisão prematura
  → Mudar algo durante o teste (invalida o resultado)
  → Testar 2 variáveis ao mesmo tempo (não sabe qual causa a diferença)
```

### Sinais de fadiga de criativo e ação corretiva

```
Sinais de alerta (verificar semanalmente):
  → CTR caindo > 20% semana a semana
  → CPM aumentando sem sazonalidade que justifique
  → Frequência > 3x/semana para objetivo de conversão
  → CPA aumentando progressivamente

Ação corretiva por nível:
  Nível 1 — Fadiga leve (frequência 2-3x, CTR caiu 10-20%):
    → Adicionar novos criativos ao Ad Set existente
    → Não pausar os antigos — deixar o algoritmo redistribuir

  Nível 2 — Fadiga moderada (frequência 3-5x, CTR caiu 20-40%):
    → Pausar criativos piores
    → Criar novo Ad Set com público expandido (LAL maior ou Advantage+)

  Nível 3 — Fadiga severa (frequência > 5x, CPL/CPA 50%+ acima da meta):
    → Pausar o Ad Set
    → Criar nova campanha com criativos completamente novos e novo ângulo de mensagem
    → Esperar 2-4 semanas antes de reativar o público — "descansar" o criativo
```

### Advantage+ Shopping Campaigns (ASC) — e-commerce

```
O que é:
  → Formato automatizado para e-commerce: Meta controla público, posicionamentos e criativos
  → Combina remarketing + aquisição em 1 campanha
  → Usa catálogo de produtos para gerar anúncios dinâmicos automaticamente

Quando usar:
  → E-commerce com catálogo configurado e histórico de conversões (> 30 compras/mês)
  → Quer simplificar a gestão e deixar a IA otimizar
  → Quando campanhas manuais já estão com CPA dentro da meta e quer escalar

Configurações-chave do ASC:
  → Budget da campanha (não por Ad Set — estrutura simplificada)
  → Definir limite de % do budget para audiências existentes (ex: máx 30% para remarketing)
    → Garante que a maioria do budget vá para aquisição de novos clientes

Limitações:
  → Menos controle de segmentação (você não define o público manualmente)
  → Não ideal para produtos de nicho muito específico ou B2B
  → Criativo: carregar múltiplos assets (imagens, vídeos, textos) — Meta testa as combinações
```

---

## Templates prontos

### Dashboard semanal de otimização

```markdown
## Revisão Semanal Meta Ads — [Semana de DD/MM a DD/MM]

### Métricas principais

| Campanha | Budget | Impressões | CTR | CPL/CPA | ROAS | Status |
|----------|--------|-----------|-----|---------|------|--------|
| [nome] | R$ | | % | R$ | x | Aprendizagem/Ativo/Problema |

### Ad Sets na fase de aprendizado
- [Ad Set A]: [X] conversões esta semana, meta 50 → [% concluído]

### Criativos (Top 3 melhor e pior)
Melhor: [nome] | CTR [%] | CPL R$ [valor]
Pior: [nome] | CTR [%] | CPL R$ [valor] → Pausar / Testar variação

### Frequência (alertas)
- [Ad Set X]: frequência [N]x → [ação: adicionar criativo / expandir público]

### Ajustes desta semana
- [o que foi ajustado, por que, resultado esperado]

### Planejamento da próxima semana
- [testes, novos criativos, mudanças de budget]
```

---

## Checklist de qualidade

- [ ] Não alterar nada nos primeiros 7 dias de campanha nova
- [ ] Aguardar 50 conversões/semana por Ad Set antes de escalar
- [ ] Aumentar budget máx 20-30% por ajuste (nunca dobrar)
- [ ] Regras automáticas configuradas para alertas de CPA e frequência
- [ ] Revisar frequência semanalmente (alerta: > 3x para conversão)
- [ ] Teste A/B com 1 variável por vez e duração mínima de 7 dias
- [ ] Criativos renovados quando frequência > 3x ou CTR caiu > 20%

---

## Armadilhas comuns

**Otimizar antes dos 7 dias:** pausar anúncio no dia 3 porque o CPL estava alto. Fase de aprendizado é instável por definição — deixar completar antes de julgar.

**Aumentar budget de uma vez:** dobrar o budget do dia para noite. O algoritmo reinicia o aprendizado. Aumentar 20-30% por vez, aguardar 72h, depois novo aumento.

**Regra automática muito agressiva:** pausar Ad Set com CPA alto em janela de 1 dia. 1 dia pode ser flutuação normal. Usar janela de 7 dias para decisões de pausa.

**Mudar tudo ao mesmo tempo:** trocar público + criativo + budget em 1 ajuste. Não sabe o que causou a melhora ou piora. 1 variável por vez.

**Ignorar frequência:** campanha com ROAS bom mas frequência 7x. O público vai saturar em 2 semanas e o CPA vai explodir. Frequência alta é sinal de antecipação — não esperar o problema chegar.

---

## Referências confiáveis

- [Meta — Advantage+ Shopping Campaigns](https://www.facebook.com/business/help/914643779141416) — verificado 2026-05-01
- [Meta — Regras automáticas](https://www.facebook.com/business/help/1811448162422593) — verificado 2026-05-01
- [Meta — Testes A/B](https://www.facebook.com/business/help/1159714227408116) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [meta-ads-otimizacao.changelog.md](meta-ads-otimizacao.changelog.md)
