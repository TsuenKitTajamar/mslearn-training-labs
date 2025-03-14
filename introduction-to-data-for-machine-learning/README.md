# Introduction-to-data-for-machine-learning

[Enlace al Laboratorio Completo](https://learn.microsoft.com/en-us/training/modules/introduction-to-data-for-machine-learning/6-evaluate-image-language-data)

## Introducción

El aprendizaje automático obtiene su poder predictivo de los datos que lo moldean. Para construir modelos efectivos, es fundamental entender los datos que se utilizan.

#### Escenario: el último viaje del Titanic

Como un entusiasta arqueólogo marino, tienes un interés particular en los desastres marítimos. Una noche, mientras navegas entre imágenes de huesos de ballena y antiguos pergaminos sobre Atlántida, encuentras un conjunto de datos público que lista los pasajeros y la tripulación conocidos del primer y último viaje del Titanic. Intrigado por la mezcla entre el destino y la casualidad, te preguntas: ¿qué factores determinaron la supervivencia de un pasajero del Titanic? Los datos de esa época son algo incompletos, ya que mucha información de ciertos pasajeros es desconocida. Deberás encontrar maneras de reparar estos datos antes de poder analizarlos completamente.

#### Objetivos de aprendizaje

Visualizar grandes conjuntos de datos mediante el Análisis Exploratorio de Datos (EDA).
Limpiar los errores de un conjunto de datos.
Predecir valores desconocidos utilizando datos numéricos y categóricos.

## Datos buenos, malos y faltantes

Es importante asegurarse de que los datos sean representativos, correctos y completos para que los modelos de machine learning funcionen bien y no generen resultados erróneos. El manejo de datos faltantes o incorrectos es esencial para obtener predicciones fiables.

#### 1. Datos Representativos

Los datos representativos son aquellos que reflejan con precisión la población que estamos analizando. Por ejemplo, si queremos estudiar los factores que influyeron en la supervivencia en el Titanic, necesitamos que nuestra muestra de datos (como la lista de pasajeros) sea lo más completa posible, aunque no sea perfecta. Si solo tomamos una muestra pequeña o sesgada, los resultados pueden no ser fiables.

#### 2. Errores en los Datos

Existen dos tipos de errores en los datos:
Errores de medición: Ocurren durante la recolección de datos y suelen ser difíciles de corregir (por ejemplo, si un sensor da lecturas imprecisas).
Errores de entrada de datos: Son errores al registrar los datos (por ejemplo, escribir un valor incorrecto como 18 metros en lugar de 1.8 metros).
Estos errores pueden afectar el rendimiento de los modelos de predicción, por lo que es importante detectar y corregirlos.

#### 3. Datos Completos

Los datos completos no tienen valores faltantes. Sin embargo, en muchos casos, los datos están incompletos (por ejemplo, falta la altura de Reece en la tabla proporcionada).
Si los datos están incompletos, podemos:
Elegir un modelo que maneje bien los datos faltantes.
Eliminar las filas con datos faltantes, pero esto puede llevar a un sesgo si eliminamos demasiados registros.
Imputar (rellenar) los valores faltantes con estimaciones razonables, aunque esto se debe hacer con cautela.

#### 4. Aplicación Práctica (Titanic):

En el siguiente ejercicio, se trabajará con el conjunto de datos del Titanic para identificar y corregir los datos incompletos, con el fin de que los modelos de predicción sean más precisos.


## Tipos de datos y su clasificación

#### Datos continuos, categóricos y ordinales

- Datos Continuos: Son datos numéricos que pueden aumentar o disminuir en cualquier cantidad. Por ejemplo, se puede agregar 1 mm a 1 metro y obtener 1.001 metros.
- Datos Categóricos: No siguen una secuencia continua. En un ejemplo, los pasajeros del Titanic pueden estar categorizados como "tripulación" o "pasajeros".
- Datos Ordinales: Son datos categóricos con un orden definido. Por ejemplo, "grande", "mediano" y "pequeño" pueden clasificarse numéricamente como 1 > 2 > 3.
- IDs: Son un tipo especial de datos categóricos en los que cada muestra tiene un identificador único, como un número de identificación en un conjunto de datos.

#### Tipos de datos (datatypes):

- Enteros (Integer): Números enteros, como 2.
- Números de punto flotante (Floating-point): Números con decimales, como 2.43.
- Cadenas (Strings): Letras y palabras.
- Booleanos (Booleans): Valores de verdadero o falso.
- Nulo (None/Null/Void): Ausencia de datos.

#### Tipos de datos derivados

Son combinaciones de tipos de datos básicos. 

Los ordenadores pueden almacenar fechas, imágenes, modelos 3D, etcétera. Los denominamos tipos de datos derivados.

Por ejemplo, podemos almacenar un valor de fecha definido como el 1 de enero de 2017 como un número entero o de coma flotante como 20170101. Los números enteros o de coma flotante facilitan los cálculos de nuestros modelos.

#### Elección del tipo de dato

- Para trabajar con datos continuos, se utilizan números de punto flotante.
- Los datos ordinales suelen codificarse con enteros.
- Los datos categóricos con dos categorías pueden ser representados con valores booleanos o enteros. Para tres o más categorías, se necesita un enfoque más complejo.

## One-hot vectors

En este punto, hemos cubierto la codificación de datos continuos (números en punto flotante), de datos ordinales (generalmente enteros) y de datos categóricos binarios (por ejemplo, sobrevivió/no sobrevivió, masculino/femenino, etc.).

Ahora aprenderemos cómo codificar datos y exploraremos recursos de datos categóricos que tienen más de dos clases. También exploraremos los posibles efectos perjudiciales de nuestras decisiones para mejorar el modelo en su rendimiento.

#### Datos categóricos no son numéricos

Los datos categóricos no funcionan con números como los datos continuos u ordinales. Por ejemplo, en datos continuos como los precios de boletos, un valor más alto significa más dinero, pero en datos categóricos no hay un orden lógico entre las categorías. Un ejemplo es el puerto de embarque, que tiene tres valores: Cherburgo (C), Queenstown (Q) y Southampton (S). Si tratamos de reemplazarlos por números, estaríamos creando relaciones falsas, como que un puerto es "mayor" o "menor" que otro.

One-hot encoding es una técnica que ayuda a codificar estos datos categóricos sin generar esas relaciones falsas. En lugar de asignar números, crea una columna para cada categoría y solo pone un 1 en la columna que corresponde a la categoría de cada fila. Por ejemplo, si alguien embarca en Cherburgo, la columna "Port_Cherbourg" tendrá un 1, mientras que las otras columnas tendrán 0.

Sin embargo, el uso de one-hot encoding puede afectar el poder estadístico del modelo, que es la capacidad de identificar relaciones reales entre los datos. Al agregar muchas columnas (como con categorías), el poder estadístico puede disminuir si hay demasiadas categorías o si las columnas no aportan información relevante.

En resumen, aunque **one-hot encoding es útil para codificar datos categóricos**, puede reducir el poder del modelo si no se maneja bien, especialmente cuando se tienen muchas categorías o columnas que no aportan información significativa.