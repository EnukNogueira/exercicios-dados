# Exercícios de Análise de Dados: Preços de Combustíveis no Brasil (2000–2021)

Análise exploratória em Python com Pandas e NumPy sobre a série histórica de preços de combustíveis no Brasil, com foco em padrões temporais, variações regionais e marcos econômicos.

---

## Sobre o projeto

Este repositório documenta exercícios práticos de análise de dados aplicados a um dataset real do mercado de revenda de combustíveis brasileiro, cobrindo mais de duas décadas de histórico. O foco está tanto na extração de insights quanto no domínio técnico das operações com Pandas: merges, séries temporais, filtros avançados e vetorização.

---

## Tecnologias utilizadas

- **Python 3**
- **Pandas** — manipulação, limpeza, cruzamento e agregação de dados
- **NumPy** — suporte matemático de alta performance (`np.float64`)
- **Jupyter Notebook** — desenvolvimento e documentação interativa

---

## Estrutura do repositório

```
exercicios-dados/
├── exercicios-pandas.ipynb     # Notebook principal com todos os exercícios
├── gasolina_2000+.csv          # Dados de 2000 a 2009
└── gasolina_2010+.csv          # Dados de 2010 a 2021
```

---

## Principais desafios técnicos resolvidos

**Dados fragmentados em arquivos temporais** — os dois CSVs precisavam ser unificados via `pd.concat()` antes de qualquer análise. Consultas a anos recentes retornavam NaN sem essa etapa.

**Séries temporais** — conversão de strings para objetos `datetime` com `pd.to_datetime()` e geração de períodos mensais com `.dt.to_period('M')`.

**Filtros booleanos com múltiplas condições** — cada condição isolada entre parênteses `()` e unida com o operador `&` para respeitar a precedência do Python.

**Variação percentual temporal** — uso de `.groupby()` multinível combinado com `.pct_change()` para calcular variações ano a ano por estado.

---

## Insights extraídos

**Preço médio nacional em agosto de 2008** → R$ 2,60

**Preço médio em São Paulo em maio de 2014** → R$ 2,88

**Rompimento da barreira dos R$ 5,00** — fenômeno iniciado em maio de 2018, com 26 estados registrando médias acima de R$ 5,00, acelerando ao longo de todo o ano de 2021.

**Maiores altas históricas no Rio de Janeiro:**

| Ano | Variação |
|---|---|
| 2018 | +18,35% (greve dos caminhoneiros) |
| 2021 | +17,38% |
| 2015 | +12,94% |

**Anos de queda no RJ:** 2007 (−1,14%) e 2020 (−1,93%, efeito pandemia).

**Ranking de maiores aumentos em 2020→2021:**
- Distrito Federal: +25,66% (1º lugar)
- Amapá: +25,36% (2º lugar)
- Mato Grosso: +16,30% (menor aumento, ainda expressivo)

---

## Como executar

```bash
# Clone o repositório
git clone https://github.com/EnukNogueira/exercicios-dados.git
cd exercicios-dados

# Instale as dependências
pip install pandas numpy jupyter

# Abra o notebook
jupyter notebook exercicios-pandas.ipynb
```

---

## Autor

**Enuk Nogueira** — Desenvolvedor focado em Engenharia de Dados e Automação de Processos

[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/enuknogueira/)
[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/EnukNogueira)
