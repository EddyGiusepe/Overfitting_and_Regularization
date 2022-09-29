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

## Curva de aprendizado de validação

Curva de aprendizado calculada a partir de um conjunto de dados de validação que dá uma ideia de quão bem o modelo está generalizando. É comum criar curvas de aprendizado duplas para um modelo de aprendizado de máquina durante o treinamento nos conjuntos de dados de treinamento e validação.


Em alguns casos, também é comum criar curvas de aprendizado para várias `métricas`, como no caso de problemas de modelagem preditiva de classificação, onde o modelo pode ser otimizado de acordo com a `Perda de Entropia Cruzada` e o desempenho do modelo é avaliado usando a precisão da classificação. Nesse caso, dois gráficos são criados, um para as curvas de aprendizado de cada métrica, e cada gráfico pode mostrar duas curvas de aprendizado, uma para cada um dos conjuntos de dados de treinamento e validação.


## Curvas de Aprendizado de Otimização

Curvas de aprendizado calculadas na métrica pela qual os parâmetros do modelo estão sendo otimizados, <font color="red">por exemplo</font>: Perda.


## Curvas de Aprendizado de Desempenho

Curvas de aprendizado calculadas na métrica pela qual o modelo será avaliado e selecionado, <font color="red">por exemplo</font>: Accuracy.


----------------------------------------------------------------------------
# Diagnosticando o comportamento do modelo

A forma e a dinâmica de uma curva de aprendizado podem ser usadas para diagnosticar o comportamento de um modelo de aprendizado de máquina e, por sua vez, talvez sugerir o tipo de mudança de configuração que pode ser feita para melhorar o aprendizado e/ou o desempenho.

Existem três dinâmicas comuns que você provavelmente observará nas curvas de aprendizado; eles são:

* Underfitting

* Overfitting

* Good fit

Analisaremos cada um deles com exemplos. Os exemplos assumirão que estamos analisando uma métrica de minimização, o que significa que pontuações relativas menores no eixo $y$ indicam mais ou melhor aprendizado.

# Curvas de Aprendizagem Underfitting

`Underfitting` refere-se a um modelo que não pode aprender o conjunto de dados de treinamento.

Um modelo de `underfitting` pode ser identificado apenas a partir da curva de aprendizado da perda de treinamento.

Ele pode mostrar uma **linha plana** ou **valores ruidosos de perda** relativamente alta, indicando que o modelo não conseguiu aprender o conjunto de dados de treinamento.

Um exemplo disso é fornecido abaixo e é comum quando o modelo não possui uma capacidade adequada para a complexidade do conjunto de dados.

