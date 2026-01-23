A continuación dejo la estructura del trabajo realizado explicada.
DESCRIPCIÓN DEL PROBLEMA DE NEGOCIO: 
las plataformas digitales en general, reciben todos los dias, grandes volumenes de reseñas (datos) escritos por usuarios, donde estos, expresan diversas opiniones, experiencias al usarlas, niveles de satisfacción entre otros.
Estas, contienen información valiosa para la empresa, pero que al tratarse de datos textuales sin estructura, su análisis como tal resulta altamente costoso y poco escalable y eficiente.
La problemática principal consiste en transformar estos comentarios en información accionable, permitiendo así identificar de manera automática si una reseña refleja una percepción positiva o negativa del servicio brindado. Contar con este tipo de análisis facilita
el monitoreo de la satisfacción del usuario, la rápida detección de problemas recurrentes y la toma de decisiones en post de una mejora del servicio o producto brindado. Entonces, desde la perspectiva del negocio, el poder clasificar y analizar grandes volúmenes de 
opiniones de manera automática aporta valor en áreas como experiencia de usuario, soporte al cliente y análisis de producto, reduciendo tanto costos como tiempo frente a otros enfoque más tradicionales.
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
OBJETIVO GENERAL:
El objetivo de este proyecto es aplicar técnicas de procesamiento de lenguaje natural (NLP) y Machine Learning trabajadas durante la carrera para analizar reseñas de usuarios de Spotify y así, desarrollar un modelo capaz de clasificar automáticamente el sentido de los
comentarios.
De esta manera, se busca implementar conceptos cómo el procesamiento del texto, incluyendo tareas de normalización, eliminación de stopwords y lemantización, buscando así reducir el ruido y preparar los datos para su posterior análisis. Luego, los textos transformados
a representaciones numéricas mediante los enfoques clásicos de Bag of Words (BoW) y TF-IDF, perimitiendo que los modelos de aprendizaje automático puedan operar sobre información textual no estructurada. Sobre esto, se entrena un modelo de Regresión Logística para poder
clasificar los sentimientos, evaluando su desempeño a través de matrices de confusión y técnicas de validación cruzada que permiten analizar la estabilidad y capacidad de generalización. 
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
ORIGEN DE LOS DATOS:
Los datos fueron obtenidos de un dataset público disponible en Kaggle titulado como "Spotify App Reviews 2022". El conjunto de datos contiene reseñas realizadas por usuarios de la app de Spotify. El dataset combina información textual no estructurada con una señal 
explícita de evaluación por parte del usuario, lo que lo hace especialmente adecuado para tareas de análisis de sentimientos (como la que realizamos).
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
DEFINICIÓN DE LAS VARIABLES:
La variable Review corresponde al comentario escrito por el usuario en lenguaje natural y constituye así la principal fuente de información no estructurada del proyecto. Esta columna es utilizada como entrada del modelo luego de aplicar las etapas de preprocesamiento y
vectorización del texto.
La variable Rating representa una valoración numérica otorgada por el usuario en la plataforma, generalmente, en una escala discreta. Usando esta columna se construyó la variable objetivo sentiment, que indica el sentimiento general de la reseña. Para esto, se transformaron
las valoraciones en una clasificación del tipo binaria donde los ratings altos fueron asociados a sentimiento positivo y los ratings bajos a sentimiento negativo, además, se descartaron los casos intermedios buscando así reducir la ambiguedad. Esta es la variable que el 
modelo busca predecir a partir del contenido textual de las reseñas.
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
LIBRERIAS UTILIZADAS:
Para el desarrollo del proyecto se utilizaron bibliotecas generalmente asociadas a la ciencia de Datos en Python, Pandas se utilizó para la carga, manipulación y limpieza de datos, permitiendo así, trabajar de manera eficiente con el dataset original y sus diversas 
transformaciones. Numpy se utilizó para realizar operaciones numéricas y manejo de las diversas estructuras consecuentes al desarrollo del proyecto.
En el procesamiento del lenguaje natural se utilizó spaCy, principalmente para la lematización del texto y el análisis linguístico básico, contribuyendo en la normalización de las reseñas. Para la vectorización del texto y el modelado se empleó scikit-learn, utilizando
herramientas como CountVectorizer y TfidVectorizer para poder transformar el texto en representaciones numéricas y LogisticRegression para entrenar el modelo de clasificación. Esta libreria fue utilizada para la evaluación del modelo mediante diversas métricas, matrices de
confusií y validación cruzada.
Finalmente, Matplotlib y Seaborn se utilizaron para la visualización de resultados, perimitiendo analizar de forma gráfica la distribución de datos, el desempeño del modelo y los errores de clasificación.
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
CONCLUSIONES:
A partir del análisis realizado sobre las reseñas de la aplicación Spotify, se logró construir un pipeline completo de Procesamiento de Lenguaje Natural orientado a la clasificación de sentimiento binaria. Este proyecto permitió abordar de forma integral las distintas
etapas vistas en la Carrera, desde el Análisis exploratorio de datos hasta la vectorización y el modelo supervisado.
En la etapa del EDA se observó que la distribución de la longitud de las reseñas es asimétrica, con una gran concentración de textos cortos y una cola larga de reseñas extensas. Al segmentar por sentimiento, se detectó que las reseñas negativas tienden a presentar 
una mayor variabilidad en longitud, lo que sugiere que los usuarios insatisfechos suelen explayarse más al describir problemas específicos. Esta diferencia aporta información al contexto del problema para el análisis del lenguaje.
El análisis de palabras frecuentes y las nubes de palabras permitieron identificar términos claramente asociados a cada polaridad con las que trabajamos (positivo-negativo). En las reseñas positivas, predominan palabras vinculadas a la experiencia 
de uso y al disfrute del servicio, mientras que en las negativas aparecen con mayor frecuencia términos relacionados con errores, rendimiento, pagos y fallas funcionales. Este comportamiento nos permite validar que el contenido textual contiene señales suficientes para 
inferir el sentimiento expresado por el usuario.
Para la representación numérica del texto se utilizaron dos enfoques clásicos: Bag of Words (BoW) y TF-IDF. En cambos casos se decidió utilizar n-gramas de tamaño (1,2), lo que permitió capturar no solo palabras individuales sino también combinaciones frecuentes de términos
que aportan mayor carga semántica, como expresiones de negación o frases comunes en las reseñas. Esto, mejoró la capacidad de los modelos para interpretar el contexto del texto frente al uso exlcusimo de unigramas.
Durante la etapa de procesamiento, se realizó una eliminación selectiva de stopwords, donde se conservaron términos de negación como "no", "not","don´t" y "do not". Esta decisión fue clave, ya que este tipo de palabras resulta fundamental en tareas de análisis de 
sentimiento y su eliminación indiscriminada puede alterar el significado de una oración completa. El impacto de esta corrección se vió reflejado en las predicciones realizadas sobre los ejemplos nuevos.
Los modelos de Regresión Logística entrenados sobre ambas representaciones mostraron un desempeño muy bueno y sólidos. Con métricas como accuracy, precision, recall y F1-Score equilibrados entre las clases. En el de TF-IDF podemos ver una leve mejora respecto a Bag of Words
(BoW), especialemte en la reducción de falsos positivos, lo cual se evidencia al ver las matrices de confusión.
Por otra parte, la evaluación mediante validación cruzada permitió confirmar la estabilidad de los resultados obtenidos, reduciendo así, el riesgo de overfitting y reforzando la capacidad de generalización del modelo. A su vez, la prueba con nuevas oraciones demostró
que el pipeline completo funciona correctamente en escenarios no vistos durante el entrenamiento.
Por último, podemos decir que los resultados obtenidos nos demuestran que, utilizando técnicas clásicas de NLP como limpieza de texto, vectorización con BoW y TF-IDF, modelos lineales supervisados, es posible construir soluciones efectivas para problemas reales de
análisis de sentimiento. Entonces, este proyecto nos muestra como conceptos trabajados durante el curso pueden asociarse de manera coherente para transformar texto no estrcturado en información con la que se pueden tomar decisiones.
