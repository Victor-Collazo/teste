# Controle de Alunos e Pacientes — Consultoria Online

Ferramenta simples (um único arquivo HTML) com dois espaços de trabalho — **Treinador** e **Nutricionista** — cada um com seus próprios cadastros, planos e quadro de acompanhamento.

> Landing page de vendas da consultoria (Victor Collazo + Gabriela Padial) fica em [`landing/`](landing/README.md), como projeto separado deste painel.

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

## Dados

Os dados de cada espaço ficam salvos separadamente no `localStorage` do navegador usado — não há backend nem conta. Isso significa que a lista não sincroniza entre dispositivos ou navegadores diferentes; ela persiste no mesmo navegador entre sessões.
