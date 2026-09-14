# Controle de Alunos e Pacientes — Consultoria Online

Ferramenta simples (um único arquivo HTML) com dois espaços de trabalho — **Treinador** e **Nutricionista** — cada um com seus próprios cadastros, planos e quadro de acompanhamento.

## Como usar

Abra `index.html` em qualquer navegador — não precisa de servidor, build ou instalação. A página inteira pede usuário e senha antes de mostrar qualquer coisa (veja "Acesso à página" abaixo). Depois de entrar: a troca **Treinador / Nutricionista** fica no canto superior direito; as abas "Alunos"/"Pacientes" e "Acompanhamento" ficam na barra lateral esquerda.

## Espaço do Treinador

Cadastro por aluno: nome, produto (Minha Consultoria / Consultoria Premium), plano (BASIC, PLUS, ADVANCED, ELITE, DIAMOND — de 1 a 12 protocolos), início do plano e protocolo/data atual. O painel calcula automaticamente:

- **Protocolo atual** (ex.: "3 de 6"), com barra de progresso.
- **Próxima troca de treino** — 45 dias após o início do protocolo atual.
- **Previsão de término do plano** — soma os protocolos restantes a partir do início do protocolo atual; se a troca atual está atrasada, o atraso é somado à previsão em vez de manter uma data fixa (porque nem sempre o aluno preenche o formulário de atualização na data certa).
- **Status** — Ativo, Trocar treino em breve, Atrasado, Plano perto do fim ou Plano concluído.

Clique em **"Treino trocado hoje"** para registrar a troca real (avança o protocolo e recalcula a previsão). No último protocolo, o botão vira **"Concluir plano hoje"**.

**Acompanhamento (CRM):** colunas Onboarding, Ativo, Atenção, Renovação, Encerrado.

## Espaço da Nutricionista

Cadastro por paciente: nome, plano e data da primeira consulta. Os planos são:

- **SILVER** — consulta avulsa, 30 dias, sem retorno agendado.
- **GOLD** — trimestral (retorno a cada 90 dias).
- **DIAMOND** — semestral (retorno a cada 180 dias).

A partir da data da consulta, o painel calcula automaticamente:

- **Envio do PARQ** — lembrete para enviar o formulário de acompanhamento 15 dias após a consulta.
- **Próxima consulta / renovação** — de acordo com o plano (Silver não tem retorno agendado).
- **Status** — Em acompanhamento, Enviar PARQ em breve/atrasado, Aguardando renovação, Renovação em breve/atrasada, ou Acompanhamento encerrado (Silver).

**Acompanhamento (CRM):** colunas Consulta, Elaboração do plano, PARQ, Renovação / Próxima consulta — refletindo o processo que ela usa com os pacientes (consulta → plano alimentar pelo app → PARQ de acompanhamento → renovação).

A paleta desse espaço (verde-escuro, dourado e marfim) segue a identidade visual da Gabi. O espaço do Treinador usa preto e vermelho, seguindo a identidade do site profvictorcollazo.com.

## Acesso à página

A página inteira (os dois espaços) fica atrás de uma tela de login. Usuário e senha padrão (definidos no início do `<script>`, na constante `APP_LOGIN`): **usuário `consultoria`, senha `acesso2026`** — troque antes de publicar. Depois de entrar uma vez, o navegador lembra o acesso (botão **"Sair"** na barra lateral bloqueia de novo).

Importante: esse login é só uma trava simples no navegador (não existe servidor por trás). Ele impede que alguém abra a página por acidente, mas **não é uma proteção de verdade** — qualquer pessoa que veja o código-fonte da página encontra a senha. Antes de publicar este link para acesso externo com dados reais de pacientes, vale a pena migrar para uma autenticação de verdade (com backend).

## Dados e sincronização

A ferramenta está publicada como um Artifact do Claude (link fixo, sempre "online" — não depende do seu navegador estar aberto). Quanto a onde os dados ficam salvos, a página tenta duas camadas, nessa ordem:

1. **Banco de dados do Artifact (nuvem).** Se o link for aberto por alguém logado no claude.ai e que faça parte da mesma organização de quem publicou a página, os dados de cada espaço (Treinador/Nutricionista) são salvos num banco compartilhado e sincronizados em tempo real entre qualquer aparelho/navegador que abrir o link — exatamente o que evita perder aluno. Um indicador no rodapé da página mostra **"Sincronizado na nuvem"** quando isso está ativo.
2. **`localStorage` do navegador (local).** Se quem abrir não estiver logado no claude.ai ou não fizer parte dessa organização, a nuvem fica indisponível e a página cai automaticamente para salvar só naquele navegador — o indicador do rodapé muda para **"Salvando apenas neste navegador"**. Nesse caso os dados não somem, mas também não aparecem em outro aparelho.

Na primeira vez que a nuvem fica disponível num navegador que já tinha alunos/pacientes salvos localmente, esses registros são copiados automaticamente para o banco — nada se perde na migração.

**Backup manual (funciona sempre, com ou sem nuvem):** os botões **"Exportar backup"** e **"Importar backup"**, ao lado de "Adicionar aluno/paciente", salvam ou recarregam a lista da aba atual como um arquivo `.json`. Vale usar isso de vez em quando como segurança extra, independente da sincronização.

### Se a Gabi não conseguir ver os dados sincronizados

Isso quer dizer que o navegador dela não está sendo reconhecido como parte da sua organização no claude.ai — o requisito da Anthropic para esse banco de dados compartilhado. Nesse caso, cada um continua salvando localmente (sem perda, só sem sincronizar), e o backup manual (exportar/importar) é o jeito de levar os dados de um aparelho para o outro enquanto isso não for resolvido.
