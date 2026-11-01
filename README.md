# Análise histórica do câmbio Real/Dólar (1994–2026)

Projeto de análise de dados sobre a cotação do dólar frente ao real desde o início do Plano Real (01/07/1994) até 19/10/2026.

## Fonte dos dados
API de dados abertos do Banco Central do Brasil (SGS, série 1: dólar americano, venda). A API limita cada consulta a 10 anos, por isso a coleta foi dividida em 4 períodos e depois consolidada.

## Status do projeto
- [x] Coleta via API, tratamento e validação dos dados (ETL)
- [ ] Análise exploratória e perguntas de negócio
- [ ] Análise por governo/mandato
- [x] Dashboard no Power BI

## Etapa 1: ETL
- Coleta em 4 períodos e concatenação em um único DataFrame
- Validações: sem valores nulos, sem datas repetidas, ordem cronológica confirmada
- Tipos corrigidos (data e valor numérico); precisão original de 4 casas decimais mantida
- Resultado: 8.107 registros, exportados em CSV

## Etapa 2: Dashboard no Power BI
Primeira versão do dashboard, construída sobre a base tratada na Etapa 1.

![Dashboard v1](dashboard_v1.png)

### O que o dashboard mostra
- Cotação atual, inicial, máxima e mínima da série
- Amplitude (máxima − mínima): R$ 5,38
- Valorização do dólar desde 01/07/1994: **405,64%**
- Desvalorização do real frente ao dólar: **cerca de 80%** (R$ 1,00 valia US$ 1,00 em 1994 e hoje vale cerca de US$ 0,20)
- Gráfico de linha com a cotação diária de 1994 a 2026
- Gráfico de colunas com a cotação média por ano

### Modelagem de dados
Tabela de calendário (criada em DAX) relacionada à tabela de cotações por data, em relação de um para muitos com filtro em direção única. Isso permite filtrar por ano, década e outros períodos, e é a base para as próximas análises.

![Modelagem de dados](modelagem_v1.png)

### Medidas em DAX
Cotação Atual, Cotação Inicial, Maior Cotação, Menor Cotação, Amplitude, Variação Percentual Total (valorização do dólar) e Desvalorização Percentual do Real.

### Validação
Os números do Power BI foram conferidos com os do Python: 8.107 registros, primeira cotação de R$ 1,00 (01/07/1994) e última de R$ 5,0564 (19/10/2026).

### Observações
- Até 1999 o câmbio era controlado por bandas, o que explica a linha quase reta no início da série. A partir da flutuação, o comportamento muda.
- A análise é descritiva: o dashboard mostra o que aconteceu com a cotação, sem atribuir causas.
- Os valores são exibidos com 2 casas decimais, mas os dados mantêm a precisão original de 4 casas.

## Ferramentas
Python, pandas, requests, Google Colab, Power BI

## Arquivos
- `01_coleta_e_tratamento.ipynb`: notebook da etapa 1
- `cotacao_dolar_1994_2026.csv`: base tratada
