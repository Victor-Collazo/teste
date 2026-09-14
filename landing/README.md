# Consultoria Premium — Collazo & Padial

Landing page de tráfego pago para a consultoria em conjunto de Victor Collazo
(treino) e Gabriela Padial (nutrição). Construída em cima dos 5 pilares de
alta conversão: foco exclusivo (sem menu nem links externos), alinhamento
com o anúncio, estrutura completa (headline, benefícios, quebra de
objeções, garantia, prova social), design simples de 3 cores e carregamento
rápido (HTML único, sem framework).

## Estrutura
- `index.html` — página completa (HTML + CSS inline no `<head>`, sem dependências além das Google Fonts)
- `images/` — fotos do casal. `hero-wide.jpg` é a foto do hero (veja abaixo); `hero.jpg` é o original em pé, ainda usado em nenhum lugar da página mas mantido caso sirva pra outra coisa; `phones.jpg` e `fun.jpg` seguem nas seções de acompanhamento e CTA final
- `favicon.svg` — selo "CP" usado como ícone da aba do navegador (mesmo desenho da marca no topo da página)

### `hero-wide.jpg`
A foto original do hero (`hero.jpg`) é vertical (1200×1800, retrato de estúdio). Para um hero horizontal sem distorcer o casal, `hero-wide.jpg` foi gerado a partir dela: recorte do excesso de fundo branco no topo, e o fundo de estúdio (liso, sem textura) estendido nas duas laterais a partir de uma amostra real da própria borda da foto — sem esticar nem distorcer as pessoas. Resultado: 2680×1500 (~16:9), sem costura visível. Script usado (Pillow) não foi versionado; se precisar refazer com outro recorte, é só pedir.

## Identidade visual
- Design escuro e editorial: verde profundo + dourado, inspirado em referências de nutrição/treino premium (selo circular, serifado clássico) e no formato de hero de landing pages fitness de alto padrão (badge + headline grande + dois CTAs)
- Paleta: verde escuro (`#10301D`), verde-oliva mais claro para faixas alternadas (`#17381F`), creme (`#F3EEDD` — só no cartão de oferta, como "plano em destaque"), dourado (`#C9A24B`) como único acento
- Tipografia: só duas famílias — Bodoni Moda (títulos serifados de alto contraste, itálico para ênfase e para o selo "CP") e Manrope (texto corrido, rótulos, botões). Fraunces e IBM Plex Mono foram removidos para simplificar.
- Hero em foto cheia (edge-to-edge) com o texto sobreposto: a foto recebe um tingimento verde-escuro (filtro + camada multiply) forte o bastante para o texto ficar legível em qualquer ponto da imagem, não só numa faixa de gradiente
- Fotos de apoio (acompanhamento, CTA final) sem moldura pesada — só um fio dourado sutil e sombra, para não competir com o fundo escuro
- Selo "CP" (bloco dourado sólido, letras em negativo, Bodoni Moda itálico) no nav, rodapé e na aba do navegador
- Sem travessões no texto (preferência do cliente)

## Decisões de conversão já tomadas
- **CTA duplo no hero**: botão principal (dourado, para o WhatsApp) + botão secundário fantasma ("Como funciona", rola até a seção de método) — o resto da página mantém CTA único pro WhatsApp.
- **Copy enxuta**: bullets de cada especialista reduzidos a 3 itens, quebra de objeções reduzida a 3 perguntas com respostas de 1 frase, textos de apoio mais curtos — menos texto, mesma estrutura de convite à conversão.
- **Preço**: mostra só o valor de entrada (R$397 / 45 dias) como âncora, em um cartão creme que se destaca do resto da página (como o plano "em destaque" da referência); planos mais longos são combinados no WhatsApp.
- **Garantia**: ajuste ilimitado do protocolo até o fim do período, sem custo extra (compromisso real, não reembolso).

## Pendências conhecidas
- **Depoimento/prova social real**: a seção de garantia hoje é uma promessa da marca, não um depoimento — falta um depoimento ou fotos reais de aluno. Fotos foram prometidas e ainda não chegaram.
- **CREF/CRN**: não aparecem mais no hero (cortados na limpeza de informação); se quiser reforçar autoridade, dá pra reintroduzir como uma linha pequena perto do nome de cada um na seção "O que você recebe".
- **Velocidade/hospedagem**: página já é leve (HTML único + 3 fotos + Google Fonts), mas para tráfego pago vale comprimir as imagens antes de publicar e usar hospedagem com CDN.

## Como rodar localmente
Abra `index.html` direto no navegador, ou sirva com:
```
npx serve .
```
