# Reconhecimento de Dígitos - Projeto de Apredizagem de Maquina - 2023

## Introdução

O reconhecimento de dígitos escritos à mão é um problema clássico de classificação na área de visão computacional. Este projeto utiliza o dataset MNIST, contendo imagens de dígitos escritos à mão (0-9), para comparar técnicas de aprendizado de máquina e construir novas soluções.

## Dataset MNIST Adaptado

Os arquivos `train.csv` e `test.csv` contêm imagens em escala de cinza dos dígitos 0, 1, 4 e 5 escritos à mão. Cada imagem é composta por 28x28 pixels, totalizando 784 pixels. Os valores de cada pixel variam de 0 a 255, onde valores mais altos representam pixels mais escuros.

### Estrutura dos Dados

- `train.csv`: 785 colunas (label + 784 pixels).
- `test.csv`: Mesmo formato do arquivo de treino.

### Redução da Dimensão das Amostras

Para reduzir a complexidade dos dados, sintetizamos as imagens em duas características principais: intensidade e simetria. 

- **Intensidade**: Soma dos tons de cinza de cada pixel dividida por 255.
- **Simetria**: Diferença entre pixels em eixos vertical e horizontal.

Arquivos gerados: `train_redu.csv` e `test_redu.csv` contendo `label`, `intensidade` e `simetria`.

## Classificadores

Três modelos lineares de aprendizado de máquina foram implementados para a classificação dos dígitos:

1. Perceptron
2. Regressão Linear
3. Regressão Logística

### Classificação dos Dígitos 1 x 5

Para o modelo Perceptron (classificação binária), classificamos os dígitos 1 e 5:

- Filtramos os dados para conter apenas dígitos 1 e 5.
- Plotamos os dados de treino em um gráfico 2D (intensidade x simetria).
- Treinamos os três classificadores com os dados filtrados.
- Testamos os classificadores e geramos matrizes de confusão e relatórios de eficácia.

### Classificador de Dígitos Completo

Implementamos a estratégia "um contra todos" para classificar os quatro dígitos (0, 1, 4 e 5):

1. Criamos classificadores binários para cada dígito contra todos os outros.
2. Utilizamos as funções hipótese para classificar os dígitos em novas imagens de teste.

### Comparação entre os Classificadores

Comparamos os classificadores utilizando as métricas de acurácia, precisão, recall e F1 score.

## Implementações Avançadas

- Heurística weight decay para regularizar o parâmetro lambda na regressão logística.
- Implementação de uma ordem de teste otimizada para melhor acurácia global.

## Como Executar

1. Clone este repositório.
2. Execute os scripts para gerar os arquivos `train_redu.csv` e `test_redu.csv`.
3. Treine os modelos utilizando os arquivos reduzidos.
4. Avalie os modelos com os dados de teste.
