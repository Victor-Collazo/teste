# Content Intelligence Engine (MVP)

Ferramenta que analisa um conteúdo (vídeo/reel) que já performou bem, extrai o **mecanismo** por trás dessa performance (hook, retenção, gatilhos psicológicos, SEO social) e usa esse aprendizado para gerar **ideias originais** para o seu próprio nicho — sem copiar o conteúdo original.

Princípio central do sistema: **copie o aprendizado, não o conteúdo.**

## Como usar

Abra `app.html` em qualquer navegador — não precisa de servidor, build ou instalação. É um app 100% client-side: não existe backend, nada é enviado para nenhum servidor além da API oficial da Anthropic.

1. **Configuração:** cole sua própria API key da Anthropic (`sk-ant-...`). Ela fica salva só no `localStorage` do seu navegador e é usada para chamar a API diretamente do navegador.
2. **1. Analisar Conteúdo:** cole a transcrição/fala de um vídeo de referência (copiada manualmente por você — a ferramenta não baixa nem transcreve vídeos do Instagram/TikTok automaticamente). A ferramenta roda em sequência: Transcrição Estruturada → Autópsia Completa → DNA Estratégico → SEO Social.
3. **2. Gerar Ideias:** escolha uma análise já feita, preencha o briefing (nicho, público, objetivo, tom, produto, tema) e gere ideias originais a partir do DNA identificado, ou gere uma matriz de possibilidades (hooks × temas × ângulos × formatos).
4. **3. Avaliar (Score):** cole qualquer ideia/roteiro e receba uma pontuação 0-100 ponderada pelo seu objetivo (Viralização, Vendas ou SEO), com pontos fortes, fracos e uma versão otimizada.
5. **Banco de Ideias:** histórico de tudo (análises, ideias geradas, matrizes, scores), salvo no navegador, com busca e opção de excluir.

## Por que é MVP e não a visão completa

Essa é a primeira fatia da visão discutida (ver `prompts/`). Decisões deliberadas para validar rápido:

- **Sem scraping de Instagram/TikTok.** Puxar vídeos/perfis automaticamente esbarra em ToS das plataformas e exige infraestrutura cara (download, transcrição de áudio, proxies). O usuário cola a transcrição manualmente.
- **Sem backend.** Cada usuário usa sua própria API key da Anthropic. Isso evita custo de infraestrutura e cobrança antes de validar que o produto entrega valor. Quando validado, o caminho natural é migrar para um backend com autenticação e assinatura (esconder a chave, cobrar por uso).
- **Geração de ideias e Matriz são fluxos separados do Score**, para manter cada chamada de IA simples e evitar parsing frágil de texto livre em cards estruturados.

## Roadmap (dos prompts originais)

| Fase | Nome | Status |
|---|---|---|
| V1 (MVP) | Vídeo único → Transcrição → Autópsia → DNA → SEO → Ideias → Score | ✅ implementado aqui |
| V2 | Find Outliers — analisar um perfil inteiro e achar vídeos fora da curva | 🔜 não iniciado |
| V3 | Content Radar — monitoramento contínuo de vários concorrentes, alertas semanais | 🔜 não iniciado |

## Estrutura de arquivos

```
content-intelligence-engine/
├── app.html              # o app (abrir direto no navegador)
├── README.md             # este arquivo
└── prompts/              # os 8 prompts de sistema que formam o pipeline
    ├── 01-cerebro-da-plataforma.md      # system prompt raiz (regras gerais)
    ├── 02-transcricao-estruturada.md    # extração
    ├── 03-autopsia-completa.md          # por que o conteúdo funciona
    ├── 04-dna-estrategico.md            # padrões reutilizáveis (mecanismo)
    ├── 05-seo-social.md                 # oportunidade de busca/descoberta
    ├── 06-geracao-de-ideias.md          # modelagem → ideias originais
    ├── 07-matriz-de-conteudo.md         # geração combinatória de ideias
    └── 08-viral-score.md                # avaliação 0-100 ponderada por objetivo
```

`app.html` embute o conteúdo desses prompts diretamente no JavaScript (não há fetch de arquivo local, para funcionar abrindo o HTML direto sem servidor). Se editar um prompt em `prompts/`, replique a mudança na constante correspondente em `app.html`.

## Dados

Tudo fica no `localStorage` do navegador (API key, análises, ideias, scores). Não sincroniza entre dispositivos e não há conta/login. Limpar os dados do navegador apaga o histórico.
