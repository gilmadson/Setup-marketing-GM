# SEO: Off-page e Link Building

**Versão:** 1.0.0 | **Atualizada em:** 2026-05-01
**Categoria:** 07-seo-organico

---

## Quando usar / Quando não usar

**Usar quando:**
- Site com bom conteúdo mas não rankeia — faltam backlinks para dar autoridade
- Nicho competitivo onde concorrentes têm muito mais backlinks
- Lançamento de novo domínio que precisa de autoridade para sair do zero

**Não usar quando:**
- Site com problemas técnicos não resolvidos (ver seo-tecnico) — backlinks em site quebrado são desperdício
- Conteúdo fraco — link building em conteúdo raso não sustenta ranking
- Estratégias de compra de links em massa — risco de penalidade manual do Google

---

## Pré-requisitos

```
- Conteúdo de qualidade publicado (link building sem conteúdo é construir em areia)
- Ferramenta de análise de backlinks: Ahrefs, SEMrush ou Moz (pago) ou Ubersuggest (limitado)
- Google Search Console — monitorar links recebidos gratuitamente
- Domínio verificado no Search Console (para disavow se necessário)
```

---

## Padrões e convenções

### Métricas de autoridade — o que medir

```
Domain Rating / Domain Authority:
  Ahrefs DR (Domain Rating):
    → Score 0-100 baseado no perfil de backlinks do domínio
    → Quanto maior, mais difícil de ranquear é um site com menos DR
    → DR 0-20: site novo, pouca autoridade
    → DR 20-40: autoridade média, consegue ranquear para KD até 40
    → DR 40-60: boa autoridade
    → DR 60+: site de referência no nicho

  Moz DA (Domain Authority):
    → Métrica similar, escala 0-100
    → Menos usada que o DR do Ahrefs hoje

  URL Rating (UR) — Ahrefs:
    → Autoridade de uma URL específica (não do domínio inteiro)
    → Útil para analisar páginas individuais que você quer superar

Qualidade de um backlink — o que importa:
  → Relevância: link de site do mesmo nicho vale muito mais que link aleatório
  → DR/DA do domínio que linka: link de DR 70 > 10 links de DR 10
  → Posição na página: link no corpo do texto > link no rodapé/barra lateral
  → Texto âncora: âncora relevante ("agência de tráfego pago") > âncora genérica ("clique aqui")
  → DoFollow vs NoFollow:
      DoFollow: transfere link equity (PageRank) → mais valioso para SEO
      NoFollow: não transfere link equity diretamente, mas ainda pode gerar tráfego e brand signal
      Sponsored: obrigatório para links pagos (posts patrocinados, press releases pagos)
      UGC (User Generated Content): para fóruns e comentários

Toxic links:
  → Links de sites de spam, PBN (Private Blog Networks), diretórios de baixa qualidade
  → Podem prejudicar o ranking se em grande volume
  → Verificar: Ahrefs Site Explorer → Backlinks → filtrar por DR < 10 e analisar
  → Ação: disavow file (ver abaixo) — raramente necessário para penalidades orgânicas, obrigatório após penalidade manual
```

### Técnicas de link building — do mais ao menos eficaz

