# Guia do Dashboard — Google Looker Studio

Use o arquivo **`dashboard_dados.xlsx`** (nesta pasta). Ele já vem com tudo pronto:

- Aba **`dados`** — base linha a linha (salário + categorias) → para filtros, histograma e contagens.
- Abas agregadas (**`mediana_senioridade`**, **`genero_x_senioridade`**, **`mediana_cargo`**, **`mediana_regiao`**, **`media_raca`**, **`mediana_experiencia`**, **`ranking_fatores`**) → resolvem o ponto fraco do Looker, que **não calcula mediana** nativamente. As medianas/médias já estão prontas.

## Passo a passo

1. Suba o `dashboard_dados.xlsx` no **Google Sheets** (Arquivo → Importar → cada aba vira uma página).
2. Em [lookerstudio.google.com](https://lookerstudio.google.com) → *Criar* → *Fonte de dados* → **Google Sheets** → selecione a planilha (e a aba desejada por gráfico).
3. **Publique com acesso público** (Compartilhar → "Qualquer pessoa com o link pode ver") e cole o link no README.

## Os 4+ gráficos (rubrica: 2,0 pts)

| # | Visualização | Aba | Pergunta que responde |
|---|---|---|---|
| 1 | **Histograma** de `salario` | `dados` | Como os salários se distribuem? |
| 2 | **Barras** mediana × senioridade | `mediana_senioridade` | Quanto a senioridade move o salário? |
| 3 | **Barras agrupadas** média × gênero × senioridade | `genero_x_senioridade` | O gap de gênero persiste no mesmo nível? |
| 4 | **Barras** mediana × cargo | `mediana_cargo` | Que papel paga mais? |
| ➕ | **Barras** ranking de fatores | `ranking_fatores` | Qual fator pesa mais no total? |

➕ **1 filtro interativo:** adicione um controle de filtro sobre a aba `dados` por `nivel_senioridade`, `genero` ou `regiao`.
➕ **1 caixa de texto** com o insight principal em linguagem de gestor, por exemplo:
> *"Senioridade e experiência são o que mais define o salário: um Sênior ganha cerca de 4x um Júnior. Mas, no nível Sênior, mulheres ganham ~18% menos que homens em média — uma diferença que não aparece nos níveis iniciais."*

➕ **Cabeçalho:** título + fonte ("State of Data Brazil 2024–2025, Data Hackers + Bain").

## Identidade visual

Azul-escuro `#1F4E79` · Azul `#2E75B6` · Azul-claro `#9DC3E6` · Laranja de destaque `#C55A11`. Use o laranja só para o dado em destaque (ex.: a barra do fator nº 1 no ranking).

> Cada gráfico responde a **uma** pergunta. Se não dá pra formular a pergunta, o gráfico não deveria estar lá.
