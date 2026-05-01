# Google Ads: YouTube e Video Ads

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 03-google-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- TOFU de awareness com storytelling visual — vídeo para construir marca e audiência
- Produto que precisa de demonstração ou explicação antes da compra
- Remarketing de vídeo — segmentar quem assistiu X% do vídeo com anúncio de conversão
- Budget >= R$ 100/dia disponível especificamente para vídeo

**Não usar quando:**
- Sem vídeo produzido — não improvisar com vídeo de baixa qualidade; prejudica a marca
- Budget limitado — priorizar Search e Meta antes de YouTube
- Produto com ciclo de compra imediato e simples — YouTube é canal de consciência, não de clique direto

---

## Pré-requisitos

```
- Canal do YouTube criado e vinculado ao Google Ads
- Vídeo publicado no YouTube (público ou não listado) — não subir direto no Ads Manager
- Google Ads vinculado ao GA4 com conversões configuradas
- Tag do Google Ads instalada no site (para remarketing de vídeo)
- Vídeo com mínimo de qualidade: resolução 1080p, áudio limpo, hook nos primeiros 5 segundos
```

---

## Padrões e convenções

### Formatos de anúncio — quando usar cada um

```
IN-STREAM SKIPPABLE (mais comum):
  → Usuário pode pular após 5 segundos
  → Duração: mín 12s (recomendado 15-60s para conversão, até 3min para MOFU)
  → Cobrança: CPV — você paga quando usuário assiste 30s ou até o fim (o que vier primeiro)
  → Posição: antes, durante ou depois de vídeos no YouTube e sites da GDN
  → Usar para: TOFU (brand), MOFU (educação), BOFU com depoimento/oferta
  → Métrica principal: View Rate (% que assistiu os 30s), CPV, VTR

IN-STREAM NON-SKIPPABLE:
  → Usuário NÃO pode pular — assiste obrigatoriamente
  → Duração: máx 15-20 segundos (depende do mercado)
  → Cobrança: CPM (por mil impressões)
  → Usar para: mensagem de marca curta e concisa que precisa ser vista inteira
  → Cuidado: criativo fraco neste formato prejudica a experiência — usuário fica irritado

BUMPER ADS:
  → Vídeo não pulável de até 6 segundos
  → Cobrança: CPM
  → Usar para: reforço de marca após campanha maior, frequência de recall
  → Estratégia: bumper como "fechamento" de sequência (viu o in-stream longo → bumper reforça)
  → Limitação: muito curto para explicar algo — só para reconhecimento e recall

IN-FEED VIDEO (Discovery):
  → Aparece nos resultados de busca do YouTube, sidebar, página inicial
  → Formato: thumbnail + título — usuário clica para assistir
  → Cobrança: CPV (quando o usuário clica e começa a assistir)
  → Usar para: MOFU — usuário está navegando, não interrompido
  → Ideal para: tutoriais, reviews, conteúdo educacional mais longo
  → Sem limite de duração — pode ser vídeo de 10 minutos

MASTHEAD (reserva — grandes budgets):
  → Banner na página inicial do YouTube por 24h
  → Reservado via equipe de vendas do Google — não disponível no Ads Manager padrão
  → Usar para: lançamentos, campanhas nacionais de grandes marcas
```

### Targeting — segmentação no YouTube

