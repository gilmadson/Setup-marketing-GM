# Outros Canais: SMS e WhatsApp Marketing

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 04-outros-canais

---

## Quando usar / Quando não usar

**Usar quando:**
- Follow-up de lead quente — WhatsApp converte leads que o email não consegue (taxa de abertura ~90%)
- Carrinho abandonado em e-commerce — mensagem 1h após abandono, quando o usuário ainda lembra
- Reengajamento de base existente com opt-in confirmado
- Lembretes de evento, consulta ou prazo — alta taxa de leitura garante que o usuário saiba

**Não usar quando:**
- Sem opt-in explícito do usuário — ilegal (LGPD), risco de bloqueio do número e ban da API
- Mensagem sem valor claro para o receptor — spam no WhatsApp destrói a relação permanentemente
- Substituir email para conteúdo longo — WhatsApp é canal de mensagens curtas e diretas

---

## Pré-requisitos

```
- Número de telefone dedicado para WhatsApp Business (não usar número pessoal)
- Opt-in documentado: prova de que o usuário autorizou receber mensagens
- Para disparos em massa: WhatsApp Business API (não o app convencional)
- Ferramenta de disparo com API oficial: Take Blip, Zendesk, Twilio, Brevo, RD Station CRM
- Templates de mensagem aprovados pelo Meta antes de usar (para WhatsApp API)
- Para SMS: plataforma de SMS (Zenvia, Infobip, Twilio) com shortcode ou número longo
```

---

## Padrões e convenções

### WhatsApp Business App vs WhatsApp Business API

```
WhatsApp Business APP (gratuito):
  → Para: pequenos negócios, atendimento manual, até ~100 conversas/dia
  → Broadcast: máx 256 contatos por lista, apenas quem salvou o número recebe
  → Limitação: não permite automações nem disparo em massa real
  → Usar para: atendimento humano, resposta a leads, pequenas campanhas manuais

WhatsApp Business API (pago):
  → Para: escala, automação, disparo em massa, integração com CRM
  → Permite: templates aprovados, chatbots, integração com sistemas
  → Acesso via: BSP (Business Solution Provider) — parceiros autorizados pelo Meta
  → BSPs recomendados no Brasil: Take Blip, Zenvia, Twilio, Brevo, RD Station
  → Custo: cobrado por conversa (janela de 24h) — Marketing, Utilidade, Autenticação

Categorias de mensagem (API) e preços:
  Marketing: mensagem proativa de oferta, promoção — custo mais alto (~R$ 0,15-0,25/conversa)
  Utilidade: confirmação de pedido, lembrete de agendamento, atualização de status — custo médio
  Autenticação: OTP, verificação de conta — custo mais baixo
  Serviço: resposta a mensagem do usuário em até 24h — custo mais baixo (usuário iniciou)
```

### Templates aprovados pelo Meta — como criar

```
O que é:
  → Mensagens pré-aprovadas pelo Meta para envio proativo (quando você inicia a conversa)
  → Sem template aprovado: não pode iniciar conversa com usuário pela API

Janela de 24h:
  → Quando o USUÁRIO envia mensagem: abre janela de 24h para conversa livre (sem template)
  → Quando você inicia OU a janela fecha: usar template aprovado obrigatoriamente

Processo de aprovação:
  1. Criar template na plataforma BSP (Take Blip, Zenvia, etc.)
  2. Definir categoria: Marketing / Utilidade / Autenticação
  3. Escrever o texto com variáveis: "Olá {{1}}, seu pedido {{2}} foi confirmado!"
  4. Submeter para revisão do Meta → prazo: algumas horas a 1-2 dias úteis
  5. Status: Aprovado / Rejeitado / Pendente

Regras para aprovação:
  → Não pode conter: linguagem enganosa, promessas falsas, conteúdo adulto
  → Deve ser claro e específico — templates vagos são rejeitados
  → Call to Action deve estar associado a botão oficial (não texto corrido)
  → Variáveis ({{1}}, {{2}}) devem fazer sentido no contexto

Exemplos de templates aprovados:
  Boas-vindas (Utilidade):
    "Olá {{1}}! Sua conta em {{2}} foi criada com sucesso. 
     Acesse: {{3}}
     Qualquer dúvida, responda esta mensagem."

  Carrinho abandonado (Marketing):
    "{{1}}, você deixou {{2}} no seu carrinho! 🛒
     Finalize sua compra antes que acabe:
     [botão: Completar pedido]"

  Lembrete de consulta (Utilidade):
    "Olá {{1}}, lembrando sua consulta amanhã às {{2}}.
     Confirme sua presença respondendo SIM ou CANCELAR."
```

