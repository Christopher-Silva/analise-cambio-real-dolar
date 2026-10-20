# Análise histórica do câmbio Real/Dólar (1994–2026)

Projeto de análise de dados sobre a cotação do dólar frente ao real desde o início do Plano Real (01/07/1994) até 19/10/2026.

## Fonte dos dados
API de dados abertos do Banco Central do Brasil (SGS, série 1: dólar americano, venda). A API limita cada consulta a 10 anos, por isso a coleta foi dividida em 4 períodos e depois consolidada.

## Status do projeto
- [x] Coleta via API, tratamento e validação dos dados (ETL)
- [ ] Análise exploratória e perguntas de negócio
- [ ] Análise por governo/mandato
- [ ] Dashboard no Power BI

## Etapa 1: ETL
- Coleta em 4 períodos e concatenação em um único DataFrame
- Validações: sem valores nulos, sem datas repetidas, ordem cronológica confirmada
- Tipos corrigidos (data e valor numérico); precisão original de 4 casas decimais mantida
- Resultado: 8.107 registros, exportados em CSV

## Ferramentas
Python, pandas, requests, Google Colab

## Arquivos
- `01_coleta_e_tratamento.ipynb`: notebook da etapa 1
- `cotacao_dolar_1994_2026.csv`: base tratada