```
1. DIGITAL PR (mais escalável, maior autoridade):
  → Criar conteúdo noticiável que jornalistas/blogs queiram citar
  → Tipos: pesquisa original com dados (enquete, estudo), ferramentas gratuitas, infográfico exclusivo, opinião especialista em tendência
  → Processo:
     → Criar o conteúdo/estudo
     → Identificar jornalistas que cobrem o tema (ferramenta: Hunter.io para emails)
     → Enviar pitch personalizado (2-3 parágrafos, por que é relevante para a audiência deles)
  → Resultado esperado: 1-5 links de alta qualidade por campanha
  → Exemplo: "Estudo: CPL de tráfego pago no Brasil por setor em 2026" → publicado por portais de marketing

2. GUEST POST (eficaz, requer reciprocidade):
  → Escrever artigo para outro blog/site do nicho com link de volta
  → Processo:
     → Identificar sites com DA relevante e audiência alinhada
     → Verificar se aceitam guest posts (procurar "escreva para nós" ou contato editorial)
     → Propor pauta (angle que gere valor para a audiência deles, não marketing próprio)
     → Link no artigo: 1-2 links contextuais para conteúdo relevante do seu site
  → O que evitar: links óbvios de autopromoção, guest posts em sites sem audiência real, fazendas de conteúdo
  → Benchmark: 2-4 guest posts/mês para site em crescimento

3. BROKEN LINK BUILDING:
  → Encontrar links quebrados (404) em sites relevantes e sugerir seu conteúdo como substituto
  → Processo com Ahrefs:
     → Site Explorer → Broken links de um concorrente
     → Ou: Content Explorer → filtrar por nicho → analisar backlinks com links quebrados
     → Contatar o webmaster: "Vi que o link X está quebrado — tenho conteúdo similar que pode substituir"
  → Taxa de resposta: 5-15%
  → Vantagem: o webmaster já quer o link corrigido — proposta de baixo atrito

4. HARO (Help A Reporter Out) — agora: Connectively:
  → Plataforma onde jornalistas publicam pedidos de fontes para suas matérias
  → Cadastro como fonte → receber emails 3x/dia com pedidos de comentários
  → Responder pitches relevantes com opinião especialista → jornalista cita e linka
  → Bons para: links em sites de grande autoridade (Forbes, G1, Folha, portais de nicho)
  → Limitação: requer monitoramento diário e respostas rápidas (horas, não dias)

5. MENÇÕES SEM LINK (brand mentions):
  → Sites que mencionam sua marca sem linkar — converter em link
  → Processo: Google Alerts com o nome da marca ou Ahrefs Alerts → identificar menções
  → Contatar: "Vi que mencionaram [empresa] — consegue adicionar o link? [URL]"
  → Taxa de resposta: 20-40% — já admiram a marca, é favor pequeno

6. LINK BUILDING POR PARCERIA:
  → Fornecedores, clientes, parceiros — pedir para linkar no site deles
  → Depoimentos: dar depoimento para fornecedor em troca de link para o seu site (prática comum)
  → Associações do setor: listar empresa em diretórios de associações profissionais
  → Requer: relacionamento existente, proposta de valor clara para eles

7. CONTEÚDO "LINKÁVEL" (Link Magnets):
  → Criar conteúdo que naturalmente atrai links sem outreach ativo
  → Tipos que geram mais links naturais:
     → Dados originais e pesquisas do setor
     → Ferramentas gratuitas online
     → Guias definitivos (conteúdo pilar extenso)
     → Recursos únicos (glossários, coleções de templates)
     → Estudos de caso com resultados reais
```

### Brand Signals — SEO além dos links

```
O que são brand signals:
  → Sinais que indicam ao Google que a marca é real, conhecida e confiável
  → Google usa esses sinais para avaliar autoridade mesmo sem link direto

Tipos de brand signals:
  → Buscas pela marca: pessoas buscando "nome da empresa" diretamente
  → Menções não linkadas: texto com o nome da empresa em outros sites
  → Presença em redes sociais com audiência real
  → Perfil verificado no Google Business Profile (para locais)
  → Wikipedia/Wikidata (para marcas grandes)
  → Reviews no Google, Reclame Aqui, Glassdoor

Como construir:
  → Campanhas de awareness (mesmo pagas) que geram buscas pela marca
  → PR tradicional: menções em mídia geram brand signals
  → Experiência do cliente excelente → reviews espontâneos
  → Redes sociais ativas com audiência engajada
```

### Disavow file — quando e como usar

```
O que é:
  → Arquivo txt submetido ao Google Search Console informando quais links ignorar
  → Google "desvincula" esses backlinks do perfil do site

Quando usar:
  → Após penalidade manual por "links não naturais" (notificação no Search Console)
  → Site com histórico de link building black hat (compra de links em massa)
  → Perfil de backlinks dominado por links de spam que não se consegue remover

Quando NÃO usar:
  → Para links ruins aleatórios que todo site recebe — Google já ignora naturalmente
  → Como medida preventiva sem penalidade — pode remover links bons por engano

Formato do arquivo:
  # Comentário explicando o motivo
  domain:spam-site.com          ← desavow domínio inteiro
  https://spam.com/pagina       ← desavow URL específica

Submissão:
  → Search Console → Disavow Tool (URL direta: search.google.com/search-console/disavow-links)
  → Efeito: semanas a meses para Google reprocessar

Cuidado:
  → Disavow é permanente até você remover o arquivo
  → Disavowar links bons por engano = perda de autoridade
  → Processo correto: primeiro tentar contatar o webmaster para remover o link; disavow é último recurso
```

