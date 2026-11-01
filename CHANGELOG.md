# Histórico de versões — Mentha CRM

Cada versão publicada fica marcada no GitHub (aba **Releases**) e pode ser restaurada a qualquer momento.
A versão em uso aparece no app em **Config → Sobre**.

## V2.2 — 2.2.0 (01/11/2026)

**Ranking de indicações** (Relatórios)
- Mostra quem mais indicou clientes, com 🥇🥈🥉, número de indicações, quantas indicadas já vieram, a receita gerada pelas indicadas e a data da última indicação. Dá para ver no período escolhido ou em todo o histórico.
- Botão **🎁 Parabenizar** para as 3 primeiras, com mensagem pronta no WhatsApp.
- Reconhece a cliente indicadora mesmo com apelido, erro de digitação ou emoji (ex.: "Manicure Camila Fasto" → Camila Fausto).
- **Indicações para confirmar:** quando o nome bate com mais de uma cliente (ex.: "Gabriela"), basta tocar na cliente certa.
- **Vieram por indicação sem dizer quem:** lista para preencher quem indicou, para entrar no ranking.
- A ficha da cliente mostra quem ela indicou com a mesma regra.

## V2.1 — 2.1.0 (01/11/2026)

**Taxa de cancelamento e falta**
- Novo botão **✕ Cancelou/Faltou** nos agendamentos. Ele já sugere a taxa de **50% do valor dos procedimentos**, que pode ser ajustada ou zerada ("Sem taxa"), com a forma de pagamento.
- Mudar o status para Cancelado ou Faltou no formulário também mostra o campo da taxa.
- A taxa **entra na receita**: total faturado, Receitas, Relatórios, formas de pagamento e total gasto pela cliente.
- A taxa **não conta como atendimento nem como visita**. Linhas de "Taxa de cancelamento" vindas da planilha também deixam de contar como atendimento.
- No Painel e nos Relatórios aparece quanto da receita veio de taxas. A ficha da cliente mostra quantas vezes ela cancelou ou faltou.
- No Google Agenda, o evento não é apagado: fica marcado com ❌ "cancelou/faltou" e com o horário livre.
- O percentual da taxa pode ser alterado em **Config → Taxas e parâmetros**.

## V2 — 2.0.0 (22/10/2026)

**Correções**
- **Total faturado sem desconto da maquininha.** Os valores lançados já são líquidos, como na planilha. O desconto agora é opcional em Config e vem desligado.
- **Contagem de atendimentos igual à da planilha.** Cada serviço conta como um atendimento (uma linha na planilha). O app mostra também o número de **visitas** (cliente + dia).
- **Importar da planilha não duplica mais.** Se a planilha ganhou um serviço novo numa visita que já existe, o app atualiza essa visita em vez de criar outra.
- Ao importar clientes, a cliente é reconhecida também pelo telefone/CPF e pelo nome parcial, sem recriar duplicadas.

**Novidades**
- **Conferir com a planilha** (aba Receitas): compara o mês do app com a aba do mês da planilha e lista o que falta, o que tem valor diferente e o que só existe no app, com botão para importar.
- **Relatórios: gráficos por data** (dia, semana ou mês, no período escolhido):
  - Atendimentos por data (por profissional)
  - Serviços por data
  - Atendimentos por forma de pagamento por data
  - Visitas por cliente por data (mapa de calor, Top 10/15/30/todas)
  - Cada gráfico tem "Ver dados em tabela".
- Ticket médio passa a ser **por visita**.
- Versão do app visível em Config → Sobre.

## V1 — 1.0.0 (21–22/10/2026)

Primeira versão em uso:
- Painel no modelo da aba do mês (meta, faturado, gastos, líquido), agenda, receitas, despesas, clientes, serviços e relatórios.
- Base importada da planilha (clientes, atendimentos, despesas, metas, histórico desde set/24).
- Google Agenda com as agendas Thais e Amanda; profissionais Thais/Amanda com filtro.
- Agenda em dia / semana / mês / lista.
- Sincronização entre aparelhos pela planilha (aba oculta `CRM_dados`).
- Layout para celular e tablet; app instalável (PWA).
- Visão de cartões ou tabela com ordenação por coluna em Receitas, Despesas e Clientes.
