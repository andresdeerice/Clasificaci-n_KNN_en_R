**Clasificación con KNN**

Una de las tantas aplicaciones de la minería de datos es la minería de textos, la cual consiste en clasificar documentación según su temática (topic modelling). Esta es una forma de machine learning, la cual busca el tema central (temática) de cada documento, en función de la frecuencia de aparición de ciertas palabras. Una vez obtenida la frecuencia de las palabras utilizadas en el documento, lo clasifica según las palabras con mayor frecuencia. Hay varios algoritmos de clasificación, pero en este caso usaré el conocido algoritmo KNN (K-Nearest Neighbors).

Este algoritmo forma parte de los que se conocen como algoritmos de aprendizaje supervisado, ya que se conoce el valor del atributo objetivo (en este caso, el destino del documento). El algoritmo clasificará las nuevas instancias de datos a partir de un juego de datos de entrenamiento. A su vez, KNN conforma un grupo de algoritmos conocidos como lazy learning methods, ya que el aprendizaje ocurre al momento de aplicar el set de datos de prueba, no antes.

El algoritmo KNN es muy sensible a : 1-) la elección del K, es decir, la cantidad de  “vecinos” con los que se compara la nueva instancia para ser clasificada, y 2-) la medida de similitud utilizada (para este ejercicio usaré la definición de distancia euclidiana, que es la predeterminada por R).

Para medir la precisión de un modelo de clasificación, como es el caso, usamos la matriz de confusión, la cual nos muestra los errores que el modelo comete:

  ![image](https://github.com/user-attachments/assets/4c062b08-cce1-4e89-ad01-527691911f19)

Donde,

-	Tipo de Aciertos:
    o	C1-C1: verdadero positivo
    o	C2-C2: verdadero negativo

-	Tipo de Errores:
    o	C2-C1: falso positivo. Era C1, pero se clasifica C2 (error tipo I)
    o	C1-C2: falso negativo. Era C2, pero se clasifica C1 (error tipo II)

Para este ejercicio, lo que haré es clasificar artículos de la agencia de noticias Reuters relacionados a inversiones financieras y fondos de inversión. Las temáticas son:
-	acquire
-	crude
-	earn
-	grain
-	interest
-	money - fx
-	ship
-	trade

El formato del fichero a utilizar es txt. Luego de hacer un análisis rápido del archivo, vemos que tiene dos columnas, la cual la primera es la temática, y la segunda, el título del artículo. Este archivo cuenta con 5.485 artículos.
Para comenzar el ejercicio en sí, lo que haré para las 8 temáticas del archivo txt, es crear el corpus, limpieza y acondicionamiento del texto (eliminar signos de puntuación, eliminar espacios en blanco innecesarios, convertir todo el texto en minúsculas, eliminar palabras sin significado propio, eliminar números, sustituir las palabras derivadas por su palabra raíz). Luego de eso, para todas las temáticas, creo la matriz de términos, y demás, hasta llegar a tener el data frame apto para knn. Este algoritmo, lo aplicaré con dos funciones, ‘knn’ del paquete ‘class’ y ’train’ de ‘caret’.

Con ambos paquetes, tenemos resultados similares, con un accuracy de aproximadamente 95%.