### Análise de concorrentes — encontrar oportunidades

```
Processo com Ahrefs/SEMrush:

  1. Identificar concorrentes que ranqueiam para suas keywords-alvo
  2. Site Explorer → Backlinks do concorrente
  3. Filtrar: DoFollow | DR do linking site > 20 | Relevante ao nicho
  4. Classificar oportunidades:
     → Sites que aceitam guest posts → pitch de conteúdo
     → Sites com menções de concorrentes sem menção da sua marca → outreach de brand mention
     → Sites com links quebrados apontando para concorrente → broken link building
     → Diretórios onde concorrente está listado → cadastrar também

Content Gap (gap de keywords):
  → Ahrefs: Site Explorer → Content Gap → inserir domínios dos concorrentes
  → Resultado: keywords em que concorrentes ranqueiam mas você não
  → Priorizar: keywords de alta intenção comercial com KD viável
```

---

## Templates prontos

### Template de outreach para guest post

```
Assunto: [Nome do seu blog] — proposta de conteúdo para [nome do blog deles]

Olá [Nome],

Acompanho o [Nome do blog] há algum tempo — principalmente os artigos sobre [tópico específico].

Sou [cargo/especialidade] na [empresa] e trabalho com [nicho] há [X] anos. Gostaria de propor um artigo exclusivo para vocês sobre [tema], que ainda não vi coberto em profundidade no blog de vocês.

3 ângulos possíveis:
1. [Ângulo 1 — dado ou perspectiva específica]
2. [Ângulo 2]
3. [Ângulo 3]

Tenho experiência escrevendo para [mencionar 1-2 publicações anteriores se houver].

Faz sentido conversarmos sobre isso?

[Nome]
[Link do seu site / LinkedIn]
```

---

## Checklist de qualidade

- [ ] Perfil de backlinks analisado mensalmente (Ahrefs ou Search Console)
- [ ] Nenhum link de compra em volume (risco de penalidade manual)
- [ ] Texto âncora variado (não repetir sempre a mesma âncora exata)
- [ ] Mix saudável: DoFollow + NoFollow (perfil natural tem ambos)
- [ ] Backlinks relevantes ao nicho priorizados sobre backlinks genéricos
- [ ] Google Alerts com nome da marca configurado para monitorar menções
- [ ] Links de concorrentes analisados trimestralmente para oportunidades

---

## Armadilhas comuns

**Comprar links em massa:** 100 links comprados por R$ 300 em fazendas de conteúdo. DR dos sites = 5. Risco alto de penalidade manual. Google cada vez mais eficiente em identificar padrões de link building artificial. Resultado: perda de ranking ou remoção do índice.

**Texto âncora exato demais:** todo backlink com âncora "agência de tráfego pago em São Paulo". Perfil antinatural — sinal de link building artificial. Variar âncoras: marca, URL nua, âncoras parciais, âncoras genéricas.

**Guest posts em farms:** postar em dezenas de sites sem audiência real, DR baixo, que aceitam qualquer conteúdo. Google desvaloriza e pode penalizar. Preferir 2 guest posts em sites relevantes a 20 em farms.

**Ignorar links internos:** focar todo esforço em backlinks externos e esquecer que links internos também distribuem autoridade. Páginas estratégicas precisam receber links internos de páginas com mais autoridade.

**Disavow preventivo:** remover links bons junto com ruins "por precaução". Resultado: queda de ranking sem motivo. Disavow só com penalidade manual confirmada ou perfil completamente contaminado por black hat histórico.

---

## Referências confiáveis

- [Google — Link Schemes (o que é proibido)](https://developers.google.com/search/docs/essentials/spam-policies#link-spam) — verificado 2026-05-01
- [Ahrefs — Link Building Guide](https://ahrefs.com/blog/link-building/) — verificado 2026-05-01
- [Google — Disavow Links Tool](https://support.google.com/webmasters/answer/2648487) — verificado 2026-05-01

---

## Versão e histórico
→ Ver [seo-offpage.changelog.md](seo-offpage.changelog.md)
