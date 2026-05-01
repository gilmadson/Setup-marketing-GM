# Meta Ads: Pixel e Conversions API

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 02-meta-ads

---

## Quando usar / Quando não usar

**Usar quando:**
- Configurando qualquer campanha de conversão no Meta Ads — sem rastreamento, o algoritmo não aprende
- Campanha com CPL ou CPA alto inexplicável — dados de conversão podem estar incompletos
- Escala de budget — Conversions API reduz perda de dados e melhora o algoritmo

**Não usar quando:**
- Campanha apenas de alcance/awareness sem conversão no site — Pixel não é necessário
- Anunciando apenas Lead Ads (formulário nativo do Meta) — Meta rastreia internamente sem Pixel

---

## Pré-requisitos

```
- Acesso ao Business Manager com permissão de administrador
- Acesso ao site (para instalar Pixel) — via GTM, plugin WordPress ou código direto
- Para Conversions API: acesso ao servidor ou backend da aplicação
- Para e-commerce: plataforma com integração nativa (Shopify, WooCommerce, VTEX, Nuvemshop)
```

---

## Padrões e convenções

### Pixel — instalação e eventos padrão

```
Código base do Pixel:
  → Copiar do Events Manager → Pixel → Configurar → Instalar manualmente
  → Colar ANTES do </head> em todas as páginas do site
  → 1 Pixel por conta de anúncios (não criar múltiplos Pixels para o mesmo site)

Via Google Tag Manager (recomendado):
  1. Criar tag "Meta Pixel — Base Code" com o código base
  2. Trigger: All Pages
  3. Criar tags de eventos específicos com triggers de página ou clique
  → Vantagem: não precisa mexer no código do site para cada evento novo

Eventos padrão — lista por prioridade:

  PageView (automático no código base):
    → Disparado em toda página vista
    → Parâmetros: nenhum obrigatório

  ViewContent:
    → Quando: usuário vê página de produto, serviço ou conteúdo específico
    → Parâmetros: content_ids, content_type, value, currency

  AddToCart:
    → Quando: usuário adiciona item ao carrinho
    → Parâmetros: content_ids, content_type, value, currency

  InitiateCheckout:
    → Quando: usuário inicia processo de checkout
    → Parâmetros: value, currency, num_items

  Purchase:
    → Quando: compra concluída — página de confirmação/obrigado
    → Parâmetros OBRIGATÓRIOS: value, currency
    → Parâmetros recomendados: content_ids, content_type, order_id

  Lead:
    → Quando: usuário preenche formulário, cadastra e-mail, faz cadastro
    → Parâmetros recomendados: value, currency (se CPL definido)

  CompleteRegistration:
    → Quando: cadastro completo em plataforma/app
    → Parâmetros: status

  Contact / Schedule / FindLocation:
    → Quando: clique em WhatsApp, agendamento, busca de loja

Parâmetro event_id:
  → ID único para cada evento disparado (ex: UUID ou timestamp + user_id)
  → Obrigatório para deduplicação com Conversions API
  → Garantir que Pixel e CAPI enviem o MESMO event_id para o mesmo evento
```

### Conversions API (CAPI) — por que e como

```
Por que usar CAPI além do Pixel:
  → iOS 14+ e navegadores bloqueiam cookies — Pixel perde 20-40% dos eventos
  → CAPI envia dados diretamente do servidor para o Meta — não depende de browser
  → Combinação Pixel + CAPI = máxima cobertura de dados → melhor algoritmo → menor CPA

Funcionamento:
  Pixel (browser) → Meta
  CAPI (servidor) → Meta
  Deduplicação via event_id → Meta conta apenas 1 evento, não 2

Configurações de CAPI:

  1. Integração nativa (mais fácil):
     → Shopify: Meta Sales Channel nativo
     → WooCommerce: plugin oficial Meta Pixel
     → Nuvemshop/VTEX: integração nativa no painel
     → LINX, Tray: verificar integração disponível

  2. Via API direta (para desenvolvedores):
     Endpoint: POST https://graph.facebook.com/v19.0/{pixel_id}/events

     Estrutura mínima de um evento Purchase via CAPI:
     {
       "data": [{
         "event_name": "Purchase",
         "event_time": 1714569600,          // Unix timestamp
         "event_id": "order_123_uuid",       // MESMO id que o Pixel enviou
         "action_source": "website",
         "user_data": {
           "em": ["hash_sha256_do_email"],   // e-mail com hash SHA-256
           "ph": ["hash_sha256_do_telefone"],// telefone com hash
           "client_ip_address": "177.x.x.x",
           "client_user_agent": "Mozilla/5..."
         },
         "custom_data": {
           "currency": "BRL",
           "value": 297.00,
           "order_id": "123",
           "content_ids": ["SKU-456"],
           "content_type": "product"
         }
       }],
       "access_token": "EAAx..."
     }

  3. Via Google Tag Manager Server-Side:
     → GTM Server-Side funciona como proxy entre browser e Meta
     → Opção intermediária — não exige backend próprio, mas precisa de container server-side

Hashing obrigatório de dados de usuário:
  → email, phone, first_name, last_name, city, zip, country → SHA-256 em minúsculo, sem espaços
  → Meta exige hashing para proteger dados pessoais (LGPD)
  → Nunca enviar PII sem hash para a API
```

### Event Match Quality (EMQ) — melhorar a correspondência

