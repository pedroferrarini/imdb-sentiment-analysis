# # Análise de Sentimentos de Resenhas de Filmes do IMDb

## Sobre o Projeto

Este projeto foi desenvolvido durante a formação em Análise de Dados e Ciência de Dados da TripleTen, com o objetivo de desenvolver modelos de Machine Learning capazes de classificar automaticamente resenhas de filmes como positivas ou negativas.

O projeto foi proposto para a Film Junky Union, uma comunidade de entusiastas de filmes clássicos que busca implementar um sistema automatizado para identificar e categorizar resenhas negativas.

Para solucionar o problema, foram aplicadas técnicas de Processamento de Linguagem Natural (NLP), vetorização de texto com TF-IDF e algoritmos de classificação supervisionada.

O objetivo principal foi desenvolver modelos com F1-score igual ou superior a **0,85**.

## Objetivos

- Realizar análise exploratória dos dados.
- Investigar a distribuição das avaliações positivas e negativas.
- Preparar e normalizar os textos para aplicação de técnicas de NLP.
- Transformar resenhas em representações numéricas utilizando TF-IDF.
- Desenvolver e comparar diferentes modelos de classificação.
- Avaliar o desempenho dos modelos utilizando métricas de classificação.
- Identificar o modelo com melhor desempenho na classificação de sentimentos.

## Conjunto de Dados

O projeto utiliza um conjunto de dados de resenhas de filmes do IMDb, armazenado no arquivo `imdb_reviews.tsv`.

O conjunto contém **47.331 resenhas**, distribuídas entre avaliações positivas e negativas.

### Distribuição das Classes

| Classificação | Quantidade |
|---|---:|
| Negativas (0) | 23.715 |
| Positivas (1) | 23.616 |
| **Total** | **47.331** |

A distribuição das classes é praticamente equilibrada, com aproximadamente 50% de avaliações positivas e 50% de avaliações negativas.

O conjunto de dados já apresenta uma divisão entre treinamento e teste:

- Treinamento: 23.796 registros.
- Teste: 23.535 registros.

## Etapas do Desenvolvimento

### 1. Análise Exploratória dos Dados (EDA)

Foram realizadas análises para compreender as características e a distribuição dos dados, incluindo:

- Quantidade de filmes e resenhas ao longo dos anos.
- Distribuição do número de resenhas por filme.
- Distribuição das avaliações positivas e negativas.
- Comparação das distribuições entre os conjuntos de treinamento e teste.

A análise identificou uma distribuição equilibrada entre as classes, permitindo prosseguir com o treinamento dos modelos.

### 2. Pré-processamento de Texto

Foi realizada a normalização dos textos para preparar as resenhas para os algoritmos de Machine Learning.

As etapas incluíram:

- Conversão dos textos para letras minúsculas.
- Remoção de números e pontuações.
- Remoção de espaços em branco desnecessários.
- Lematização com spaCy em uma das abordagens.
- Tratamento de stopwords em inglês.

### 3. Vetorização com TF-IDF

Foi utilizada a técnica **Term Frequency–Inverse Document Frequency (TF-IDF)** para transformar as resenhas em representações numéricas.

Essa técnica permite identificar a relevância dos termos presentes nos textos, possibilitando sua utilização pelos algoritmos de classificação.

Foram utilizadas abordagens com stopwords do NLTK e com pré-processamento textual utilizando spaCy.

### 4. Treinamento dos Modelos

Foram desenvolvidos três modelos principais de classificação:

- Regressão Logística com TF-IDF.
- Regressão Logística com spaCy e TF-IDF.
- LightGBM com spaCy e TF-IDF.

Também foi desenvolvido um modelo baseline utilizando `DummyClassifier`, como referência para comparação dos resultados.

### 5. Avaliação dos Modelos

Os modelos foram avaliados utilizando as seguintes métricas:

- **Accuracy:** proporção de classificações corretas.
- **F1-score:** equilíbrio entre precisão e recall.
- **APS (Average Precision Score):** avaliação do desempenho na curva precisão-revocação.
- **ROC AUC:** capacidade de distinguir as classes positivas e negativas.

## Resultados dos Modelos

Os resultados obtidos no conjunto de teste foram:

| Modelo | Accuracy | F1-score | APS | ROC AUC |
|---|---:|---:|---:|---:|
| Baseline | 0,50 | 0,00 | 0,50 | 0,50 |
| Regressão Logística + TF-IDF | 0,88 | **0,88** | 0,95 | 0,95 |
| Regressão Logística + spaCy + TF-IDF | 0,87 | 0,87 | 0,94 | 0,95 |
| LightGBM + spaCy + TF-IDF | 0,86 | 0,86 | 0,93 | 0,93 |

### Melhor Modelo

A **Regressão Logística com TF-IDF** apresentou o melhor desempenho geral, alcançando F1-score de **0,88** no conjunto de teste.

O resultado superou a meta estabelecida de 0,85.

Os outros dois modelos também atingiram o desempenho mínimo esperado, demonstrando resultados satisfatórios na classificação de sentimentos.

## Testes com Resenhas Próprias

Além da avaliação com os dados de teste, foram utilizadas oito resenhas próprias em inglês para verificar o comportamento dos modelos diante de novos exemplos.

Os três classificadores concordaram em cinco das oito classificações.

Nas outras três avaliações, foram identificadas divergências entre os modelos, principalmente em situações envolvendo negações e opiniões com sentimentos mistos.

Essa etapa demonstrou que um bom desempenho nas métricas gerais não garante classificações corretas em todos os exemplos individuais.

## Conclusão

O projeto demonstrou a aplicação de técnicas de Processamento de Linguagem Natural e Machine Learning na classificação automática de sentimentos em resenhas de filmes.

Entre as abordagens desenvolvidas, a Regressão Logística com TF-IDF apresentou o melhor resultado, alcançando F1-score de 0,88 e superando a meta estabelecida.

A comparação também demonstrou que a lematização e a mudança de algoritmo não necessariamente proporcionam melhores resultados para todos os conjuntos de dados textuais.

Outro ponto identificado foi a dificuldade dos modelos em interpretar determinadas negações e opiniões mistas. A remoção de palavras como "not" durante o pré-processamento pode comprometer o significado original das resenhas.

Também foi observado um leve overfitting, indicando uma diferença entre os resultados obtidos nos dados de treinamento e teste.

Dessa forma, a Regressão Logística com TF-IDF foi selecionada como a abordagem mais adequada entre as avaliadas para o problema proposto.

## Tecnologias e Bibliotecas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- NLTK
- spaCy
- Scikit-learn
- LightGBM
- Jupyter Notebook

## Competências Desenvolvidas

- Análise Exploratória de Dados (EDA).
- Limpeza e pré-processamento de dados textuais.
- Processamento de Linguagem Natural (NLP).
- Vetorização de textos com TF-IDF.
- Lematização com spaCy.
- Classificação supervisionada.
- Regressão Logística.
- LightGBM.
- Avaliação e comparação de modelos de Machine Learning.
- Interpretação de métricas e resultados.

---
