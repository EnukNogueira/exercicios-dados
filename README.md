# Exercícios de Análise de Dados: Histórico de Preços de Combustíveis no Brasil

Este repositório foi criado para registrar meus estudos, práticas e evolução em Análise de Dados utilizando Python e a biblioteca Pandas. O projeto principal contido aqui consiste em uma análise exploratória aprofundada da série histórica dos preços de combustíveis no Brasil (abrangendo o período de 2000 a 2021), utilizando dados reais do mercado de revenda.

---

##  Tecnologias Utilizadas

* **Python 3**
* **Pandas**: Manipulação, limpeza, cruzamento e agregação de dados.
* **NumPy**: Suporte matemático subjacente para cálculos de alta performance (`np.float64`).
* **Jupyter Notebook**: Ambiente de desenvolvimento interativo.

---

##  O Desafio Técnico & Aprendizados

Durante a execução dos exercícios, enfrentei e solucionei desafios reais de engenharia e análise de dados que simulam perfeitamente o dia a dia de um analista em produção:

1. **Tratamento de Dados Fragmentados (`pd.concat`):** Inicialmente, os dados estavam divididos em arquivos temporais (`gasolina_2000+.csv` e `gasolina_2010+.csv`). Identifiquei que análises de anos recentes (como 2014 ou 2021) resultavam em valores nulos (`NaN`) porque a base não estava unificada. Solucionei o problema consolidando os arquivos de forma eficiente através do método de concatenação.
2. **Séries Temporais e Tipos de Dados:** Manipulei colunas de data nativas transformando strings em objetos datetime (`pd.to_datetime`) e gerando períodos customizados (`.dt.to_period('M')`).
3. **Filtros Avançados e Precedência de Operadores:** Domínio na aplicação de múltiplos filtros lógicos simultâneos utilizando o operador `&` e o isolamento obrigatório de condições por parênteses `()`.
4. **Análise de Variação Temporal e Janelas:** Utilização de agrupamentos multinível (`.groupby()`) associados à função de deslocamento `.pct_change()` para calcular variações percentuais ano a ano.

---

##  Insights Extraídos do Dataset

Abaixo estão algumas das principais perguntas de negócios respondidas através das consultas desenvolvidas no notebook:

###  Preço Médio da Gasolina (Agosto de 2008)
Utilizando filtros de tempo e produto, o Pandas isolou a média nacional da gasolina comum em um período de estabilidade econômica:
* **Resultado:** `2.601244` (Aproximadamente **R$ 2,60**)

###  Preço Médio em São Paulo (Maio de 2014)
Após corrigir as inconsistências de dados unificando os arquivos e ajustando a busca exata pelas colunas textuais corretas (`ESTADO` em vez de `REGIÃO`), localizou-se o valor exato para o estado de SP:
* **Resultado:** `2.8822` (Aproximadamente **R$ 2,88**)

###  Rompimento da Barreira dos R$ 5,00
Filtramos todas as linhas onde o `PREÇO MÉDIO REVENDA > 5.0` para mapear a disseminação geográfica e a linha do tempo desse impacto econômico:
* **Onde:** Praticamente todo o país (**26 estados** registraram médias acima de 5 reais).
* **Quando:** O fenômeno teve início em **Maio de 2018 (`2018-05`)**, estabilizou em parte de 2019/2020 e acelerou continuamente ao longo de todo o ano de 2021.

###  Análise de Variação Ano a Ano (Rio de Janeiro)
Calculamos a variação percentual anual do preço médio no RJ, identificando os maiores picos de aumento e momentos de deflação:
* **Maior alta histórica:** 2018 (`+18.35%`), impulsionada pelo cenário macroeconômico e greve dos caminhoneiros, seguida de perto por 2021 (`+17.38%`) e 2015 (`+12.94%`).
* **Anos de queda:** O preço médio fechou negativo em 2007 (`-1.14%`) e no ano pandêmico de 2020 (`-1.93%`).

###  Desafio Final: O Ranking de Aumentos (2020 ➔ 2021)
Agrupamos o dataset por `ESTADO` e `ANO` para extrair a variação percentual de todos os estados simultaneamente na virada de 2020 para 2021.
* **Maior Aumento:** **Distrito Federal**, liderando o ranking nacional com uma alta impressionante de **25,66%**, seguido pelo Amapá com **25,36%**.
* **Menor Aumento:** Mato Grosso (`+16.30%`) e Amazonas (`+16.31%`), que mesmo na lanterna do ranking sofreram impactos muito expressivos.
