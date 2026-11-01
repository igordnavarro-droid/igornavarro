# Mentha CRM 🌿

**Versão atual: 2.2.0** — veja o [histórico de versões](CHANGELOG.md).

CRM e controle financeiro do **Mentha Nail Design** em um único arquivo (`index.html`), feito para rodar no GitHub Pages.

## O que tem

- Tema claro com detalhes em verde e a logo da Mentha Nail Spa.
- **Instalável como app** (PWA): no Chrome do Android, menu ⋮ → *Instalar app*. Abre em tela cheia, com ícone na tela inicial, e funciona offline com os dados salvos no aparelho.
- **Profissionais** (Thais e Amanda): cada atendimento tem a profissional; filtro Todas/Thais/Amanda no Painel, Agenda, Receitas e Relatórios; cada uma tem a sua agenda no Google.
- **Painel** no modelo da aba Outubro.26: meta do mês, quanto falta, total bruto faturado, total de gastos e total líquido, além de próximos atendimentos, clientes que precisam reagendar, contas pendentes, aniversariantes e dízimo sugerido.
- **Cancelamentos e faltas**: botão *Cancelou/Faltou* sugere taxa de 50% dos procedimentos; a taxa entra na receita, mas não conta como atendimento.
- **Ranking de indicações** (Relatórios): quem mais indicou clientes, para premiar.
- **Agenda**: visões Dia, Semana, Mês e Lista (como o Google Agenda), com filtro de data. Clique num horário vazio para agendar. Tudo o que é criado, concluído ou excluído vai automaticamente para o Google Agenda; se o login do Google tiver expirado, os eventos ficam na fila e são enviados quando você entrar de novo.
- **Receitas**: tabela igual à da planilha (Data, Cliente, Procedimento, Valor, Adicional, Pagamento, Total, Descrição). Os valores são líquidos, como na planilha (o desconto da maquininha é opcional em Config). Botão **Conferir com a planilha** compara o mês com a aba da planilha.
- **Despesas**: Pago/Pendente com um toque, tipos e meios de pagamento da planilha, parcelamentos (1/10, 2/10…) e botão para gerar as despesas fixas do mês.
- **Clientes**: ficha com anamnese (alergias, diabetes, gestante), indicações, histórico, ficha técnica das manutenções, total gasto e última visita.
- **Serviços**: tabela de preços e duração editáveis.
- **Relatórios**: filtro de período e visão por dia/semana/mês; faturado × gastos × meta, atendimentos, serviços, formas de pagamento e visitas por cliente por data, além de serviços mais vendidos, melhores clientes, dia da semana e origem das clientes. Exporta CSV.

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

## Sincronização entre aparelhos

Os dados ficam numa aba oculta (`CRM_dados`) da planilha "Controle Financeiro - Unhas", na conta Google de vocês, e não no repositório. Todo aparelho que entrar com o Google usa os mesmos dados. As alterações são enviadas em segundos, e os outros aparelhos recebem ao abrir o app ou a cada ~45 s.

- Para configurar um celular ou tablet novo: no computador, **Config → Usar em outro aparelho**. Escaneie o QR code com o celular e toque em **Entrar com Google**.
- A planilha precisa estar compartilhada como **Editor** com todos os e-mails que usam o app.
- Se dois aparelhos editarem ao mesmo tempo, as alterações são combinadas registro a registro.

## Backup

Em **Config → Backup** dá para baixar uma cópia `.json` dos dados a qualquer momento.

## Versões

- Cada versão publicada ganha uma marcação (`v1.0.0`, `v2.0.0`…) e uma página em **Releases** no GitHub, com o que mudou.
- O histórico completo está em [CHANGELOG.md](CHANGELOG.md).
- Para voltar a uma versão anterior, peça ao Claude: "volte o app para a V1". A versão marcada é republicada sem perder os dados, que ficam na planilha.
