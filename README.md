# Painel de Protocolos

Ferramenta simples (um único arquivo HTML) para consultores acompanharem alunos, protocolos de treino e vencimento de planos.

## Como usar

Abra `index.html` em qualquer navegador — não precisa de servidor, build ou instalação.

Para cada aluno, informe:

- **Nome do aluno**
- **Plano contratado** (texto livre, ex.: "Consultoria Trimestral")
- **Início do plano**
- **Duração do plano** (em dias, com atalhos para 45/90/135/180/365 dias)

A partir disso, o painel calcula automaticamente:

- **Próxima troca de treino** — cada protocolo dura 45 dias; o painel mostra a data do próximo ciclo e em qual protocolo o aluno está (ex.: "protocolo 2/4").
- **Vencimento do plano** — data de início + duração contratada.
- **Status** — "Ativo", "Trocar treino em breve" (≤3 dias), "Plano vence em breve" (≤7 dias) ou "Plano vencido".

A lista é ordenável (mais urgente primeiro, nome ou data de início) e tem busca por nome/plano.

## Dados

Os dados ficam salvos apenas no `localStorage` do navegador usado — não há backend nem conta. Isso significa que a lista não sincroniza entre dispositivos ou navegadores diferentes; ela persiste no mesmo navegador entre sessões.
