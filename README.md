# 📊 O que move o salário em dados no Brasil?
> Análise dos fatores que mais influenciam a remuneração de profissionais de dados no Brasil em 2024.

![UNIFSA](https://img.shields.io/badge/UNIFSA-Engenharia%20de%20Software-1F4E79?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker%20Studio-4285F4?style=for-the-badge&logo=google&logoColor=white)

---

## 📋 Sobre o Projeto

Este trabalho analisa a base **State of Data Brazil 2024–2025** (Data Hackers + Bain & Company) — o maior mapeamento do mercado de dados e IA do Brasil, com **5.217 respondentes** e 400+ variáveis — para responder à pergunta central:

> *"Quais fatores mais influenciam o salário de um profissional de dados no Brasil em 2024?"*

**Autores:** João William · Guilherme Frazão
**Disciplina:** Análise Avançada de Dados · UNIFSA
**Professora:** Ma. Heloísa Guimarães

---

## 🔗 Links

| Entregável | Link |
|---|---|
| 📊 Dashboard (Looker Studio) | [Acessar dashboard](https://datastudio.google.com/reporting/dd8b8e9e-ff30-466a-af7e-5dec5b95b85f) |
| 📓 Notebook de análise | [notebook/joaowilliam-guilhermefrazao-analise.ipynb](notebook/joaowilliam-guilhermefrazao-analise.ipynb) |
| 📄 Relatório narrativo (PDF) | [relatorio/joaowilliam-guilhermefrazao-relatorio.pdf](relatorio/joaowilliam-guilhermefrazao-relatorio.pdf) |

---

## 💡 Resposta à Pergunta Central

A análise de **4.863 profissionais** revelou que os fatores que mais movem o salário são, em ordem de impacto:

| # | Fator | Amplitude salarial |
|---|---|---|
| 🥇 | Tempo de experiência | R$ 16.142 |
| 🥈 | Nível de ensino | R$ 11.788 |
| 🥉 | Cargo/papel técnico | R$ 10.549 |
| 4º | Senioridade | R$ 10.502 |
| 5º | Ser gestor | R$ 10.252 |
| 6º | Região | R$ 4.069 |
| 7º | Cor/raça | R$ 3.763 |
| 8º | Gênero | R$ 2.477 |

### 📈 Senioridade em números
- **Júnior:** mediana R$ 3.500
- **Pleno:** mediana R$ 7.000
- **Sênior:** mediana R$ 14.000 *(+300% vs Júnior)*
- Correlação de Spearman: **ρ = 0,73** (p < 0,001)

### ⚖️ Achado ético: gap de gênero cresce com a senioridade
Na média global, homens ganham **19,6% a mais** que mulheres. Mas o ponto decisivo está no controle por nível:

| Nível | Gap (média) |
|---|---|
| Júnior | −1% (sem diferença) |
| Pleno | +4% |
| **Sênior** | **+17,6%** |

O gap se concentra no topo, onde mulheres já são minoria (21% dos sêniores). Por cor/raça, profissionais brancos ganham **22,1% a mais** que pretos na média.

---

## 🧹 Principais Decisões de Limpeza

| Problema | Decisão | Justificativa |
|---|---|---|
| Salário em texto (faixas) | Convertido para **ponto médio** numérico | Sem número não há estatística |
| Colunas crípticas (`2.h_...`, `1.b_...`) | Detecção automática + renomeação de 13 colunas | Legibilidade e reprodutibilidade |
| *Missing* em gênero e raça | **Não imputados** — mantido como "Não informado" | A não-resposta é informação |
| *Missing* em salário (6,8%) | 354 linhas removidas | É a variável-resposta |
| Mediana mascara gaps | Usamos **média** para gênero e raça | Em faixas largas a mediana cai na mesma banda |

> ⚠️ A imprecisão do ponto médio é assumida explicitamente — por isso a **mediana** é a medida principal nas comparações grandes.

---

## 🚀 Como Reproduzir

### Pré-requisitos
- Python 3.10+
- Google Colab (recomendado) ou Jupyter Notebook
- Conta no Kaggle

### 1. Baixe a base de dados
```
kaggle.com/datasets/datahackers/state-of-data-brazil-20242025
```
Instruções detalhadas em [`dados/README.md`](dados/README.md).

### 2. Execute o notebook
Abra `notebook/joaowilliam-guilhermefrazao-analise.ipynb` no Colab e clique em **Executar tudo**. O notebook detecta e baixa a base automaticamente (ou abre o upload manual).

### 3. Monte o dashboard
O notebook gera `state_of_data_tratado.csv`. Suba no Google Sheets e conecte ao Looker Studio seguindo o [`dados/GUIA_DASHBOARD.md`](dados/GUIA_DASHBOARD.md).

---

## 🛠️ Tecnologias

| Camada | Tecnologia |
|---|---|
| Linguagem | Python 3 |
| Análise de dados | pandas, numpy |
| Visualização | matplotlib, seaborn |
| Estatística | scipy (Spearman, skewness) |
| Dashboard | Google Looker Studio |
| Versionamento | GitHub |

---

## 📁 Estrutura do Repositório

```
joaowilliam-guilhermefrazao-state-of-data/
├── README.md                                        ← Este arquivo
├── notebook/
│   └── joaowilliam-guilhermefrazao-analise.ipynb   ← Análise completa (5 etapas)
├── relatorio/
│   └── joaowilliam-guilhermefrazao-relatorio.pdf   ← Relatório narrativo (5 páginas)
└── dados/
    ├── README.md                                    ← Como baixar a base do Kaggle
    └── GUIA_DASHBOARD.md                            ← Passo a passo do dashboard
```

> ⚠️ O CSV da base do Kaggle **não está versionado** neste repositório (15MB). Veja as instruções em `dados/README.md`.

---

## 📚 Referências

- **Dados:** State of Data Brazil 2024–2025 — Data Hackers + Bain & Company
- **Bibliotecas:** pandas, numpy, matplotlib, seaborn, scipy
- **Dashboard:** Google Looker Studio

---

*© 2026 João William & Guilherme Frazão · UNIFSA*
