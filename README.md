# Projeto Integrador - TED e PIX

Análise exploratória simples das movimentações mensais por TED e PIX, com dados públicos do Banco Central do Brasil.

## Estrutura

- `dados/Meios de Pagamentos Mensais.csv`: base de entrada.

- `src/analise_pix_ted.py`: tratamento, estatísticas descritivas, tabelas e gráficos.

- `dados/Meios_de_Pagamentos_Mensais_Tratado_Reproduzido.csv`: base tratada gerada pelo script.

- `resultados/tabelas/`: tabelas em CSV.

- `resultados/graficos/`: figuras usadas no relatório.

- `docs/`: relatório técnico e roteiro da apresentação.


## Execução

```bash

python -m venv .venv

# Windows: .venv\Scripts\activate

# Linux/macOS: source .venv/bin/activate

pip install -r requirements.txt

python src/analise_pix_ted.py

```

## Método

A análise utiliza somente estatística descritiva básica: média, mediana, mínimo, máximo, totais, variações percentuais, participação relativa e ticket médio. Não há previsão, regressão ou aprendizado de máquina.


## Unidades

Na base do BCB, as quantidades são apresentadas em milhares de transações e os valores em R$ milhões. O ticket médio em reais é calculado por `(valor / quantidade) * 1.000`.


