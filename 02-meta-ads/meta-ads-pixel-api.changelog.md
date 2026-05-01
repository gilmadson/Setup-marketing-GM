# Changelog - Meta Ads: Pixel e Conversions API

## [1.0.0] - 2026-05-01
- Skill completa — instalação do Pixel base e configuração dos eventos padrão com parâmetros obrigatórios
- Eventos padrão: PageView, ViewContent, AddToCart, InitiateCheckout, Purchase, Lead — parâmetros e quando disparar
- Conversions API (CAPI): por que usar (iOS 14+), 3 métodos de integração (nativa, API direta, GTM Server-Side)
- Estrutura JSON completa de evento Purchase via CAPI com hashing SHA-256 dos dados de usuário
- Deduplicação via event_id: conceito, implementação e diagnóstico quando não funciona
- Event Match Quality (EMQ): o que é, como melhorar, sinais por impacto (email > phone > fbclid > IP), meta >= 7.0
- Ferramentas de verificação: Pixel Helper, Test Events, Events Manager — diagnóstico de problemas comuns
- Checklist de instalação Pixel + CAPI completo para uso em novos projetos

## [0.1.0] - 2026-05-01
- Criacao do esqueleto - estrutura padrao, conteudo a desenvolver
