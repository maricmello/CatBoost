<div align="center">

# CatBoost aplicado à previsão de churn

**Atividade Final de Aprendizado de Máquina I**
FATEC Jundiaí · Ciência de Dados

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![CatBoost](https://img.shields.io/badge/CatBoost-1.2-FFCC00)
![scikit--learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-interpretação-D9682B)

</div>

## Sobre o trabalho

Investigação da técnica **CatBoost** (Modalidade A da atividade): uma biblioteca de gradient boosting criada pela Yandex que trata variáveis categóricas direto no modelo, usando *Ordered Target Statistics* para evitar o vazamento do alvo.

A técnica foi testada num problema real de **previsão de cancelamento de clientes (churn)** de telecom, com a base pública [IBM Telco Customer Churn](https://github.com/IBM/telco-customer-churn-on-icp4d): 7.043 clientes, 16 de 19 variáveis categóricas e 26,5% de churn.

| Aluna | Professor | Tema |
|:--|:--|:--|
| Mariana Costa de Mello | Mateus Guilherme Fuini | CatBoost |

## Principais resultados

| | Resultado |
|:--|:--|
| ROC-AUC no teste | **0,845** (IC 95%: 0,824 a 0,865), contra 0,737 de uma regra de negócio simples |
| Churns encontrados | **71%**, com 57% de acerto nas ações de retenção (limiar 0,37) |
| Curva de ganho | Os 20% de clientes de maior risco concentram **51%** dos cancelamentos |
| Vazamento (E5) | Uma coluna de ruído derrubou a AUC para 0,66 com target encoding simples; no CatBoost ficou em 0,84 |
| Comparação | Melhor média entre os modelos da disciplina, mas só 0,004 de AUC acima da Regressão Logística |

## Estrutura

```
├── Notebooks/
│   ├── 01_Introducao.ipynb
│   ├── 02_Fundamentacao_Teorica.ipynb
│   ├── 03_Aplicacoes_Praticas.ipynb
│   ├── 04_Implementacao.ipynb
│   ├── 05_Experimentacao.ipynb
│   ├── 06_Avaliacao.ipynb
│   ├── 07_Analise_Critica.ipynb
│   └── 08_Conclusao.ipynb
├── CatBoost_Apresentacao_Mariana_Costa_de_Mello.pdf
└── CatBoost_Apresentacao_Mariana_Costa_de_Mello.pptx
```

| # | Notebook | Conteúdo |
|:--|:--|:--|
| 1 | [Introdução](Notebooks/01_Introducao.ipynb) | Técnica, problema e dados |
| 2 | [Fundamentação teórica](Notebooks/02_Fundamentacao_Teorica.ipynb) | Boosting, Ordered TS, Ordered Boosting, árvores simétricas e hiperparâmetros |
| 3 | [Aplicações práticas](Notebooks/03_Aplicacoes_Praticas.ipynb) | Casos reais e exemplos de regressão e ranqueamento |
| 4 | [Implementação](Notebooks/04_Implementacao.ipynb) | Qualidade dos dados, EDA, baselines e primeiro modelo |
| 5 | [Experimentação](Notebooks/05_Experimentacao.ipynb) | Cinco experimentos com parâmetros e dados |
| 6 | [Avaliação](Notebooks/06_Avaliacao.ipynb) | Resultado no teste, limiar, calibração, SHAP e análise de erros |
| 7 | [Análise crítica](Notebooks/07_Analise_Critica.ipynb) | Comparação com Regressão Logística, KNN, Árvore, Random Forest e Gradient Boosting |
| 8 | [Conclusão](Notebooks/08_Conclusao.ipynb) | Síntese, aprendizados e referências |

A apresentação está em [PDF](CatBoost_Apresentacao_Mariana_Costa_de_Mello.pdf) (abre direto no GitHub) e em [PowerPoint](CatBoost_Apresentacao_Mariana_Costa_de_Mello.pptx).

## Como executar

Cada notebook é independente: instala as bibliotecas e baixa a base sozinho.

**No Google Colab:** abra o notebook e use *Ambiente de execução > Executar tudo*.

**Localmente:**

```bash
pip install catboost shap category_encoders scikit-learn pandas matplotlib seaborn jupyter
jupyter notebook
```

Todos os resultados usam semente 42 e a mesma divisão estratificada (60% treino, 20% validação, 20% teste). O conjunto de teste só é usado nos notebooks 6 e 7.

## Referências principais

- PROKHORENKOVA, L. et al. *CatBoost: unbiased boosting with categorical features*. NeurIPS, 2018.
- DOROGUSH, A. V.; ERSHOV, V.; GULIN, A. *CatBoost: gradient boosting with categorical features support*. arXiv:1810.11363, 2018.
- FRIEDMAN, J. H. *Greedy function approximation: a gradient boosting machine*. Annals of Statistics, 2001.
- LUNDBERG, S.; LEE, S.-I. *A unified approach to interpreting model predictions*. NIPS, 2017.
- [Documentação do CatBoost](https://catboost.ai/docs/)

A lista completa está no [Notebook 8](Notebooks/08_Conclusao.ipynb).
