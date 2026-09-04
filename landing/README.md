# Consultoria Premium — Collazo & Padial

Landing page de tráfego pago para a consultoria em conjunto de Victor Collazo
(treino) e Gabriela Padial (nutrição). Construída em cima dos 5 pilares de
alta conversão: foco exclusivo (sem menu nem links externos), alinhamento
com o anúncio, estrutura completa (headline, benefícios, quebra de
objeções, garantia, prova social), design simples de 3 cores e carregamento
rápido (HTML único, sem framework).

## Estrutura
- `index.html` — página completa (HTML + CSS inline no `<head>`, sem dependências além das Google Fonts)
- `images/` — fotos do casal usadas no hero, na seção de acompanhamento e no CTA final

## Identidade visual
- Paleta: bege (`#F7F4EE`), verde pinho (`#1F3D2B`), dourado (`#B99458`)
- Tipografia: Playfair Display (títulos), Cormorant Garamond (detalhes serifados), DM Sans (texto corrido)
- Sem travessões no texto (preferência do cliente)

## Decisões de conversão já tomadas
- **CTA único**: todos os botões (nav, hero, meio de página, oferta, final) levam para o mesmo WhatsApp — sem formulário de lead, sem menu de navegação, sem links de Instagram no rodapé.
- **Preço**: mostra só o valor de entrada (R$397 / 45 dias) como âncora; os planos mais longos são combinados no próprio WhatsApp, para não travar a decisão numa tabela grande.
- **Garantia**: ajuste ilimitado do protocolo até o fim do período, sem custo extra (compromisso real, não reembolso).

## Pendências conhecidas
- **Depoimento/prova social real**: a seção de garantia hoje é uma promessa da marca, não um depoimento — falta um depoimento ou fotos reais de aluno para reforçar prova social. Fotos foram prometidas e ainda não chegaram.
- **CREF/CRN reais**: hero ainda mostra "CREF" / "CRN" genérico; números reais foram prometidos e ainda não chegaram.
- **Velocidade/hospedagem**: página já é leve (HTML único + 3 fotos + Google Fonts), mas para tráfego pago vale comprimir as imagens antes de publicar e usar hospedagem com CDN.

## Como rodar localmente
Abra `index.html` direto no navegador, ou sirva com:
```
npx serve .
```
