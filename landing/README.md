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
- `favicon.svg` — selo "CP" usado como ícone da aba do navegador (mesmo desenho da marca no topo da página)

## Identidade visual
- Design claro e editorial, inspirado em estúdios boutique de alto padrão (Equinox, Solo60, SIX) — clima de "clube privado", não de academia
- Paleta: papel claro (`#F2EFE6`), branco (`#FFFFFF`), bronze escuro (`#8B5A2E`) — único acento, escolhido escuro o bastante para ter contraste em texto sobre fundo claro
- Tipografia: Fraunces (títulos serifados), Manrope (texto corrido), IBM Plex Mono (rótulos, números de protocolo), Bodoni Moda itálico (só no selo "CP" — serifado de alto contraste, mais elegante, ainda legível em 16px)
- Fotos sem moldura: hero em imagem cheia (edge-to-edge, logo abaixo do bloco de texto), e as demais fotos aparecem soltas na página, só com uma sombra suave para se destacarem do fundo
- Selo "CP" (bloco bronze sólido, letras em negativo, Bodoni Moda itálico) no lugar do nome pessoal no topo da página, no rodapé e na aba do navegador — "Collazo & Padial" aparece como subtítulo discreto ao lado do nome da marca
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
