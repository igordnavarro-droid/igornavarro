# Mentha CRM 🌿

CRM e controle financeiro do **Mentha Nail Design** em um único arquivo (`index.html`), feito para rodar no GitHub Pages.

## O que tem

- **Painel** no modelo da aba Outubro.26: meta do mês, quanto falta, total bruto faturado, total de gastos e total líquido, além de próximos atendimentos, clientes que precisam reagendar, contas pendentes, aniversariantes e dízimo sugerido.
- **Agenda**: agendar, concluir com forma de pagamento, lembrete pronto no WhatsApp e sincronização com a Google Agenda.
- **Receitas**: tabela igual à da planilha (Data, Cliente, Procedimento, Valor, Adicional, Pagamento, Total, Descrição). Taxa de crédito (3,09%) e débito (0,89%) descontadas automaticamente.
- **Despesas**: Pago/Pendente com um toque, tipos e meios de pagamento da planilha, parcelamentos (1/10, 2/10…) e botão para gerar as despesas fixas do mês.
- **Clientes**: ficha com anamnese (alergias, diabetes, gestante), indicações, histórico, ficha técnica das manutenções, total gasto e última visita.
- **Serviços**: tabela de preços e duração editáveis.
- **Relatórios**: 12 meses de faturado × gastos × meta, comparação com o ano anterior, serviços mais vendidos, melhores clientes e de onde as clientes vieram. O histórico desde set/24 já vem carregado.

## Publicar no GitHub Pages

1. Crie um repositório (ex.: `mentha-crm`) e envie o `index.html` (e este README).
2. Em **Settings → Pages**, escolha *Deploy from a branch*, branch `main`, pasta `/ (root)`.
3. O app fica em `https://SEU-USUARIO.github.io/mentha-crm/`.

> ⚠️ **Não coloque dados de clientes no repositório.** O arquivo não contém nenhum dado pessoal; tudo o que você cadastra fica salvo só no navegador. Pode deixar o repositório público sem problema.

## Trazer os dados da planilha

No Google Sheets, abra a aba e use **Arquivo → Fazer download → .csv**. Depois, no app, vá em **Config → Importar**:

- **Clientes**: aba `Clientes` (ou `Todas Clientes`).
- **Atendimentos e despesas**: uma aba mensal (ex.: `Outubro.26`), com o mês selecionado no topo do app igual ao da aba. Também aceita `db_receitas` (só atendimentos).

Lançamentos repetidos são ignorados, então pode reimportar sem medo.

## Conectar a Google Agenda

Sem configurar nada, o botão 📅 de cada atendimento já abre o evento preenchido na Google Agenda. Para sincronizar automaticamente:

1. Em [console.cloud.google.com](https://console.cloud.google.com/), crie um projeto.
2. **APIs e serviços → Biblioteca** → ative a **Google Calendar API**.
3. **Tela de consentimento OAuth** → Externo → adicione seu e-mail em *Usuários de teste*.
4. **Credenciais → Criar credenciais → ID do cliente OAuth → Aplicativo da Web**. Em *Origens JavaScript autorizadas* coloque `https://SEU-USUARIO.github.io`.
5. Copie o Client ID e cole em **Config → Google Agenda** no app. Depois, **Entrar com Google**.

Com isso, cada agendamento cria/atualiza/remove o evento na agenda, e a aba Agenda mostra os eventos do Google do mês para importar. O login do Google dura cerca de 1 hora; quando expirar, é só clicar em "Entrar com Google" de novo.

## Backup

Os dados ficam no navegador do aparelho. Em **Config → Backup**, baixe o arquivo `.json` com frequência; use **Restaurar backup** para passar os dados para outro celular ou computador.