```
1. Keywords (palavras-chave de vídeo):
   → Anúncio aparece em vídeos cujo conteúdo contém as keywords
   → Diferente de Search — aqui a keyword é do CONTEÚDO do vídeo, não da busca do usuário
   → Exemplo: anunciar em vídeos sobre "marketing digital" para produto de gestão de campanhas

2. Topics (tópicos):
   → Categorias de conteúdo do YouTube (Negócios, Tecnologia, Saúde, etc.)
   → Menos preciso que keywords — maior volume, menor relevância

3. Placements (posicionamentos):
   → Canal específico do YouTube: aparecer em todos os vídeos de um canal
   → Vídeo específico: aparecer antes de 1 vídeo específico
   → Usar quando: conhece exatamente o canal que seu público assiste

4. Audience Segments (audiências):
   → In-Market: usuários identificados pelo Google como em busca ativa
   → Custom Intent: criados a partir de keywords pesquisadas no Google
   → Affinity: interesses de longo prazo
   → Customer Match: lista de e-mails de clientes
   → Remarketing de vídeo: quem assistiu X% dos seus vídeos

5. Demographics:
   → Idade, gênero, status parental, renda familiar
   → Menos preciso no YouTube — muitos usuários não logados ou com dados desconhecidos

Targeting combinado (mais eficiente):
  → In-Market + Keywords contextuais: mais preciso que cada um separado
  → Placement + Audience: aparecer num canal específico E só para a audiência certa
```

### Estrutura ABCD — criativo de vídeo que converte

```
Framework ABCD do Google para vídeos de alta performance:

A — Attract (primeiros 5 segundos — antes do botão pular):
  → Hook que prende antes do botão "Pular anúncio" aparecer
  → Técnicas: pergunta direta, afirmação surpreendente, rosto olhando para câmera, movimento
  → Erro fatal: logo da empresa nos primeiros 5 segundos — o usuário pula
  → Exemplos de hook:
     "Você está jogando dinheiro fora em anúncios?" (pergunta)
     "3 erros que 90% das lojas cometem no Meta Ads" (curiosidade)
     "Isso me custou R$ 50.000" (surpresa)

B — Brand (primeiros 5-10 segundos):
  → Mencionar a marca após o hook — não antes
  → Pode ser visual (logo no canto) ou verbal ("aqui na [Empresa]...")
  → Não interromper o hook com branding

C — Connect (meio do vídeo):
  → Conectar a marca à dor ou desejo da persona
  → Mostrar o problema claramente → apresentar a solução
  → Prova social: depoimento, número de clientes, caso de sucesso

D — Direct (final — CTA):
  → Call to Action claro e específico
  → Verbal: "Acesse o link na descrição agora"
  → Visual: botão de CTA no próprio vídeo (overlay CTA no Ads Manager)
  → Criar urgência: "Oferta válida até domingo", "Vagas limitadas"

Duração por objetivo:
  TOFU Brand Awareness: 15-30s (prender e lembrar)
  MOFU Consideration: 60-120s (explicar, educar, mostrar resultado)
  BOFU Conversion: 30-60s (depoimento + oferta + CTA)
```

### Remarketing de vídeo — sequência de anúncios

```
Por que sequência:
  → Contar uma história em múltiplos vídeos — aumenta lembrança e intenção
  → Usuário vê vídeo 1 → recebe vídeo 2 → recebe vídeo 3 → converte

Exemplo de sequência de 3 etapas:

  Vídeo 1 (TOFU — 60s):
    → "Você tem esse problema?" — apresentar o problema
    → Target: In-Market + Keywords contextuais
    → Quem assistiu 50%+ avança para vídeo 2

  Vídeo 2 (MOFU — 90s):
    → "Como resolvemos o problema" — apresentar a solução
    → Target: Audience de quem assistiu 50%+ do vídeo 1
    → Quem assistiu 75%+ avança para vídeo 3

  Vídeo 3 (BOFU — 30s):
    → "Depoimento de cliente + oferta" — converter
    → Target: Audience de quem assistiu 75%+ do vídeo 2
    → CTA direto com urgência

Como criar Audience de visualização:
  → Google Ads → Ferramentas → Gerenciador de audiências → Criar
  → Fonte: Vídeos do YouTube → Visualizou [vídeo específico] → [X]% ou mais
  → Usar como target do próximo vídeo na sequência
```

### Métricas de YouTube Ads

