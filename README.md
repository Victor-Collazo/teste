# Controle de Alunos Consultoria Online

Ferramenta simples (um único arquivo HTML) para consultores acompanharem alunos, protocolos de treino e previsão de término de plano.

## Como usar

Abra `index.html` em qualquer navegador — não precisa de servidor, build ou instalação.

Para cada aluno, informe:

- **Nome do aluno**
- **Produto** — Minha Consultoria (treino) ou Consultoria Premium (treino e dieta)
- **Plano contratado** — BASIC (1 protocolo), PLUS (2), ADVANCED (3), ELITE (6) ou DIAMOND (12)
- **Início do plano**
- **Protocolo atual** e **início do protocolo atual** — para um aluno novo, mantenha os dois iguais ao início do plano; para um aluno que já está no meio do plano, ajuste esses dois campos.

A partir disso, o painel calcula automaticamente:

- **Protocolo atual** — em qual dos protocolos do plano o aluno está (ex.: "3 de 6"), com barra de progresso.
- **Próxima troca de treino** — 45 dias após o início do protocolo atual.
- **Previsão de término do plano** — soma os protocolos restantes (45 dias cada) a partir do início do protocolo atual. Como os alunos nem sempre preenchem o formulário de atualização de treino na data certa, essa previsão se ajusta automaticamente: se a troca atual já está atrasada, o atraso é somado à previsão de término, em vez de manter uma data fixa.
- **Status** — Ativo, Trocar treino em breve (≤3 dias), Atrasado (quando passou dos 45 dias sem confirmação), Plano perto do fim ou Plano concluído.

Quando o aluno finalmente preenche o formulário e o treino é atualizado, clique em **"Treino trocado hoje"** no card do aluno (ou escolha outra data) para registrar a troca — isso avança o protocolo e recalcula a previsão de término com a data real. No último protocolo, o botão vira **"Concluir plano hoje"**.

A lista é filtrável por produto, com busca por nome e ordenável (mais urgente primeiro, nome ou data de início).

## Dados

Os dados ficam salvos apenas no `localStorage` do navegador usado — não há backend nem conta. Isso significa que a lista não sincroniza entre dispositivos ou navegadores diferentes; ela persiste no mesmo navegador entre sessões.
