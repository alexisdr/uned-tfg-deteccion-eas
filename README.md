# Detección de eventos adversos en historiales clínicos

## Código fuente

El código se ha distribuido en 5 cuadernos Jupyter con responsabilidades muy concretas:
1. analisis.ipynb: encargado de analizar los datos de entrada usados para el entrenamiento del modelo, como los EAs, su relación con el CIE10, el CIE10 y los informes médicos.
2. data-set.ipynb: realizar los procesos de transformación de datos necesarios para extraer la información más significativa de los informes médicos y generación del dataset.
3. train.ipynb: este cuaderno se encarga de la generación de los tokens y el entrenamiento del modelo a partir del dataset generado en el paso anterior.
4. inferencia.ipynb: a partir del modelo generado se realiza la clasificación de los códigos EAs de un informe e interpreta los resultados.
5. metrica-s-test.ipynb: toma todos los datos de test y los clasifica mediante el modelo para calcular la métrica-S.

## Entorno

Los elementos que componen el entorno de desarrollo y ejecución son los siguientes:
* GitHub: repositorio de código.
* Google Drive: almacenamiento de los datos (privado) accesible por Google Colab aportando las credenciales aportunas.
* Google Colab: edición del código fuente en cuadernos Jupyter y su posterior ejecución.
* Hugging Face: además de aportar librerías, actúa como repositorio desde el que descargar el Modelo y Tokenizer base y permite cargar el modelo entrenado.


## Descripción de los procesos y su relación con el entorno.

* Para realizar el análisis de los datos se han cargado los archivos del Corpus desde Google Drive, en una cuenta privada sin acceso para otros usuarios. 
* De forma similar, para el procesamiento de la información toma los datos del Corpus desde Google Drive, realiza los procesos de transformación y como resultado, guarda el Dataset en Google Drive (también de forma privada).
* Para realizar el entrenamiento del modelo comienza con carga del Dataset a partir de Google Drive, además carga el modelo base y su Tokenizer desde Hugging Face. Con esa información, realiza el proceso de entrenamiento y el modelo resultado lo almacena en Hugging Face, siendo público su uso.
* Para el proceso de inferencia se cargan los datos desde Google Drive y el modelo y su Tokenizer desde Hugging Face, permitiendo con ello clasificar nuevos textos con los códigos EAs.
* Para el cálculo de métrica-S se realizan los mismos pasos que en el proceso de inferencia, pero en este caso se realizan los cálculos contra todos los datos de prueba.