![](https://machinelearningmastery.com/wp-content/uploads/2019/02/Example-of-Training-Learning-Curve-Showing-An-Underfit-Model-That-Does-Not-Have-Sufficient-Capacity.png)


Um modelo de `underfitting` também pode ser identificado por uma perda de treinamento que está diminuindo e continua a diminuir no final do gráfico.

Isso indica que o modelo é capaz de mais aprendizado e possíveis melhorias e que o processo de treinamento foi interrompido prematuramente.



![](https://machinelearningmastery.com/wp-content/uploads/2018/12/Example-of-Training-Learning-Curve-Showing-An-Underfit-Model-That-Requires-Further-Training.png)

Então, um gráfico de curvas de aprendizado mostra `underfitting` se:

* A perda de treinamento permanece plana, independentemente do treinamento.

* A perda de treinamento continua a diminuir até o final do treinamento.


# Curvas de Aprendizagem Overfitting

`Overfitting` refere-se a um modelo que aprendeu muito bem o conjunto de dados de treinamento, incluindo o ruído estatístico ou flutuações aleatórias no conjunto de dados de treinamento.

Isso geralmente ocorre se o modelo tiver mais capacidade do que o necessário para o problema e, por sua vez, muita flexibilidade. Também pode ocorrer se o modelo for `treinado por muito tempo`.

Um gráfico de curvas de aprendizado mostra `overfitting` se:

* O gráfico de perda (Loss) de Treinamento continua a diminuir com a experiência.

* O gráfico de perda (Loss) de validação diminui até um ponto e começa a aumentar novamente.


O ponto de inflexão na `Loss de validação` pode ser o ponto em que o treinamento pode ser interrompido, pois a experiência após esse ponto mostra a dinâmica do `overfitting`.

![](https://machinelearningmastery.com/wp-content/uploads/2018/12/Example-of-Train-and-Validation-Learning-Curves-Showing-An-Overfit-Model.png)



# Curvas de Aprendizagem de Bom Ajuste

Um bom ajuste é o objetivo do algoritmo de aprendizado e existe entre um modelo de `Overfitting` e `Underfitting`.

Um bom ajuste é identificado por uma Loss de Treinamento e Validação que diminui até um ponto de estabilidade com um Gap mínimo entre os dois valores finais de perda.

A Loss do modelo quase sempre será menor no conjunto de dados de Treinamento do que no conjunto de dados de Validação. Isso significa que devemos esperar algum gap entre as curvas de aprendizado da Loss de treinamento e validação. Esse Gap é chamada de <font color="yellow">“Gap de generalização”</font>.

Um gráfico de curvas de aprendizado mostra um bom ajuste se:

* <font color="yellow">O gráfico da Loss de treinamento diminui até um ponto de estabilidade.</font>

* O gráfico de perda de validação diminui até um ponto de estabilidade e tem um pequeno Gap com a Loss de treinamento.


<font color="orange">O treinamento contínuo de um bom ajuste provavelmente levará a um overfitting.</font>


![](https://machinelearningmastery.com/wp-content/uploads/2018/12/Example-of-Train-and-Validation-Learning-Curves-Showing-A-Good-Fit.png)



# Como diagnosticar conjuntos de Dados não representativos

As curvas de aprendizado também podem ser usadas para diagnosticar propriedades de um conjunto de Dados e se ele é relativamente representativo.

Um conjunto de Dados não representativo significa um conjunto de dados que pode não capturar as características estatísticas relativas a outro conjunto de dados extraído do mesmo domínio, como entre um conjunto de TREINAMENTO e um conjunto de dados de VALIDAÇÃO. Isso geralmente pode ocorrer se o número de amostras em um conjunto de dados for muito pequeno em relação a outro conjunto de dados.

Existem dois casos comuns que podem ser observados; eles são:

* O conjunto de dados de treinamento é relativamente pouco representativo.

* O conjunto de dados de validação é relativamente pouco representativo.


# Conjunto de dados de TREINAMENTO não representativo

Um conjunto de dados de treinamento não representativo significa que o conjunto de dados de treinamento não fornece informações suficientes para aprender o problema, em relação ao conjunto de dados de validação usado para avaliá-lo.

Isso pode ocorrer se o conjunto de dados de treinamento tiver poucos exemplos em comparação com o conjunto de dados de validação.

<font color="orange">Essa situação pode ser identificada por uma curva de aprendizado para a Loss de treinamento que mostra melhora e similarmente uma curva de aprendizado para a Loss de validação que mostra melhora, mas permanece um grande Gpa entre as duas curvas.</font>


![](https://machinelearningmastery.com/wp-content/uploads/2018/12/Example-of-Train-and-Validation-Learning-Curves-Showing-a-Training-Dataset-the-May-be-too-Small-Relative-to-the-Validation-Dataset.png)



# Conjunto de dados de VALIDAÇÃO não representativo

Um conjunto de dados de validação não representativo significa que o conjunto de dados de validação não fornece informações suficientes para avaliar a capacidade de generalização do modelo.

Isso pode ocorrer se o conjunto de dados de validação tiver poucos exemplos em comparação com o conjunto de dados de treinamento.

<font color="orange">Este caso pode ser identificado por uma curva de aprendizado para a Loss de treinamento que parece um bom ajuste (ou outros ajustes) e uma curva de aprendizado para a Loss de validação que mostra movimentos ruidosos em torno da Loss de treinamento.</font>

![](https://machinelearningmastery.com/wp-content/uploads/2018/12/Example-of-Train-and-Validation-Learning-Curves-Showing-a-Validation-Dataset-the-May-be-too-Small-Relative-to-the-Training-Dataset.png)


Também pode ser identificado por uma Loss de validação menor que a Loss de treinamento. Nesse caso, indica que o conjunto de dados de validação pode ser mais fácil para o modelo prever do que o conjunto de dados de treinamento.


![](https://machinelearningmastery.com/wp-content/uploads/2018/12/Example-of-Train-and-Validation-Learning-Curves-Showing-a-Validation-Dataset-that-is-Easier-to-Predict-than-the-Training-Dataset.png)




Links de estudo:

* [Machine Learning Mastery: Jason Brownlee PhD](https://machinelearningmastery.com/learning-curves-for-diagnosing-machine-learning-model-performance/)

* [Machine Learning Mastery: ROC-AUC e Precision-Recall](https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/)




Thanks God!
