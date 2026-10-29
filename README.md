Classificador de Sentimentos de Críticas de Filmes — IMDB

Este projeto utiliza Deep Learning para classificar críticas de filmes do IMDB como positivas ou negativas. A solução foi desenvolvida com uma Rede Neural Recorrente (RNN) baseada em camadas LSTM (Long Short-Term Memory), capazes de processar sequências de texto e identificar padrões linguísticos associados ao sentimento expresso em uma avaliação.

O projeto também conta com uma aplicação interativa desenvolvida em Streamlit, que permite ao usuário submeter uma crítica e visualizar a previsão gerada pelo modelo.

Sobre o Projeto

O classificador foi treinado com o conjunto de dados de críticas de filmes do IMDB. Durante o processamento, os textos são convertidos em sequências numéricas, considerando as 5.000 palavras mais frequentes do vocabulário. Para padronizar a entrada da rede neural, cada sequência é limitada a 100 tokens.

A partir do texto processado, o modelo estima a probabilidade de a crítica expressar um sentimento positivo ou negativo.

Arquitetura do Modelo

A rede neural foi implementada utilizando TensorFlow e a API Keras, com as seguintes camadas:

Entrada (Input): recebe sequências numéricas de tamanho fixo, com 100 tokens por crítica.
Embedding: transforma os índices das palavras em vetores densos de 16 dimensões, permitindo que o modelo aprenda representações numéricas do vocabulário.
Primeira camada LSTM: composta por 10 unidades, processa a sequência e retorna os estados intermediários para a próxima camada recorrente.
Segunda camada LSTM: composta por 10 unidades, processa as representações temporais e gera uma representação final da sequência.
Camada de saída (Dense): utiliza uma unidade com função de ativação sigmoide (Sigmoid) para estimar a probabilidade de sentimento positivo.

A saída do modelo é interpretada da seguinte forma:

Valores próximos de 0 indicam maior probabilidade de sentimento negativo.
Valores próximos de 1 indicam maior probabilidade de sentimento positivo.
Desempenho

O modelo apresentou os seguintes resultados de acurácia nas avaliações realizadas:

Métrica	Acurácia
Treinamento	91,16%
Validação	84,56%
Teste	84,62%

Os resultados indicam que o modelo consegue classificar corretamente a maior parte das críticas avaliadas, incluindo textos que não foram utilizados durante o treinamento. A diferença entre a acurácia de treinamento e a de teste também sugere uma possível ocorrência de overfitting, que pode ser investigada em trabalhos futuros.

Estrutura do Projeto

Os principais arquivos do repositório são:

modelo_imdb.keras: contém a arquitetura e os pesos treinados da rede neural.
word_index.json: armazena o mapeamento entre palavras e índices numéricos utilizado no processamento dos textos.
app.py: implementa a aplicação interativa desenvolvida com Streamlit, responsável por receber as críticas e apresentar as previsões do modelo.
Tecnologias Utilizadas
Python: linguagem utilizada no desenvolvimento do projeto.
TensorFlow e Keras: ferramentas utilizadas para construir, treinar e executar a rede neural.
LSTM: arquitetura recorrente utilizada para processar sequências textuais.
Streamlit: framework utilizado para disponibilizar a interface interativa.
JSON: formato utilizado para armazenar o vocabulário e seu mapeamento numérico.
Aplicação

A aplicação permite inserir uma crítica de filme e obter uma classificação de sentimento com base no modelo treinado. A interface foi desenvolvida para facilitar a experimentação e demonstrar, de forma prática, o funcionamento de um classificador de textos baseado em Deep Learning.

Possíveis Melhorias

Como evolução do projeto, podem ser exploradas estratégias como o ajuste dos hiperparâmetros, a aplicação de técnicas de regularização, a ampliação das representações vetoriais e a comparação com outras arquiteturas de processamento de linguagem natural.

Objetivo: demonstrar a aplicação de redes neurais recorrentes à análise de sentimentos, desde o processamento de textos até a disponibilização de um modelo preditivo em uma interface interativa.
