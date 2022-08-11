# <h2 align="center">Como usar as curvas de aprendizado para diagnosticar o desempenho do modelo de aprendizado de máquina</h2>

---------------------------------------------------------------------------

Data Scientist.: Dr.Eddy Giusepe Chirinos Isidro

---------------------------------------------------------------------------


Uma `curva de aprendizado` é um gráfico do desempenho de aprendizado do modelo ao longo da experiência ou do tempo.

As curvas de aprendizado são uma ferramenta de diagnóstico amplamente utilizada em aprendizado de máquina para algoritmos que aprendem de um conjunto de dados de `treinamento` (Ver <font color="red">Figura</font> a seguir) de forma incremental. O modelo pode ser avaliado no conjunto de dados de `treinamento` e em um conjunto de dados de `validação` de espera após cada atualização durante o treinamento e gráficos do desempenho medido podem ser criados para mostrar as curvas de aprendizado.

![](https://stanford.edu/~shervine/teaching/cs-229/illustrations/train-val-test-pt.png?275227d2a8762bcaf3611555178a73ba)


A revisão das curvas de aprendizado de modelos durante o treinamento pode ser usada para diagnosticar problemas com o aprendizado, como um modelo [Underfitting](https://didatica.tech/underfitting-e-overfitting/) ou [Overfitting](https://www.deeplearningbook.com.br/overfitting-e-regularizacao-parte-1/), bem como se os conjuntos de dados de Treinamento e Validação são adequadamente representativos.


Aqui aprenderemos o seguinte:

* As curvas de aprendizagem são gráficos que mostram as mudanças no desempenho da aprendizagem ao longo do tempo em termos de experiência.


* As curvas de aprendizado do desempenho do modelo nos **conjuntos de dados de Treino e Validação** podem ser usadas para diagnosticar um modelo de `ajuste insuficiente`, `ajuste excessivo` ou `ajuste adequado`.


* As curvas de aprendizado do desempenho do modelo podem ser usadas para diagnosticar se os conjuntos de dados de Treinamento ou Validação não são relativamente representativos do domínio do problema.

## Curva de Aprendizagem

Gráfico de linhas de aprendizagem (eixo $y$) sobre a experiência (eixo $x$).

As curvas de aprendizado são amplamente utilizadas em aprendizado de máquina para algoritmos que aprendem (otimizam seus parâmetros internos) de forma incremental ao longo do tempo, como Redes Neurais de aprendizado profundo.

A métrica usada para avaliar o aprendizado pode ser maximizadora, o que significa que melhores pontuações (números maiores) indicam mais aprendizado. Um <font color="red">exemplo</font> seria a `Accuracy` da classificação.


É mais comum usar uma pontuação que está `minimizando`, como `perda` ou erro, em que pontuações melhores (números menores) indicam mais aprendizado e um valor de $0.0$ indica que o conjunto de dados de Treinamento foi aprendido perfeitamente e nenhum erro foi cometido.

Durante o treinamento de um modelo de aprendizado de máquina, o estado atual do modelo em cada etapa do algoritmo de treinamento pode ser avaliado. Ele pode ser avaliado no conjunto de dados de treinamento para dar uma ideia de quão bem o modelo está <font color="yellow">"aprendendo"</font>. Ele também pode ser avaliado em um conjunto de dados de validação de retenção que não faz parte do conjunto de dados de treinamento. A avaliação no conjunto de dados de validação dá uma ideia de quão bem o modelo está <font color="yellow">"generalizando"</font>.

## Curva de Aprendizagem do Treinamento

Curva de aprendizado calculada a partir do conjunto de dados de treinamento que dá uma ideia de quão bem o modelo está aprendendo.

































