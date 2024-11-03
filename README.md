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

## Exemplo de Uso
    import pandas as pd
    from grangerscope import GrangerScope  # Importe a classe

    # Suponha que df seja um DataFrame com as colunas 'x' e 'y'
    df = pd.DataFrame({
        'x': [...],  # Série temporal da variável x
        'y': [...]   # Série temporal da variável y
    })

    # Defina o lag máximo desejado para a análise
    max_lag = 5

    # Instancie e execute a análise com GrangerScope
    analyzer = GrangerScope(df, max_lag)

## Exemplo de Saída
Após a execução da análise, você verá:

- Relatório de Estacionaridade: Exibe os p-valores dos testes ADF e KPSS e indica se a série foi diferenciada para se tornar estacionária.
- Teste de Granger: Um relatório com os p-valores para cada lag testado, indicando quais lags são significativos.
- Critérios de Informação: Gráficos com critérios AIC, BIC, HQIC e FPE para os modelos restritos e irrestritos, auxiliando na escolha do melhor lag para a análise causal.

## Métodos Principais

 - ``validate_lag``: Verifica se o lag máximo é adequado, considerando o tamanho do conjunto de dados.
 - ``run_analysis``: Executa todo o pipeline de análise, incluindo testes de estacionaridade, análise de Granger, ajuste de modelos VAR e geração de relatórios e gráficos.
 - ``generate_report``: Gera um relatório detalhado com resultados dos testes de estacionaridade, p-valores de Granger e critérios de seleção de lag.
 - ``plot_results``: Plota gráficos dos p-valores e critérios de informação para facilitar a visualização dos resultados.


## Contato
Para perguntas ou sugestões, entre em contato com o desenvolvedor no william-johnny@hotmail.com.
