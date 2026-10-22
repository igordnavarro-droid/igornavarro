# Mentha CRM 🌿

CRM e controle financeiro do **Mentha Nail Design** em um único arquivo (`index.html`), feito para rodar no GitHub Pages.

## O que tem

- Tema claro com detalhes em verde.
- **Painel** no modelo da aba Outubro.26: meta do mês, quanto falta, total bruto faturado, total de gastos e total líquido, além de próximos atendimentos, clientes que precisam reagendar, contas pendentes, aniversariantes e dízimo sugerido.
- **Agenda**: visões Dia, Semana, Mês e Lista (como o Google Agenda), com filtro de data. Clique num horário vazio para agendar. Tudo o que é criado, concluído ou excluído vai automaticamente para o Google Agenda; se o login do Google tiver expirado, os eventos ficam na fila e são enviados quando você entrar de novo.
- **Receitas**: tabela igual à da planilha (Data, Cliente, Procedimento, Valor, Adicional, Pagamento, Total, Descrição). Taxa de crédito (3,09%) e débito (0,89%) descontadas automaticamente.
- **Despesas**: Pago/Pendente com um toque, tipos e meios de pagamento da planilha, parcelamentos (1/10, 2/10…) e botão para gerar as despesas fixas do mês.
- **Clientes**: ficha com anamnese (alergias, diabetes, gestante), indicações, histórico, ficha técnica das manutenções, total gasto e última visita.
- **Serviços**: tabela de preços e duração editáveis.
- **Relatórios**: filtro de período (este mês, mês passado, 3/6/12 meses, ano, personalizado…) e visão por dia, semana ou mês, com faturado, gastos, líquido, atendimentos, ticket médio, meta, serviços, clientes, formas de pagamento, dia da semana, despesas por tipo e novas clientes. Exporta CSV.

## Publicar no GitHub Pages

1. Crie um repositório (ex.: `mentha-crm`) e envie o `index.html` (e este README).
2. Em **Settings → Pages**, escolha *Deploy from a branch*, branch `main`, pasta `/ (root)`.
3. O app fica em `https://SEU-USUARIO.github.io/mentha-crm/`.

> ⚠️ **Não coloque dados de clientes no repositório.** O arquivo não contém nenhum dado pessoal; tudo o que você cadastra fica salvo só no navegador. Pode deixar o repositório público sem problema.

## Trazer os dados da planilha

O app lê direto a planilha **Controle Financeiro - Unhas** pela sua conta Google (somente leitura, nada é alterado nela):

1. Configure o Client ID do Google (passo a passo abaixo). Ative também a **Google Sheets API** no projeto.
2. Em **Config → Planilha Google**, clique em **Conectar e ver abas**.
3. Marque as abas e clique em **Importar abas selecionadas**. Os clientes vêm da aba `Clientes`; atendimentos, despesas e metas vêm das abas mensais (`Outubro.26`, `Setembro.26`…).
4. No dia a dia, o botão **↻ Planilha** no Painel puxa de novo os clientes e a aba do mês selecionado.

Lançamentos repetidos são ignorados, então pode sincronizar quantas vezes quiser. Sem login do Google, também dá para importar abas baixadas em `.csv` em **Config → Importar arquivo CSV**.

## Conectar a Google Agenda

Sem configurar nada, o botão 📅 de cada atendimento já abre o evento preenchido na Google Agenda. Para sincronizar automaticamente:

1. Em [console.cloud.google.com](https://console.cloud.google.com/), crie um projeto.
2. **APIs e serviços → Biblioteca** → ative a **Google Calendar API** e a **Google Sheets API**.
3. **Tela de consentimento OAuth** → Externo → adicione seu e-mail em *Usuários de teste*.
4. **Credenciais → Criar credenciais → ID do cliente OAuth → Aplicativo da Web**. Em *Origens JavaScript autorizadas* coloque `https://SEU-USUARIO.github.io`.
5. Copie o Client ID e cole em **Config → Google Agenda** no app. Depois, **Entrar com Google**.

Com isso, cada agendamento cria/atualiza/remove o evento na agenda, e a aba Agenda mostra os eventos do Google do mês para importar. O login do Google dura cerca de 1 hora; quando expirar, é só clicar em "Entrar com Google" de novo.

## Backup

Os dados ficam no navegador do aparelho. Em **Config → Backup**, baixe o arquivo `.json` com frequência; use **Restaurar backup** para passar os dados para outro celular ou computador.