```
View Rate (VTR):
  → % de usuários que assistiram o vídeo sem pular (vs quem pulou)
  → Benchmark: > 25% para in-stream skippable (varia muito por nicho e criativo)
  → VTR baixo: hook fraco ou público errado

CPV — Custo por Visualização:
  → Quanto você paga por cada visualização de 30s+
  → Benchmark: R$ 0,10–0,50/view (varia por nicho e competitividade)

Impressions e Reach:
  → Para TOFU — quantas pessoas únicas viram pelo menos 1 segundo

Earned Views:
  → Visualizações orgânicas geradas pelo engajamento com o anúncio (usuário clicou no canal)
  → Sinal de que o vídeo gerou interesse genuíno

Brand Lift (via Google):
  → Pesquisa automática do Google para medir aumento de recall, awareness e favorabilidade
  → Disponível para campanhas com budget > USD 1.000 por 2+ semanas
  → Resultado: % de lift em recall entre quem viu vs quem não viu o anúncio
```

---

## Templates prontos

### Brief de vídeo para YouTube Ads

```markdown
## Brief de Vídeo — [Nome do Anúncio]

**Formato:** In-Stream Skippable / Non-Skippable / Bumper / In-Feed
**Duração:** [X segundos]
**Etapa do funil:** TOFU / MOFU / BOFU

### ABCD

**A — Attract (0 a 5s):**
[Descrever a cena e o texto de hook — o que aparece antes do botão "pular"]

**B — Brand (5 a 10s):**
[Como a marca aparece — visual ou verbal]

**C — Connect (10s até penúltimos 5s):**
[Estrutura do meio: problema → solução → prova social]

**D — Direct (últimos 5-10s):**
[CTA verbal + CTA visual — o que o usuário deve fazer]

### Targeting
- Formato: [in-stream / in-feed]
- Audience: [interesses + In-Market + remarketing]
- Placements: [canal específico / youtube geral / GDN]

### KPI de sucesso
- View Rate meta: [%]
- CPV meta: R$ [valor]
- Conversão esperada: [para in-stream BOFU]
```

---

## Checklist de qualidade

- [ ] Vídeo publicado no YouTube antes de criar campanha (não subir pelo Ads Manager)
- [ ] Hook nos primeiros 5 segundos — não abre com logo
- [ ] Legendas adicionadas ao vídeo (CC no YouTube Studio)
- [ ] CTA overlay configurado no Ads Manager (botão clicável sobre o vídeo)
- [ ] Targeting definido por camada (audience + contextual)
- [ ] Frequency cap configurada para campanhas de awareness
- [ ] Audience de visualização criada para remarketing sequencial

---

## Armadilhas comuns

**Abrir com logo ou marca:** usuário não tem contexto, pula em 2 segundos. Hook precede branding — sempre. Marca aparece após capturar atenção.

**Vídeo de qualidade ruim:** áudio com barulho, imagem tremida, iluminação ruim. YouTube é plataforma visual — vídeo ruim prejudica a percepção da marca mais do que nenhum anúncio.

**Não criar audience de visualização:** rodar in-stream sem criar audiência de quem assistiu para remarketing. Perde o canal mais quente de remarketing de vídeo.

**CPV sem VTR:** focar em CPV baixo ignorando que VTR caiu. CPV baixo com VTR 5% = público vendo o hook e pulando. Priorizar VTR — se baixo, o criativo ou o targeting está errado.

**In-stream não skippable com criativo fraco:** usuário é forçado a assistir 15s de anúncio ruim → associação negativa com a marca. Non-skippable exige criativo de alta qualidade.

---

## Referências confiáveis

- [Google — Formatos de anúncio em vídeo](https://support.google.com/google-ads/answer/2375497) — verificado 2026-05-01
- [Google — Framework ABCD](https://www.thinkwithgoogle.com/intl/pt-br/estrategias-de-marketing/video/abcd-framework/) — verificado 2026-05-01
- [Google — Remarketing de vídeo](https://support.google.com/google-ads/answer/2545661) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [google-youtube.changelog.md](google-youtube.changelog.md)