### Opt-in — coleta legal e documentada

```
LGPD e termos do WhatsApp exigem opt-in explícito:

Como coletar opt-in válido:
  → Checkbox no formulário: "Aceito receber mensagens pelo WhatsApp"
     → Não pode ser pré-marcado — usuário deve marcar ativamente
  → Mensagem de confirmação: ao cadastrar, enviar "Responda SIM para confirmar"
  → WhatsApp Flow: formulário nativo dentro do WhatsApp
  → Atendimento: ao iniciar conversa no WhatsApp, pedir permissão para futuras mensagens

O que documentar:
  → Data e hora do opt-in
  → IP ou identificador do dispositivo
  → Texto exato que o usuário aceitou ("aceito receber promoções via WhatsApp")
  → Canal onde o opt-in foi coletado (formulário X, LP Y)

Opt-out fácil (obrigatório):
  → Toda mensagem de marketing deve ter forma clara de sair
  → Instrução: "Responda PARAR para não receber mais mensagens"
  → Implementar: ao receber "PARAR", remover automaticamente da lista de marketing
```

### Sequências de WhatsApp — estrutura e timing

```
Sequência de nutrição de lead B2C (produto R$ 200-2k):

  Mensagem 1 (imediato após lead):
    → Apresentação + entregar o prometido (link do material, acesso, etc.)
    → Tom: pessoal, caloroso — como se fosse alguém do time

  Mensagem 2 (dia 1 - se não respondeu):
    → Pergunta aberta: "Você conseguiu acessar? Tem alguma dúvida?"
    → Aguardar resposta — iniciar conversa humana se responder

  Mensagem 3 (dia 3):
    → Conteúdo de valor: dica relevante relacionada ao problema

  Mensagem 4 (dia 5):
    → Prova social: "Fulano tinha a mesma situação e em 30 dias..."
    → CTA: "Quer saber como funciona para o seu caso?"

Sequência de carrinho abandonado (e-commerce):
  Mensagem 1 (1h após abandono): lembrete simples + link direto para o carrinho
  Mensagem 2 (24h): superar objeção + oferecer suporte
  Mensagem 3 (72h): urgência (prazo/estoque) ou incentivo (frete grátis)

Horários recomendados (Brasil):
  Segunda a sexta: 8h-20h (evitar horário de almoço 12h-14h para melhor abertura)
  Sábado: 9h-14h
  Domingo e feriados: evitar (exceto para e-commerce com pico de compra)
  Nunca enviar: 22h-7h
```

### SMS — quando usar e como

```
SMS vs WhatsApp:
  → SMS não requer app instalado — maior alcance para públicos que não usam WhatsApp
  → Menor taxa de abertura que WhatsApp (~85% vs 90%)
  → Sem imagens, sem botões, sem rich media — texto puro
  → Mais barato por disparo que WhatsApp API em alguns cenários

Quando SMS faz sentido:
  → Autenticação OTP (código de verificação) — não depende de internet
  → Lembretes urgentes (médico, banco, prazo) — chega mesmo sem Wi-Fi
  → Público mais velho ou em regiões com menor penetração de WhatsApp
  → Backup quando WhatsApp não responde (falha do app)

Limites técnicos:
  → 1 SMS = 160 caracteres (GSM) ou 70 caracteres (Unicode — com acentos e emojis)
  → Mensagem > 160 chars: dividida em múltiplos SMS cobrados separadamente
  → Shortcode (número curto como 28013): mais confiável para disparos em massa
  → Número longo (celular normal): pode ser bloqueado por operadoras em alto volume

Ferramentas de SMS no Brasil:
  → Zenvia: plataforma BR com shortcode, boa entregabilidade
  → Infobip: global, suporte WhatsApp + SMS integrado
  → Twilio: API mais flexível, para times técnicos
```

