# 📊 Pipeline de Inteligência em Planejamento de Demanda & S&OP (End-to-End Analytics)

![Dashboard de Planejamento de Demanda e S&OP](imagens/sop.jpg)

## 🧩 Contexto e Problema de Negócio

No setor de bens de consumo (FMCG), o desalinhamento entre o volume previsto de vendas (*Forecast*) e o volume realmente comercializado na ponta (*Sell-Out*) gera sérios impactos financeiros nas operações fabris e de distribuição:
* **Overforecasting (BIAS positivo):** Acúmulo desnecessário de estoque, imobilização de capital de giro e risco de obsolescência de produtos.
* **Underforecasting (BIAS negativo):** Ruptura de estoque nos canais de venda, perda direta de receita e queda no nível de serviço aos clientes.

Este projeto foi projetado para automatizar o ciclo de inteligência de **Sales and Operations Planning (S&OP)**, calculando métricas de acurácia em grande escala e convertendo análises quantitativas em recomendações prescritivas para as tomadas de decisão estratégicas.

---

## 🎯 Objetivos do Projeto

* Construir um pipeline escalável e distribuído em **PySpark** para ingestão e consolidação de dados de vendas e planejamento.
* Monitorar a eficiência da cadeia logística e a precisão do *forecast* por meio de métricas como **BIAS (unidades)**, **MAPE / Erro % SKU** e **Fill Rate (%)**.
* Desenvolver uma matriz de recomendação automatizada para direcionar ações prescritivas diretamente para as áreas responsáveis (Trade Marketing/RGM, Supply Chain e Planejamento).
* Publicar um painel interativo no **Looker Studio** com visão executiva e tática dos indicadores.

---

## 🧱 Arquitetura e Etapas da Solução

```text
[Dados Brutos ERP/CSV]
       │
       ▼
[Pipeline Distribuído - PySpark (Google Colab)]
   ├── 1. Ingestão e Sanitização de Tipos
   ├── 2. Agregações & Engenharia de KPIs (BIAS, Fill Rate, MAPE)
   └── 3. Regra de Negócio Prescritiva (Classificação S&OP)
       │
       ▼
[Data Layer (Arquivos Processados Parquet / CSV)]
       │
       ▼
[Looker Studio - Dashboard Executivo & Tático]

📊 Principais Indicadores Calculados (KPIs):

* Métrica - BIAS(Unidades) |   Conceito de Negócio - Medida de viés direcional (Forecast - Sell Out) | Impacto Estratégico - Identifica a sobra ou a falta absoluta de produto na ponta.
** Métrica - Erro % SKU (MAPE) | Conceito de Negócio -  Percentual de desvio absoluto vs. venda real | Impacto Estratégico - Avalia a precisão do algoritmo de demanda por item.
*** Métrica - Fill Rate (%) | Conceito de Negócio - Taxa de atendimento da fábrica (Atendido / Sell In) | Impacto Estratégico - Mede o nível de serviço e a eficiência logística fabril
**** Métrica - Ação Prescritiva | Conceito de Negócio - Classificação automática baseada na variação do BIAS | Direciona a ação responsável (Trade Mkt, Supply Chain ou Planejamento).
                             
                              
📈 Resultados & Painel Executivo no Looker Studio

💡 Destaques dos Resultados ObtidosVisualização Unificada (Scorecards): Mapeamento global de 50.000 un planejadas (Forecast) contra 41.100 un comercializadas (Sell-Out), evidenciando um BIAS líquido de +9.000 un acumuladas e um Fill Rate médio de 96,36%.

Matriz de Responsabilidade Prescritiva:

40% Trade Mkt & RGM: Atuação promocional para queima controlada de sobre-estoque em categorias críticas.
20% Supply Chain: Ação prioritária de reabastecimento em SKUs subestimados com risco iminente de ruptura.
40% Planejamento Contínuo: Produtos operando dentro da margem tolerável de acurácia.

📊 Acesse o Dashboard Executivo de S&OP no Looker Studio (https://datastudio.google.com/s/iRtI9-AMkyY)

🛠️ Tecnologias e Ferramentas UtilizadasLinguagem & Processamento: Python 3.x, Apache Spark / PySpark
Manipulação & Análise: pandas, numpy
Visualização: Google Looker Studio
Ambiente de Desenvolvimento: Google Colab / Jupyter NotebookControle de Versão: Git / GitHub

📂 Estrutura do RepositórioPlaintext├── data/
│   ├── raw/                  # Respostas brutas da base ERP (vendas/forecast)
│   └── processed/            # Dados limpos e métricas S&OP consolidadas
├── notebooks/
│   └── pipeline_sop_demand.ipynb # Notebook PySpark com tratamento, métricas e regras
├── images/
│   └── dashboard_sop.png     # Capturas do dashboard executivo no Looker Studio
├── requirements.txt          # Dependências e bibliotecas
└── README.md                 # Documentação completa do projeto

▶️ Como Executar o Projeto

1. Clone este repositório:

Bashgit clone [https://github.com/julimarpoliveira2902/pipeline-planejamento-demanda-sop.git](https://github.com/julimarpoliveira2902/pipeline-planejamento-demanda-sop.git)
cd pipeline-planejamento-demanda-sop

2. Instale o PySpark e dependências:

Bashpip install -r requirements.txt

3. Execute o Notebook:

Abra e execute o arquivo notebooks/pipeline_sop_demand.ipynb em seu ambiente do Google Colab ou Jupyter Notebook.

👨‍💻 Autor:Julimar Pedro de Oliveira
Linkedin [ www.linkedin.com/in/julimarpoliveira]

