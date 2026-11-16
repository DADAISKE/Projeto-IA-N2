# CredScore AI: Decifrando o Risco de Crédito

Projeto da disciplina de Inteligência Artificial (7º CC) — Faculdade de Computação e Informática, Universidade Presbiteriana Mackenzie.
Professor: Prof. Dr. Ivan Carlos Alcântara de Oliveira

## Integrantes

| Nome | RA | E-mail |
|---|---|---|
| Rodrigo Daiske Uehara | 10440295 | 10440295@mackenzista.com.br |

- Artigo final: [`artigo/artigo_final_credscoreai.pdf`](artigo/artigo_final_credscoreai.pdf)
- Vídeo de apresentação: _[colocar aqui o link do YouTube]_

## Sobre o projeto

O projeto compara três modelos de aprendizado de máquina (Regressão Logística, Random Forest e XGBoost) para prever se um cliente de crédito ao consumidor é mau pagador. Depois o melhor modelo é explicado com SHAP e os erros são comparados entre grupos de sexo e de idade.

ODS relacionados: **ODS 8** (Trabalho Decente e Crescimento Econômico) e **ODS 10** (Redução das Desigualdades).

## Dataset

German Credit Data, versão simplificada do [Statlog (German Credit Data)](https://archive.ics.uci.edu/dataset/144/statlog+german+credit+data) do UCI: 1.000 clientes, 9 atributos e a variável-alvo `Risk`. A descrição está em [`dados/dataset.md`](dados/dataset.md).

## Estrutura do repositório

```
├── README.md
├── requirements.txt
├── artigo/
│   ├── artigo_final_credscoreai.pdf     # artigo final (N2)
│   └── artigo_parcial_credscoreai.pdf   # artigo parcial (N1)
├── dados/
│   ├── german_credit_data.csv           # dataset
│   └── dataset.md                       # descrição do dataset
├── notebooks/
   ├── 01_analise_exploratoria.ipynb    # análise exploratória (N1)
   └── 02_modelagem_resultados.ipynb    # treino, avaliação, SHAP e equidade (N2)

```

## Como executar

```
pip install -r requirements.txt
jupyter notebook
```

Abrir os notebooks da pasta `notebooks/` e executar na ordem (01 e depois 02).

## Resultados principais (conjunto de teste, 300 clientes)

| Modelo | Recall | F1 | PR-AUC | Custo (5xFN + FP) |
|---|---|---|---|---|
| Baseline (sempre bom pagador) | 0,000 | 0,000 | 0,300 | 450 |
| Regressão Logística | 0,722 | 0,591 | 0,623 | 190 |
| Random Forest | 0,744 | 0,598 | 0,599 | 182 |
| XGBoost (modelo final) | 0,711 | 0,607 | 0,589 | 187 |

- Os três modelos tiveram desempenho parecido. O XGBoost foi escolhido pela validação cruzada.
- Pelo SHAP, as variáveis mais importantes são a conta corrente, o prazo e o valor do crédito.
- As diferenças de TPR e FPR entre sexos e faixas de idade ficaram abaixo de 0,10, mas os intervalos de confiança são largos.
- Tirar sexo e idade do modelo não melhorou a equidade.

## Aspectos éticos

O dataset é público e anônimo. O modelo foi feito para estudo e não deve ser usado para decidir crédito de verdade: a base é alemã, de 1994, e pequena. O artigo discute a LGPD, a diferença entre explicar e ser justo e as limitações do trabalho.
