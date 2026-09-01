# Análise de Risco de Crédito: Do SQL/Python ao Power BI

##  Visão Geral do Projeto
Este projeto tem como objetivo analisar os fatores determinantes da inadimplência bancária e entender o risco de crédito. 

A solução foi construída desde a ingestão e tratamento de dados brutos usando **Python e SQL (SQLite)**, passando por análises exploratórias (**Plotly**), até a consolidação em um **Dashboard no Power BI** para apoio à tomada de decisão.


## Tecnologias e Etapas do Projeto

### 1. Ingestão e Consultas(SQL & SQLite)
A partir da base bruta, os dados foram carregados em um banco SQLite (`credito_banco.db`) para a criação de queries de inteligência de negócio:
* **Intenção de Crédito:** Avaliação do volume e ticket médio por motivo de empréstimo.
* **Progressão de Risco:** Cálculo da taxa de inadimplência por nota de risco (`loan_grade` A-G).
* **Comprometimento de Renda:** Análise de impacto do valor do empréstimo sobre a renda do cliente (`loan_percent_income`).
* **Análise de Histórico:** Avaliação das taxas de juros para negativados (`cb_person_default_on_file`) e tempo de histórico bancário.
  

### 2. Tratamento de Dados e Análise Exploratória (Python)
Utilizando **Pandas** e **Plotly**, a base passou por limpeza e validação estatística:
* **Ajuste de Valores Nulos:** Preenchimento de valores ausentes em `person_emp_length` e `loan_int_rate` utilizando a mediana.
* **Limpeza de Outliers/Erros:** Remoção de inconsistências físicas (clientes com idade maiores que 100 anos ou tempo de trabalho superior à idade).
* **Visualização com Plotly:** Construção de Boxplots de taxas de juros, Scatter Plots (Renda vs. Empréstimo) e Histogramas de distribuição.
* **Exportação:** Geração do dataset tratado (`new_credit_risk.csv`).
  

### 3. Business Intelligence & Dashboard (Power BI)
* **Métricas DAX:** Criação de medidas calculadas para percentual de inadimplência e taxa de juros média.
* **Layout One-Pager:** Painel consolidado com cartões de KPI e visuais comparativos (Risco por Grade, Histórico Negativo, Motivo e Moradia).
  

## Principais Insights Extraídos

* **Progressão Linear do Risco:** A taxa de inadimplência cresce de forma diretamente proporcional à nota de risco do cliente, sendo a classe **A** a mais segura e a **G** a de maior risco.
* **Precificação do Histórico:** Clientes com histórico prévio de inadimplência (`Y`) pagam taxas de juros médias visivelmente superiores aos clientes com nome limpo (`N`).
* **Demanda de Crédito:** **Educação** e **Despesas Médicas** lideram a quantidade de solicitações de empréstimos.


## Demonstração & Links

* **Google Colab (Código Python & SQL):** [Acessar Notebook no Google Colab](https://colab.research.google.com/drive/1MdaQUX69pHu0dBtMNLsfJ2uo90eyqwZP?usp=sharing)
* **Dashboard Power BI:** <img width="1381" height="778" alt="image" src="https://github.com/user-attachments/assets/395bad93-cd35-4fe3-b77a-34e98ae542e8" />



![Dashboard Power BI](COLE_O_LINK_DA_IMAGEM_OU_ARRASTE_A_FOTO_AQUI)

## Estrutura do Repositório
* `notebooks/`: Script Python (`.py`/`.ipynb`) contendo a criação do banco SQLite, queries e limpeza com Pandas.
* `data/`: Datasets utilizados (`credit_risk_dataset.csv` e `new_credit_risk.csv`).
* `powerbi/`: Arquivo do dashboard `.pbix` e capturas de tela do relatório final.
