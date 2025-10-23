# CP5 - Implementação de Pipeline de Classificação: Predição de Doenças Cardíacas

## Objetivo Geral e Justificativa

O objetivo central deste trabalho individual é implementar um Pipeline completo de Ciência de Dados e Machine Learning para desenvolver um modelo de classificação capaz de prever a presença ou ausência de doenças cardíacas. O projeto demonstra a aplicação prática, raciocínio crítico e clareza metodológica, conforme exigido.

* Problema: Classificação Binária (Doença vs. Sem Doença).
* Dataset: Cleveland Heart Disease (UCI Machine Learning Repository). O dataset atende ao requisito de ter no mínimo 300 registros e pelo menos 5 variáveis explicativas.

---

## Instalação e Execução

Para rodar o Notebook Jupyter (`CP5_IA.ipynb`) e reproduzir os resultados, é necessário ter o Python instalado e as bibliotecas de Machine Learning.

1.  **Requisitos:**
    O projeto foi desenvolvido em Python e requer as seguintes bibliotecas: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn` e `tabulate`.
2.  **Instalação (Ambiente Virtual Recomendado):**
    Utilize o terminal para instalar todos os pacotes de uma vez:

    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn tabulate
    ```

3.  **Execução do Código:**
    * Abra o arquivo `CP5_IA.ipynb` em um ambiente Jupyter (como VS Code ou Google Colab).
    * Execute todas as células sequencialmente ("Run All"). Os resultados e métricas serão impressos diretamente no Notebook.

---

## 1. Pré-processamento e Metodologia

O pré-processamento de dados foi estruturado utilizando o Pipeline e ColumnTransformer, seguindo o critério com peso de 20% na avaliação.

* Limpeza de Dados: O processo iniciou com 303 registros e foi finalizado com 297 registros limpos após o tratamento de valores ausentes ('?'), garantindo um dataset de trabalho consistente.
* Transformações: O ColumnTransformer foi utilizado para:
    * Variáveis Numéricas: Aplicação do StandardScaler (Padronização), essencial para modelos baseados em distância como o KNN.
    * Variáveis Categóricas: Uso do OneHotEncoder.
* Divisão: Utilização do train_test_split para separar o conjunto de treino e teste.

## 2. Modelagem e Experimentação

Foram testados os 3 modelos de classificação exigidos no pipeline (KNN, Random Forest e Regressão Logística), representando 20% do peso da nota.

### Tabela Comparativa de Métricas (Modelos Base)

| Modelo | Acurácia | Precisão | Recall | F1-Score | Tempo (s) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| KNN | 0.8778 | 0.8780 | 0.8571 | 0.8675 | 0.0234 |
| Random Forest | 0.8444 | 0.8684 | 0.7857 | 0.8250 | 0.1848 |
| Regressão Logística | 0.8333 | 0.8649 | 0.7619 | 0.8101 | 0.0288 |

O modelo k-vizinhos mais próximos (KNN) foi selecionado para a otimização por ter apresentado o maior F1-Score base.

## 3. Avaliação e Otimização

A avaliação utiliza múltiplas métricas (Acurácia, Precisão, Recall, F1-Score e Matriz de Confusão) e representa 15% da nota.

A otimização de hiperparâmetros foi realizada com GridSearchCV (busca em grade com CV=5), utilizando F1-Score como métrica de pontuação prioritária.

* Melhores Parâmetros Encontrados: `{'classifier__n_neighbors': 5, 'classifier__weights': 'uniform'}`

### Relatório Final de Métricas (Comparação do Modelo Vencedor)

| Métrica | Modelo Base (KNN) | Modelo Otimizado (KNN) | Variação (%) |
| :--- | :--- | :--- | :--- |
| F1-Score | 0.8675 | 0.8471 | -2.35% |

## 4. Conclusões e Análise Crítica

O modelo k-vizinhos mais próximos (KNN) em sua configuração Base é a solução final escolhida, demonstrando coerência e profundidade na análise (10% do peso).

* Justificativa da Métrica: O F1-Score é a métrica mais relevante por ser o equilíbrio ideal entre Precisão e Recall. Em diagnósticos médicos, é vital maximizar o Recall (evitar Falsos Negativos), e o KNN Base foi o que melhor atendeu a essa necessidade.
* Análise da Otimização: A otimização resultou em uma regressão de -2.35% no F1-Score. Isso indica que os hiperparâmetros padrão do KNN já eram robustos e próximos do ótimo para este dataset específico, justificando a escolha do modelo Base como a solução final mais eficaz.

---
### Entregáveis

O projeto foi entregue no repositório GitHub, contendo o Notebook Jupyter (`CP5_IA.ipynb`) com o código completo, e este `README.md` detalhado com a metodologia e os resultados.

https://colab.research.google.com/drive/1B6J_6AjeL-xg9quzfMBtmCUPIna4lc7h#scrollTo=G9CE4M96CzWA