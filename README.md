# Foundation Models vs. Algoritmos Clássicos em Sensoriamento Remoto

Repositório desenvolvido para o trabalho final da disciplina de **Introdução à Ciência de Dados**, com o objetivo de realizar um estudo comparativo entre abordagens de *Foundation Models* e algoritmos clássicos de aprendizado de máquina aplicados à classificação de uso e cobertura da terra na Amazônia.

---

## 👩‍💻 Desenvolvedoras

* **[Carla Almeida / Sofia Sena Tavares]**

---

## 🎯 Objetivo do Estudo

Avaliar e comparar o desempenho preditivo, o custo computacional, a capacidade de generalização e a robustez de diferentes arquiteturas de modelagem utilizando séries temporais de imagens de satélite (Sentinel-2) obtidas via arquitetura STAC, tendo como base espacial unidades de referência (*tiles*) no bioma amazônico.

---

## 🤖 Modelos Avaliados

O estudo contrasta duas filosofias distintas de aprendizado de máquina:

1. **Foundation Models:** Modelos de grande escala capazes de processar sequências temporais nativas de observação da terra.
2. **Algoritmos Clássicos (Estado da Arte):** Modelos baseados em árvores de decisão e aprendizado tabular que utilizam engenharia de atributos estatísticos, incluindo:
   * **Random Forest (RF)**
   * **XGBoost**
   * **LightGBM**
   * **CatBoost**
   * **TabPFN**

---

## ⚙️ Fluxo Metodológico

* **Delimitação Espacial:** Uso de malhas de *tiles* (ex: `C56L49`) e bibliotecas geoespaciais (`geopandas`, `shapely`) para recorte e mascaramento de áreas de interesse do DETER.
* **Extração via STAC:** Conexão com catálogos abertos (AWS *Earth Search*) para aquisição otimizada de bandas espectrais (`red`, `nir`, `scl`) do Sentinel-2 sem necessidade de *downloads* massivos prévios.
* **Processamento e Filtragem:** Aplicação de máscara de nuvens, cálculo do índice de vegetação NDVI e interpolação linear temporal.
* **Engenharia de Atributos:** Geração de métricas estatísticas anuais (média, desvio padrão, mínimos, máximos e percentis) destinadas exclusivamente aos algoritmos clássicos.

---

## 📁 Estrutura do Repositório

```text
├── data/                  # Dados tabulares e amostras de treino
├── notebooks/             # Jupyter Notebooks com o pipeline de extração e modelagem
├── src/                   # Scripts auxiliares e funções de processamento
├── outputs/               # Resultados, métricas e artefatos gerados
└── README.md              # Documentação do projeto
---

## 🛠️ Requisitos e Execução

### Pré-requisitos
Certifique-se de ter o [Anaconda](https://www.anaconda.com/) ou o [Miniconda](https://docs.conda.io/) instalados em sua máquina para gerenciar o ambiente virtual e as dependências geoespaciais.

### Dependências Principais (`environment.yml`)
O projeto utiliza bibliotecas voltadas para manipulação de dados tabulares, computação científica, séries temporais e processamento geoespacial em nuvem:
* **Python** (versão 3.11 ou superior)
* **Pandas** e **NumPy** (manipulação de dados)
* **Xarray** (manipulação de cubos de dados multidimensionais)
* **PySTAC Client** (`pystac_client`) e **Stackstac** (`stackstac`) (consulta ao catálogo STAC e criação de cubos sob demanda)
* **Geopandas** e **Shapely** (manipulação de geometrias e máscaras espaciais)
* **Scikit-Learn / XGBoost / LightGBM / CatBoost** (modelos de aprendizado de máquina clássicos)

---

### 💻 Passo a Passo para Execução

1. **Clone o repositório e acesse a pasta:**
   ```bash
   git clone [https://github.com/seu-usuario/foundation-vs-classical-ml.git](https://github.com/seu-usuario/foundation-vs-classical-ml.git)
   cd foundation-vs-classical-ml
