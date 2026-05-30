# O que move o salário em dados no Brasil? — State of Data Brazil 2024–2025

**Trabalho Final · Análise Avançada de Dados · UNIFSA**
**Autores:** João William · Guilherme Frazão
**Pergunta central:** *Quais fatores mais influenciam o salário de um profissional de dados no Brasil em 2024?*

🔗 **Dashboard (Looker Studio):** `COLE_AQUI_O_LINK_PUBLICO`
📓 **Notebook:** [`notebook/joaowilliam-guilhermefrazao-analise.ipynb`](notebook/joaowilliam-guilhermefrazao-analise.ipynb)
📄 **Relatório:** [`relatorio/joaowilliam-guilhermefrazao-relatorio.pdf`](relatorio/joaowilliam-guilhermefrazao-relatorio.pdf)

---

## Resposta à pergunta central

Analisando 4.863 profissionais (dos 5.217 respondentes, após remover quem não informou salário), o fator que **mais** influencia o salário é o **tempo de experiência** — e, no mesmo eixo, a **senioridade**. A mediana salarial sobe de **R$ 3.500 (Júnior)** para **R$ 7.000 (Pleno)** e **R$ 14.000 (Sênior)** — um Sênior ganha cerca de **300% a mais** que um Júnior — e a correlação de Spearman é forte (ρ = 0,73 para senioridade; ρ = 0,64 para experiência, ambos p < 0,001). Logo atrás vêm **cargo/papel técnico** (Engenheiro de ML e Arquiteto de Dados lideram, com mediana R$ 14.000; Analista de BI fica na base, R$ 5.000), **nível de ensino** (mestrado/doutorado R$ 14.000) e **ser gestor** (R$ 18.000 vs R$ 10.000). A **região** importa menos do que se imagina (Sul/Sudeste R$ 10.000 vs demais R$ 7.000).

Há um segundo grupo de fatores que pesa menos em amplitude, mas é o mais relevante eticamente: **gênero** e **cor/raça**. Na média, homens ganham **19,6% a mais** que mulheres — e o ponto decisivo é que, ao **controlar por senioridade**, a diferença é nula entre Júniores, pequena entre Plenos (+4%) e salta para **+17,6% entre Sêniores** (+28,6% na mediana). Ou seja: o gap se concentra exatamente no topo, onde as mulheres já são minoria (21% dos sêniores). Por cor/raça, profissionais brancos ganham **22,1% a mais** que pretos na média.

Em resumo: salário em dados é movido principalmente por **mérito acumulável** (experiência, senioridade, formação, papel técnico) — controlável pelo profissional —, mas os dados também revelam diferenças por gênero e raça que não se explicam por mérito e merecem leitura crítica.

---

## Principais decisões de limpeza

| Problema | Decisão tomada | Por quê |
|---|---|---|
| Salário em texto (faixas) | Convertido para o **ponto médio** (ex.: "R$ 4.001 a R$ 6.000" → 5.000). Abertas: "Menos de N" → N×0,5; "Acima de N" → N×1,2 | Sem número não há estatística; ponto médio é a aproximação padrão |
| Colunas crípticas (`2.h_...`, `1.b_...`) | Detecção automática + renomeação de 13 colunas-chave via rótulo/código/valores | Legibilidade e reprodutibilidade |
| *Missing* em gênero e raça | **Não imputados** — "Prefiro não informar" mantido | A não-resposta é informação; imputar distorceria a análise de desigualdade |
| *Missing* em salário (6,8%) | 354 linhas removidas | É a variável-resposta |
| Mediana mascara gaps pequenos | Para gênero e raça usamos a **média** | Em faixas largas a mediana cai na mesma banda e esconde a diferença |

> A imprecisão do ponto médio (assume distribuição uniforme na faixa) é assumida explicitamente — por isso a **mediana** é a medida principal nas comparações grandes.

## Como reproduzir

1. Baixe a base do Kaggle (ver [`dados/README.md`](dados/README.md)).
2. Abra `notebook/joaowilliam-guilhermefrazao-analise.ipynb` no Colab → **Executar tudo**.
3. O notebook gera o CSV tratado; suba no Google Sheets e conecte ao Looker Studio (ver [`dados/GUIA_DASHBOARD.md`](dados/GUIA_DASHBOARD.md)).

## Estrutura do repositório

```
joaowilliam-guilhermefrazao-state-of-data/
├── README.md
├── notebook/   joaowilliam-guilhermefrazao-analise.ipynb
├── relatorio/  joaowilliam-guilhermefrazao-relatorio.pdf
└── dados/      README.md · GUIA_DASHBOARD.md · dashboard_dados.xlsx
```

## Referências

- **Dados:** State of Data Brazil 2024–2025 — Data Hackers + Bain & Company. `kaggle.com/datasets/datahackers/state-of-data-brazil-20242025`
- **Bibliotecas:** pandas, numpy, matplotlib, seaborn, scipy
- **Dashboard:** Google Looker Studio
