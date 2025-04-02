# Convolutional neural networks

Los modelos de deep learning, especialmente las Redes Neuronales Convolucionales (CNN), son clave para trabajar con datos de imágenes en visión por computadora. Las CNN extraen características de las imágenes, reduciendo el gran conjunto de valores de píxeles a un conjunto más pequeño, que luego es procesado por una red neuronal completamente conectada para generar predicciones. Este enfoque ha impulsado avances significativos en el campo.

### Layers in a CNN
CNNs consist of multiple layers, each performing a specific task in extracting features or predicting labels.

## Convolution layers
A convolutional layer works by applying a filter to images. The filter is defined by a kernel that consists of a matrix of weight values.

Una imagen también es simplemente una matriz de valores de píxeles. Para aplicar el filtro, se superpone "overlay" sobre la imagen y se calcula una suma ponderada (weighted sum) de los valores de los píxeles correspondientes de la imagen bajo el núcleo del filtro.

## Pooling layers
Después de extraer los valores de características de las imágenes, se utilizan capas de pooling (o submuestreo) para reducir el número de valores de características, manteniendo las características clave que se han extraído. 

Este proceso ayuda a disminuir la dimensionalidad de los datos y a reducir la complejidad computacional, mientras se preservan las características más importantes que permiten diferenciar las imágenes.

## Dropping layers
Uno de los desafíos más difíciles en una CNN es evitar el sobreajuste (overfitting), donde el modelo obtiene buenos resultados con los datos de entrenamiento pero no generaliza bien con nuevos datos sobre los que no fue entrenado. 

Una técnica para mitigar el sobreajuste es incluir capas en las que el proceso de entrenamiento elimine (o "descarté") aleatoriamente mapas de características. Aunque esto pueda parecer contraproducente, es una forma efectiva de evitar que el modelo dependa en exceso de las imágenes de entrenamiento.

Otras técnicas para mitigar el sobreajuste incluyen voltear, reflejar o distorsionar aleatoriamente las imágenes de entrenamiento, generando datos que varían entre las épocas de entrenamiento.

## Flattening layers
Después de usar las capas convolucionales y de pooling para extraer las características más relevantes de las imágenes, los mapas de características resultantes son arreglos multidimensionales de valores de píxeles. 

Una capa de flattening (aplanamiento) se utiliza para convertir estos mapas de características en un vector de valores, que luego puede ser utilizado como entrada para una capa completamente conectada (fully connected layer).

## Fully connected layers
Una CNN generalmente termina con una red completamente conectada, donde los valores de características se pasan a una capa de entrada, a través de capas ocultas, y generan predicciones en una capa de salida.

En una arquitectura básica de CNN:

1. Se alimentan imágenes a una capa convolucional con dos filtros, generando dos mapas de características.

2. Los mapas de características pasan a una capa de pooling, donde un filtro 2x2 reduce su tamaño.

3. En la capa de dropping, se eliminan aleatoriamente algunos mapas para evitar el sobreajuste.

4. La capa de flattening aplana los mapas restantes en un vector.

5. El vector se pasa a una red completamente conectada que genera predicciones, como la clasificación en tres clases de imágenes: triángulo, cuadrado y círculo.

### Training a CNN model
Al igual que cualquier red neuronal profunda, una CNN se entrena pasando lotes de datos de entrenamiento a través de ella durante varias épocas, ajustando los pesos y los valores de sesgo según la pérdida calculada en cada época.

En una CNN, la retropropagación de los pesos ajustados incluye tanto los pesos del núcleo del filtro en las capas convolucionales como los pesos en las capas completamente conectadas.