---

## Templates prontos

### Sequência de follow-up de lead WhatsApp

```markdown
## Sequência WhatsApp — Lead [Produto] — [Etapa]

**Template Nome:** followup_lead_produto_v1
**Categoria:** Marketing
**Aprovado em:** [data]

---

Mensagem 1 (imediato):
"Oi {{1}}! 👋

Sou {{2}} da {{3}}.

Você acabou de baixar {{4}} — aqui está o link de acesso:
{{5}}

Qualquer dúvida, pode me chamar aqui mesmo. 😊"

[Botão de resposta rápida: "Recebi, obrigado!"]
[Botão de resposta rápida: "Tenho uma dúvida"]

---

Mensagem 2 (dia 1 — se não respondeu):
"{{1}}, conseguiu acessar o material?

Pergunto porque muita gente me diz que {{6}} era exatamente o que precisava — mas só depois de ter lido com calma.

Se precisar de algo, estou por aqui! 🙂"

---

Mensagem 3 (dia 3):
"{{1}}, uma dica rápida que vi fazer diferença para quem está no seu momento:

{{7}}

Se fizer sentido pro seu caso, me conta — posso aprofundar. 👇"
```

---

## Checklist de qualidade

- [ ] Opt-in documentado com data, hora e texto aceito (LGPD)
- [ ] Templates aprovados pelo Meta antes de disparar via API
- [ ] Opt-out implementado: "PARAR" remove da lista automaticamente
- [ ] Horário de disparo dentro da janela recomendada (8h-20h seg-sex)
- [ ] Sequência com no máximo 1 mensagem proativa por dia (não sobrecarregar)
- [ ] Diferença clara entre WhatsApp Business App (manual) e API (automação em escala)
- [ ] Processo de atendimento humano definido para quando o lead responde

---

## Armadilhas comuns

**Disparar sem opt-in:** enviar mensagem para lista de clientes que nunca autorizaram WhatsApp. Usuários denunciam como spam → número bloqueado pelo Meta → perda permanente do número.

**Usar WhatsApp Business App para disparo em massa:** app pessoal/business não é para broadcast em escala. Limite de 256 por lista, possibilidade de ban por comportamento suspeito. Usar API oficial.

**Template rejeitado sem investigar motivo:** Meta rejeita e o gestor resubmete o mesmo template. Ler o motivo da rejeição, ajustar o texto e resubmeter.

**Frequência alta de mensagens marketing:** enviar 3 mensagens de marketing em 1 semana para o mesmo usuário. Taxa de bloqueio e report explode. WhatsApp é canal de baixa frequência e alto valor.

**SMS com acentos sem calcular custo:** mensagem com "ção", "ã", "é" usa encoding Unicode = 70 chars por SMS. "Confirmação do pedido" (23 chars) = 1 SMS. Uma mensagem com 140 chars e acentos = 2 SMS cobrados. Calcular sempre.

---

## Referências confiáveis

- [Meta — WhatsApp Business API](https://developers.facebook.com/docs/whatsapp/) — verificado 2026-05-01
- [Meta — Políticas de mensagens do WhatsApp](https://www.whatsapp.com/legal/business-policy/) — verificado 2026-05-01
- [LGPD — Lei 13.709/2018](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [outros-sms-whatsapp.changelog.md](outros-sms-whatsapp.changelog.md)
