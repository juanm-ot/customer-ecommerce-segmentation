El comercio electrónico es  una opción cada vez más popular para los consumidores a la hora de realizar compras. Las empresas de ecommerce tienen la oportunidad de recopilar una gran cantidad de datos valiosos sobre el comportamiento de sus clientes durante el proceso de compra. Estos datos pueden proporcionar información crucial para entender y satisfacer las necesidades de los clientes, mejorar la experiencia de compra y aumentar la lealtad a la marca.

En este contexto, un ecommerce ha recopilado datos de las compras realizadas por sus clientes durante un período de un año, desde diciembre del 2010 hasta diciembre del 2011. Estos datos, disponibles en Kaggle, contienen información sobre las transacciones, como la fecha de compra, el monto gastado y otros detalles relevantes.

El objetivo de este proyecto es utilizar **técnicas de análisis y segmentación** para comprender el comportamiento transaccional de los clientes. Para ello, se aplicará el análisis RFM (Recency, Frequency, Monetary) y el algoritmo de agrupamiento K-means.


## Flujo de datos

El repositorio tiene tres .ipynb: "Pipeline de procesamiento", "EDA" y "Segmentación". Cada uno contiene el código y los archivos relacionados con las etapas del proyecto.

* **Pipeline de procesamiento:**
En esta sección del repositorio, se encuentra el código responsable de evaluar la calidad de los datos y realizar las funciones de limpieza y transformación necesarias. El resultado de este proceso es un archivo CSV limpio y listo para el análisis posterior.

* **EDA (Exploratory Data Analysis):** 
Análisis estadístico descriptivo de las variables. Se agrupan las transacciones por grupos de países, específicamente, Reino Unido y los demás países. Esta decisión se tomó debido a que el 99.8 % de las transacciones ocurrieron en el Reino Unido, lo que generaba un desbalance en los datos. Se analizan patrones transaccionales temporales y de usuario por grupo de países. Para este análisis se utiliza Python y la librería plotly para generar gráficas interactivas. 
[![newplot.png](https://i.postimg.cc/NGDs3gwn/newplot.png)](https://postimg.cc/NLyvTvF8)

Se proporciona el enlace a Google Colab para visualizar las gráficas en línea, y se sugiere descargar el archivo para ejecutarlo localmente con el archivo requirements.txt para instalar las dependencias necesarias<br>
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1osS1xgpETOeTlQ_pA9uIUpPO2HX0rVeu?usp=sharing) 


* **Segmentación:**
En esta sección, se proponen dos técnicas complementarias de segmentación. En primera instancia, se aplica una agrupación RFM para calcular el score de cada cliente en función de su recencia, frecuencia y valor monetario. Luego, se utiliza el algoritmo K-means para realizar la segmentación basada en los scores calculados anteriormente. Para determinar el número óptimo de clústeres (K), se evalúan los resultados utilizando el coeficiente de la silueta y la curva del codo.


## Resultados segmentación

En el contexto del análisis RFM (Recency, Frequency, Monetary), Recencia, Frecuencia y Valor Monetario son tres métricas clave utilizadas para segmentar y entender el comportamiento de los clientes en base a sus transacciones. Ademas, se realiza un "Ranking Customer's" basado en los puntajes asignados para cada parametro de evaluacion segun las reglas del negocio. Para este caso, fueron clasificados asi.

| RFM Score Range | Customer Segment     |
|-----------------|----------------------|
| RFM Score > 4.5 | Top Customer         |
| 4.5 > RFM Score > 4 | High Value Customer |
| 4 > RFM Score > 3 | Medium Value Customer |
| 3 > RFM Score > 1.6 | Low-Value Customer |
| RFM Score < 1.6 | Lost Customer        |


[![descarga.png](https://i.postimg.cc/85yYbXqZ/descarga.png)](https://postimg.cc/7G2XH9Pz)

A partir de esta información se realiza una segmentación con K-means con el proposito de identificar segmentos mas precisos, automatizacion y escalabilidad del modelo para entornos productivos y consideracion de las interacciones complejas que el RFM no puede encontrar. Siguiendo las metricas de evalucion(coeficiente de silueta) y de pronostico de K( elbow curve) se itero sobre segmentos con K= 2, k=3 y k=5. 

Los resultados y analisis se pueden visitar en el archivo ```03_segmentacion_customers.ipynb```



## Estructura repositorio

```linux

.
├── README.md                               # Leeme
├── 01_process_data_pipeline.ipynb          # pre-procesamiento data
├── 02_exploratory_data_analysis.ipynb      # analisis exploratorio
├── 03_segmentation_users.ipynb             # segmentacion clientes
│
├── requirements.txt           # Instalar para correr archivos en local
│
├── online_retail_data.xlsx            # raw data
├── online_retail_data.csv             # raw data .csv
└── process_online_retail_data.csv     # output pipeline preprocesamiento

```
