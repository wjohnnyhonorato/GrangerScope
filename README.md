# GrangerScope

**GrangerScope** é uma classe em Python que realiza uma análise de causalidade de Granger detalhada entre duas séries temporais, combinando testes de estacionaridade (ADF e KPSS), testes de causalidade de Granger e modelos de Vetores Autorregressivos (VAR). Ela fornece uma análise automatizada com relatórios e visualizações de critérios de seleção de lags.

## Descrição

O objetivo do GrangerScope é ajudar a identificar relações de precedencia temporal entre duas variáveis em séries temporais. A classe aplica diferenciações para garantir a estacionaridade, realiza testes de causalidade de Granger em diferentes lags e ajusta modelos VAR para avaliar a qualidade do ajuste. Com isso, ela fornece insights detalhados sobre quais lags melhor explicam a causalidade e os critérios de informação associados.

## Funcionalidades

- **Testes de Estacionaridade**: Aplicação dos testes ADF e KPSS para avaliar e ajustar a estacionaridade das séries.
- **Teste de Causalidade de Granger**: Realiza o teste de causalidade de Granger para vários lags, verificando se uma variável ajuda a prever a outra.
- **Modelagem VAR**: Ajusta modelos VAR e AR (modelo restrito) para cada lag até o máximo especificado, calculando métricas como AIC, BIC, HQIC e FPE.
- **Relatório e Visualização**: Gera relatórios de p-valores dos testes e gráficos dos critérios de informação e p-valores, ajudando na interpretação dos resultados.

## Instalação

1. Clone este repositório:
   ```bash
   git clone https://github.com/wjohnnyhonorato/GrangerScope.git

2. Instale as dependências necessárias:
   ```bash
   pip install -r requirements.txt

3. Importe a classe GrangerScope  
O arquivo que vai realizar a importação da classe precisa estar no mesmo nivel da pasta grangerscope
   ```bash
   from grangerscope import GrangerScope

## Exemplo de Uso
    import numpy as np
    import pandas as pd

    # Criando um DataFrame exemplo com as colunas 'x' e 'y'
    np.random.seed(42)
    n = 150  # número de pontos da série
    # Série X: uma sequência temporal com ruído
    x = np.cumsum(np.random.normal(loc=0, scale=1, size=n))
    # Série Y: depende dos valores passados de X mais um ruído adicional
    y = [0] * n
    for i in range(2, n):
        y[i] = 0.5 * x[i - 1] + 0.3 * x[i - 2] + np.random.normal(0, 1)
    # Criação do DataFrame
    df = pd.DataFrame({'x': x, 'y': y})


    # Defina o lag máximo desejado para a análise
    max_lag = 5
    # Instancie e execute a análise com GrangerScope, um relatório consolidado será exibido
    analyzer = GrangerScope(df, max_lag)

## Exemplo de Saída
Após a execução da análise, você verá:

- Relatório de Estacionaridade: Exibe os p-valores dos testes ADF e KPSS e indica se a série foi diferenciada para se tornar estacionária.
- Teste de Granger: Um relatório com os p-valores para cada lag testado, indicando quais lags são significativos.
- Critérios de Informação: Gráficos com critérios AIC, BIC, HQIC e FPE para os modelos restritos e irrestritos, auxiliando na escolha do melhor lag para a análise causal.

   ```plaintext 
   RESULTADOS DA ANÁLISE DE GRANGER E LAG ÓTIMO
   
   Resultados dos Testes de Estacionaridade Iniciais (ADF e KPSS)
   Série      ADF p-valor    KPSS p-valor  Estacionaridade
   -------  -------------  --------------  -----------------
   x             0.374183            0.01  Não Estacionária
   y             0.303492            0.01  Não Estacionária

   Número de diferenciações aplicadas para tornar as séries estacionárias: 1

   Resultados do Teste de Granger (Lags Significativos)
   Lag    p-valor F    p-valor Chi-Square
   -----  -----------  --------------------
      1  0.0228984             0.0201647
      2  1.03577e-07           7.67136e-09
      3  7.00358e-09           9.29781e-11
      4  1.90265e-09           5.51498e-12
      5  1.81332e-10           4.60367e-14

   Lags Ótimos Baseados em Critérios de Informação (Apenas Lags Significativos)
   Critério      Lag Ótimo    Lag Ajustado
   ----------  -----------  --------------
   AIC                   5               6
   BIC                   2               3
   HQIC                  5               6
   FPE                   5               6


<p align="center">
  <img src="images\granger_test.png">
</p>
<p align="center">
  <img src="images\criterios_informacao.png">
</p>
<p align="center">
  <img src="images\fpe.png">
</p>


## Métodos Principais

 - ``validate_lag``: Verifica se o lag máximo é adequado, considerando o tamanho do conjunto de dados.
 - ``run_analysis``: Executa todo o pipeline de análise, incluindo testes de estacionaridade, análise de Granger, ajuste de modelos VAR e geração de relatórios e gráficos.
 - ``generate_report``: Gera um relatório detalhado com resultados dos testes de estacionaridade, p-valores de Granger e critérios de seleção de lag.
 - ``plot_results``: Plota gráficos dos p-valores e critérios de informação para facilitar a visualização dos resultados.


## Contato
Para perguntas ou sugestões, entre em contato com o desenvolvedor no william-johnny@hotmail.com.

