# Dataset — German Credit Data

**Arquivo:** `german_credit_data.csv` (1.000 linhas, 9 atributos + variável-alvo `Risk`)

**Origem:** Statlog (German Credit Data), Hofmann, H. (1994), UCI Machine Learning Repository.
https://archive.ics.uci.edu/dataset/144/statlog+german+credit+data — licença CC BY 4.0.

**Versão usada:** versão simplificada publicada no Kaggle ("German Credit Risk - With Target"),
https://www.kaggle.com/datasets/kabure/german-credit-data-with-risk. Ela tem os mesmos 1.000
clientes do original, mas só 9 dos 20 atributos, com nomes legíveis.

## Descrição breve

Clientes de um banco alemão (não identificado) que pediram crédito ao consumidor. Cada linha é um
cliente, classificado como bom (`good`) ou mau (`bad`) pagador. São 700 bons e 300 maus pagadores.

## Atributos

| Coluna | Tipo | Descrição |
|---|---|---|
| Age | Numérico | Idade do cliente (anos) |
| Sex | Categórico | Sexo (male, female) |
| Job | Numérico | Nível de qualificação no trabalho, de 0 (menor) a 3 (maior) |
| Housing | Categórico | Moradia (own, rent, free) |
| Saving accounts | Categórico | Faixa de saldo na poupança (little, moderate, quite rich, rich) |
| Checking account | Categórico | Faixa de saldo na conta corrente (little, moderate, rich) |
| Credit amount | Numérico | Valor do crédito (marcos alemães) |
| Duration | Numérico | Prazo do crédito (meses) |
| Purpose | Categórico | Finalidade do crédito |
| **Risk** | Alvo | `good` (bom pagador) ou `bad` (mau pagador) |

## Valores ausentes

- `Checking account` (39,4% vazio): no dicionário original a categoria é "no checking account",
  então o vazio significa **sem conta corrente**.
- `Saving accounts` (18,3% vazio): no dicionário original a categoria é "unknown / no savings
  account", então o vazio significa **desconhecido ou sem poupança**.

No notebook 02 esses vazios viram as categorias `sem conta` e `desconhecido`.

## Observações

Os dados são públicos e anônimos. A base é de 1994, de um banco alemão, então não representa o
mercado de crédito brasileiro atual.
