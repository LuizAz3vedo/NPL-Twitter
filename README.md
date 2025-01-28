# NPL-Twitter

# Análise e Classificação de Tweets Relacionados a Desastres

Este projeto foi desenvolvido como parte de um desafio de estágio em uma empresa que desenvolve soluções de análise de dados. O objetivo principal é classificar tweets em duas categorias: **0** para tweets não relacionados a desastres reais e **1** para tweets relacionados a desastres reais. Para isso, foram utilizadas técnicas de manipulação de dados, processamento de linguagem natural (NLP), estatística e aprendizado de máquina.

## Contexto

O conjunto de dados fornecido consiste em tweets que podem ou não estar relacionados a desastres reais. A tarefa é analisar esses tweets e classificá-los corretamente. Os dados estão organizados em três arquivos:

- **train.csv**: Contém os dados de treinamento, incluindo características e variáveis-alvo.
- **test.csv**: Contém os dados de teste, sem as variáveis-alvo.
- **sample_submission.csv**: Contém as respostas para o arquivo de teste, utilizado para validação.

As colunas presentes nos dados são:

- **id**: Identificador único do tweet.
- **keyword**: Palavra-chave associada ao tweet.
- **location**: Localização de onde o tweet foi postado.
- **text**: Texto do tweet.
- **target**: Categoria do tweet (0 ou 1).

## Objetivo

O objetivo do projeto é:

1. **Explorar os dados**: Entender a distribuição das classes, frequência das palavras-chave, etc.
2. **Pré-processar os dados**: Limpar e preparar os dados para análise, incluindo remoção de NaNs, normalização de texto, tokenização e remoção de palavras irrelevantes.
3. **Analisar os dados**: Descobrir padrões e relações relevantes, como a relação entre palavras-chave e categorias.
4. **Modelagem**: Desenvolver um modelo de aprendizado de máquina para classificar os tweets.
5. **Interpretação dos resultados**: Apresentar os resultados de forma clara, com visualizações que destacam as principais descobertas.

## Metodologia

### Exploração de Dados

A análise inicial dos dados incluiu a verificação da distribuição das classes, a frequência das palavras-chave e a identificação de possíveis padrões nos textos dos tweets.

### Pré-processamento de Dados

Os dados foram limpos e preparados para análise, incluindo:

- Remoção de valores nulos (NaNs).
- Normalização do texto (lowercasing, remoção de pontuação, etc.).
- Tokenização e remoção de stopwords.

### Modelagem

Foram testados diferentes modelos de classificação, incluindo:

- **LinearSVC**
- **Logistic Regression**
- **Naive Bayes (NB)**

O modelo final escolhido foi o **LinearSVC**, que foi otimizado utilizando **RandomizedSearchCV** para encontrar os melhores hiperparâmetros.

### Avaliação do Modelo

O desempenho do modelo foi avaliado utilizando métricas como **F1-score**, **AUC-ROC**, e **matriz de confusão**. O modelo foi capaz de classificar os tweets com uma precisão considerável, conforme mostrado no relatório de classificação e na curva ROC.

## Resultados

O modelo final apresentou um bom desempenho na classificação dos tweets, com um **F1-score** de **X** e uma **AUC-ROC** de **Y**. A matriz de confusão mostrou que o modelo foi capaz de distinguir corretamente entre tweets relacionados a desastres e tweets não relacionados.

### Exemplo de Teste Manual

Para testar o modelo manualmente, foi fornecido um exemplo de tweet:

```python
x_test_manual = 'airplane%20accident,France,Experts in France begin examining airplane debris found on Reunion Island: French air accident experts on Wedn'
x_test_manual_transformed = best_pipeline.named_steps['tfidf'].transform([x_test_manual])
y_pred_test_manual = best_pipeline.named_steps['clf'].predict(x_test_manual_transformed)
print(f"Resultado do teste manual: {y_pred_test_manual[0]}")
```
Resultado do teste manual: 1
