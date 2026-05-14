# Análise de Indicadores Energéticos e Econômicos Globais

## Descrição do Projeto

Este projeto realiza uma **análise exploratória de dados (EDA)** e **preparação de dataset para Machine Learning** com base no dataset [Energy Economics Curated](https://www.kaggle.com/), extraído da plataforma Kaggle. O conjunto de dados reúne indicadores anuais de 129 países ao longo de 26 anos (1995–2020), abrangendo dimensões econômicas, energéticas, climáticas e ambientais.

O objetivo central é aplicar, de forma prática, os conceitos fundamentais de exploração, interpretação, tratamento e preparação de dados utilizando as principais bibliotecas do ecossistema Python para Ciência de Dados.

---

## Sobre o Dataset

| Atributo | Valor |
|---|---|
| **Fonte** | Kaggle — Energy Economics Curated |
| **Arquivo** | `energy_economics_curated.csv` |
| **Linhas** | 3.354 |
| **Colunas** | 21 |
| **Países** | 129 |
| **Período** | 1995 – 2020 |

### Principais variáveis

| Variável | Descrição |
|---|---|
| `co2_emissions_metric_tonnes_per_capita` | Emissões de CO₂ per capita (t) |
| `renewable_energy_consumption_pct_final_energy_use` | Consumo de renováveis (% do consumo final) |
| `real_gdp_constant_2015_usd` | PIB real em USD constantes de 2015 |
| `greenhouse_gas_emissions_metric_tonnes_per_capita` | Emissões de GEE per capita (t CO₂e) |
| `adaptive_capacity_index` | Índice de capacidade adaptativa climática (0–1) |
| `readiness_index` | Índice de prontidão climática (0–1) |
| `ecological_footprint_index` | Índice de pegada ecológica |
| `urban_population_pct_total_population` | Urbanização (% da população total) |
| `forest_area_pct_land_area` | Cobertura florestal (% da área) |
| `average_temperature_celsius` | Temperatura média anual (°C) |

---

## Estrutura do Repositório

```
projeto-np2-energia/
├── 📓 NP2_Energia_Economia_Global.ipynb   # Notebook principal (análise completa)
├── 📄 energy_economics_curated.csv        # Dataset original
├── 📄 energy_economics_treated.csv        # Dataset tratado (legível, não escalado)
├── 📄 energy_economics_ml_ready.csv       # Dataset pronto para ML (padronizado)
└── 📄 README.md                           # Este arquivo
```

---

## Etapas Realizadas no Notebook

### 1. Contextualização
Apresentação do tema, relevância do dataset e problema analisado: a relação entre desenvolvimento econômico, matriz energética e emissões de carbono.

### 2. Descrição do Dataset
Mapeamento completo das 21 variáveis, seus tipos, unidades e papel analítico.

### 3. Análise Exploratória dos Dados (EDA)
- Estatísticas descritivas (média, mediana, desvio padrão, coeficiente de variação)
- Histogramas e distribuições das variáveis-chave
- Evolução temporal dos indicadores globais (1995–2020)
- **Matriz de correlação de Pearson** com heatmap anotado
- **Identificação de outliers** via método IQR + boxplots
- Scatter plot: Renováveis vs Emissões de CO₂

### 4. Preparação dos Dados
| Etapa | Técnica Aplicada |
|---|---|
| Conversão de tipos | `pd.to_numeric(..., errors='coerce')` |
| Nulos — ODA | Preenchimento com `0` (semanticamente correto) |
| Nulos — índices compostos | Mediana por país |
| Nulos — séries temporais | Interpolação linear por país-ano |
| Variável categórica | Label Encoding (`country_name`) |
| Alta assimetria | Transformação logarítmica (`log1p`) |
| Escalonamento | StandardScaler (Z-score) |
| Colunas redundantes | Remoção justificada |

### 5. Dataset Final para ML
O dataset resultante possui **3.354 linhas × 16 colunas**, sem nulos, totalmente padronizado e pronto para algoritmos supervisionados ou não-supervisionados.

---

## Tecnologias Utilizadas

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white)

---

## Como Executar

### Pré-requisitos

- Python 3.10+
- Jupyter Notebook ou JupyterLab

### Instalação das dependências

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

### Executando o notebook

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/projeto-np2-energia.git
cd projeto-np2-energia

# Inicie o Jupyter
jupyter notebook NP2_Energia_Economia_Global.ipynb
```

> Certifique-se de que o arquivo `energy_economics_curated.csv` está na mesma pasta do notebook antes de executar.

---

## Principais Resultados

- As emissões de CO₂ per capita apresentam **distribuição altamente assimétrica** — países produtores de petróleo (Qatar, Kuwait, EAU) são outliers legítimos com valores 4–8× acima da mediana global.
- A **correlação de Pearson** entre CO₂ per capita e pegada ecológica é forte e positiva (~0.75); com o consumo de renováveis, é negativa moderada (~−0.40).
- O consumo médio global de renováveis **decresceu** no período, refletindo a industrialização via combustíveis fósseis em países emergentes.
- A **transformação logarítmica** reduziu a assimetria do PIB de ~15 para ~0.3, tornando a variável viável para modelos lineares.

---

## Critérios de Avaliação Atendidos

| Critério | Status |
|---|---|
| Escolha e apresentação do dataset | ✅ |
| Descrição das variáveis | ✅ |
| Estatísticas descritivas básicas | ✅ |
| Correlação de Pearson | ✅ |
| Identificação e análise de outliers | ✅ |
| Tratamento de dados nulos | ✅ |
| Tratamento de variáveis categóricas | ✅ |
| Normalização / Padronização | ✅ |
| Preparação final para ML | ✅ |
| Relatório técnico no notebook | ✅ |
| Dificuldades e limitações | ✅ |
| Conclusão | ✅ |

---

## Limitações Identificadas

- Dataset encerrado em 2020; não captura a aceleração de renováveis pós-2021.
- O coeficiente de Pearson não captura relações não-lineares (ex.: Curva de Kuznets Ambiental).
- `natural_capital_dependency_index` apresenta valores repetidos entre anos, indicando atualizações infrequentes na fonte.
- A estrutura de painel (país × ano) implica dependência temporal entre observações, o que deve ser considerado na escolha do modelo de ML.

---

## Cronograma do Projeto

| Etapa | Período |
|---|---|
| Escolha do Dataset | 22/04 – 27/04/2026 |
| Checkpoint 1 — Análise Exploratória | 27/04 – 04/05/2026 |
| Checkpoint 2 — Data Preparation | 04/05 – 11/05/2026 |
| **Entrega do Relatório** | **15/05/2026** |
| **Apresentação e Avaliação** | **18/05/2026** |

---

## Autoria

Desenvolvido como parte da disciplina **Ciência de Dados** na **Universidade Christus — Unichristus**.