```
O que é:
  → Score de 0 a 10 que indica com que precisão o Meta consegue associar o evento a um usuário
  → Maior EMQ = mais eventos atribuídos = CPA aparente menor = algoritmo aprende melhor

Como EMQ é calculado:
  → Cada sinal de usuário enviado contribui para o score
  → Sinais de maior impacto: email (maior), phone, external_id
  → Sinais de menor impacto: IP, user_agent, click_id (fbclid)

Como melhorar o EMQ:
  1. Capturar email e/ou telefone no formulário → enviar com hash no evento
  2. Adicionar fbclid à URL e capturar como parâmetro → enviar no evento
     → fbclid = parâmetro que o Meta adiciona automaticamente nos cliques de anúncio
  3. external_id: ID único do usuário no sistema (userId do CRM, por exemplo)
  4. Login na plataforma: se usuário logado, ter email disponível para enviar

Meta de EMQ: >= 7.0 (bom), >= 8.5 (excelente)
```

### Verificação e diagnóstico

```
Ferramentas de teste:
  1. Meta Pixel Helper (extensão Chrome):
     → Mostra quais eventos estão disparando na página em tempo real
     → Identifica erros de configuração (evento sem parâmetros obrigatórios, Pixel não encontrado)

  2. Test Events (no Events Manager):
     → Events Manager → Pixel → Test Events
     → Cola a URL do site → acessa via link de teste → eventos aparecem em tempo real
     → Usar para validar Pixel E CAPI antes de lançar campanha

  3. Events Manager → Atividade:
     → Mostra volume de eventos nas últimas 24h-7d
     → Compara Pixel vs CAPI (deduplicado) vs total
     → Alerta se evento diminuiu significativamente (possível quebra)

Sinais de problema:
  → Pixel Helper mostra "Pixel não encontrado": código base não instalado ou em conflito com GTM
  → Evento sem parâmetros: Purchase sem value/currency → não otimiza lances de valor
  → EMQ < 5: poucos sinais de usuário sendo enviados → adicionar email/phone
  → Deduplicação não funcionando: event_id diferente entre Pixel e CAPI → mesmo ID, mesmo evento
```

---

## Templates prontos

### Checklist de instalação do Pixel + CAPI

```markdown
## Configuração Pixel + CAPI — [Cliente/Projeto]

### Pixel Base
- [ ] Código base instalado em TODAS as páginas (antes do </head>)
- [ ] PageView disparando — confirmar com Pixel Helper
- [ ] Domínio verificado no Business Manager

### Eventos (Pixel lado do browser)
- [ ] ViewContent — página de produto/serviço
- [ ] Lead — página de obrigado / evento de submit do formulário
- [ ] Purchase — página de confirmação de pedido
- [ ] Parâmetros value e currency presentes no Lead e Purchase
- [ ] event_id único gerado e enviado em cada evento

### Conversions API (CAPI)
- [ ] Método de integração escolhido: [integração nativa / API direta / GTM Server-Side]
- [ ] Eventos espelhados no servidor: Lead + Purchase (mínimo)
- [ ] Hashing SHA-256 aplicado nos dados de usuário (email, phone)
- [ ] event_id IGUAL ao enviado pelo Pixel (deduplicação)
- [ ] Teste no Test Events: eventos chegando corretamente

### EMQ
- [ ] EMQ atual: [score] — meta >= 7.0
- [ ] Sinais enviados: [email ✅ / phone ✅ / fbclid ✅ / external_id ✅]
```

---

## Checklist de qualidade

- [ ] Pixel instalado antes de criar campanha de conversão
- [ ] Test Events validado — eventos chegando com parâmetros corretos
- [ ] CAPI configurado para os eventos de conversão principais (Lead, Purchase)
- [ ] event_id único e idêntico entre Pixel e CAPI (deduplicação)
- [ ] Dados de usuário com hash SHA-256 antes de enviar para a API
- [ ] EMQ >= 7.0 para os eventos de conversão
- [ ] Aumento de cobertura validado: Pixel standalone vs Pixel+CAPI no Events Manager

---

## Armadilhas comuns

**Pixel instalado mas sem eventos:** o código base (PageView) está lá mas os eventos de conversão (Lead, Purchase) não foram configurados. O algoritmo não sabe quem converteu.

**Purchase sem value/currency:** Meta não consegue otimizar por valor de compra (Value-Based Optimization). Sempre incluir esses parâmetros — mesmo que com valor fixo estimado.

**Sem deduplicação:** Pixel e CAPI enviando o mesmo evento com event_id diferentes. O Meta conta 2 conversões para 1 real → dados inflados → algoritmo aprende errado.

**Dados pessoais sem hash:** enviar email ou telefone em texto puro para a CAPI viola LGPD e os termos do Meta. Sempre SHA-256 antes de enviar.

**Não verificar após atualizações do site:** redesign ou migração de plataforma quebra o Pixel. Configurar monitoramento de volume de eventos no Events Manager com alerta automático.

---

## Referências confiáveis

- [Meta — Conversions API](https://developers.facebook.com/docs/marketing-api/conversions-api) — verificado 2026-05-01
- [Meta — Eventos padrão](https://developers.facebook.com/docs/meta-pixel/reference) — verificado 2026-05-01
- [Meta — Event Match Quality](https://www.facebook.com/business/help/765081237991473) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [meta-ads-pixel-api.changelog.md](meta-ads-pixel-api.changelog.md)
