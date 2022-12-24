# COVID Paper Exploration Workshop

En este taller explorarás el uso de [Azure Text Analytics](https://azure.microsoft.com/services/cognitive-services/text-analytics/?WT.mc_id=academic-49822-dmitryso) y [Text Analytics for Health](https://docs.microsoft.com/azure/cognitive-services/language-service/text-analytics-for-health/overview/?WT.mc_id=academic-49822-dmitryso) para obtener algunas ideas de un gran número de documentos médicos de COVID. 

| **Objetivo del proyecto**              | Aprender a utilizar Análisis de Texto con IA para extraer información visual significativa del texto|
| ----------------------------- | --------------------------------------------------------------------- |
| **¿Qué aprenderás?**       | Cómo utilizar Azure Text Analytics Cognitive Service, Cómo procesar datos tabulares en Python usando Pandas y visualizarlos usando diferentes técnicas de visualización |
| **Lo que necesitarás**          | [Suscripción de Azure](https://azure-for-academics.github.io/getting-azure/),  ejecutar [Jupyter Notebooks](https://soshnikov.com/education/how-to-execute-notebooks-from-github/) |
| **Duración**                  | *1-1.5 horas*                                                                |
| **¿Quieres directamente probar la aplicación o ver la solución?** | [COVIDPaperExploration.ipynb](solution/COVIDPaperExploration.ipynb) |
| **Diapositivas** | [Powerpoint](slides.pptx), [SpeakerDeck](https://speakerdeck.com/shwars/covid-paper-exploration-the-workshop) |
| **Autor** | [Dmitry Soshnikov](http://soshnikov.com) |

> Este taller está basado en la siguiente publicación: [arXiv:2110.15453](https://arxiv.org/abs/2110.15453). También puedes consultar [esta publicación de blog](https://towardsdatascience.com/analyzing-covid-medical-papers-with-azure-machine-learning-and-text-analytics-for-health-c87ab621a3d0) para obtener una descripción general de un proyecto de exploración de papel más grande.

<!---  🎥 Watch Microsoft Student Ambassadors [give this workshop](https://www.youtube.com/watch?v=B_Z4qnYtnoU)! -->

## Video

¡Video próximamente!

## Lo que los estudiantes aprenderán

En este proyecto, procesará automáticamente textos de artículos científicos relacionados con COVID para obtener información visual significativa, como:

  - ¿Qué medicamentos se discuten principalmente y por qué?
  - ¿Cómo las estrategias de tratamiento de COVID han cambiado con el tiempo?
  - ¿Cómo se relacionan los síntomas con diferentes diagnósticos?
  - ¿Qué medicamentos se usan a menudo juntos?

![Imagen del proyecto completado](../../images/result.png)

## Requisitos previos

Para este taller:

1. Necesitarás tener una [Cuenta de Azure](https://azure-for-academics.github.io/getting-azure/). Puede que obtengas una cuenta de tu universidad, de lo contrario puedes obtener una cuenta de [Azure for Students](https://azure.microsoft.com/free/students/?WT.mc_id=academic-49822-dmitryso), del [GitHub Student Developer Pack](https://education.github.com/pack) o crear una [Cuenta Gratuita de Azure](https://azure.microsoft.com/free/?WT.mc_id=academic-49822-dmitryso).
> Aprende más sobre la creación de Cuentas de Azure en [Microsoft Learn](https://docs.microsoft.com/learn/modules/create-an-azure-account/?WT.mc_id=academic-49822-dmitryso)
2. Necesitarás saber como ejecutar [Jupyter Notebooks](https://jupyter.org/). Lee más sobre las diferentes opciones [en esta publicación de blog](https://soshnikov.com/education/how-to-execute-notebooks-from-github/):
    - Instala Python de manera local y utiliza Visual Studio Code con la extensión de Python
    - Utiliza [GitHub Codespaces](https://github.com/features/codespaces)

> Jupyter Notebooks ofrece una excelente manera de combinar el código de Python con texto y visualizaciones, creando **documentos ejecutables**. Puede trabajar con Jupyter Notebook a través del navegador o mediante herramientas como Visual Studio Code. Para poder ejecutar el código, debe tener instalado un entorno de Python, ya sea en su computadora local o en la nube.

## Paso 1: Obtener el conjunto de datos

Vamos a empezar [obteniendo el conjunto de datos](data/README.md) de trabajos de investigación médica de COVID. Necesitarás reemplazar el archivo de ejemplo `data/metadata.csv` por la versión completa del conjunto de datos [desde Kaggle](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge?select=metadata.csv). 

> *Lee más acerca de este proceso [aquí](data/README.md). Es posible que deba registrarse en Kaggle.com, pero eso será útil para su futura carrera.*
## Paso 2: Ejecutar Jupyter y explorar los datos

Después de obtener los datos, necesitas abrir la notebook [COVIDPaperExploration.ipynb](COVIDPaperExploration.ipynb) o la notebook [COVIDPaperExplorationDetailed.ipynb](COVIDPaperExplorationDetailed.ipynb) y comienza a escribir código allí, siguiendo las instrucciones.

**Nota**: Se proporcionan dos versiones de la notebook. Puedes elegir la que más te convenga:

* [COVIDPaperExploration.ipynb](COVIDPaperExploration.ipynb) contiene solo breves descripciones de los pasos. Tienes la libertad de escribir la mayor parte del código por tu cuenta.
* [COVIDPaperExplorationDetailed.ipynb](COVIDPaperExplorationDetailed.ipynb) contiene instrucciones más detalladas y debe completar las partes más importantes del código, pero el flujo general es creado por usted.

También hay una [notebook con la solución](solution/COVIDPaperExploration.ipynb), que puedes consultar en caso de que tengas algún problema que no puedas resolver. Sin embargo, te sugerimos que intentes resolver todos los problemas por tu cuenta, utilizando [Stack Overflow](http://stackoverflow.com/) como referencia para encontrar las soluciones. 

> Se describen diferentes opciones para ejecutar Jupyter Notebooks [en esta publicación de blog](https://soshnikov.com/education/how-to-execute-notebooks-from-github/).

Como resultado de este paso, debe cargar todos los datos del artículo en un *Pandas DataFrame* y filtrar solo los artículos que se publicaron después de enero de 2020. Puede trazar un histograma de frecuencias de publicación:

<img src="../../images/pubfreq.png" width="300"/>

<table border="0"><tr><td><img src="../../images/ds4beginners.png" width="300"/>
</td><td><b>Pandas</b> es una biblioteca de Python muy utilizada para manipular datos tabulares. Puedes <a href="https://github.com/microsoft/Data-Science-For-Beginners/tree/main/2-Working-With-Data/07-python">leer más</a> acerca de utilizar Pandas para el procesamiento de datos en nuestro <a href="https://github.com/microsoft/Data-Science-For-Beginners/">Data Science for Beginners Curriculum</a>.
</td></tr></table>

## Paso 3: Crear y utilizar un endpoint de Text Analytics

Para este punto, deberías tener tu suscripción de Azure lista. Comienza iniciando sesión en el [portal de Azure](http://portal.azure.com/?WT.mc_id=academic-49822-dmitryso).

Después, crea un recurso de [Azure Cognitive Service for Language](https://docs.microsoft.com/azure/cognitive-services/language-service/overview/?WT.mc_id=academic-49822-dmitryso). Puede comenzar a crear el recurso haciendo clic [**AQUÍ**](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesTextAnalytics) - te llevará a la página correspondiente en el portal de Azure.

> Asegúrate de seleccionar el nivel de precios **S - Standar**, porque Health Analytics no está disponible en el nivel gratuito

Una vez que hayas creado el recurso, debes ir al portal y copiar el **Endpoint URL** y la **Clave de acceso** en el notebook:

```python
endpoint = 'https://myservice.cognitiveservices.azure.com/' 
key = '123456789123456789012345678901' 
```

> Los números aquí son ficticios, debes sustituirlos con valores reales de un recurso en tu suscripción para que el código funcione.

Para utiizar el servicio, primero creamos el endpoint:
```python
from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient

text_analytics_client = TextAnalyticsClient(
    endpoint=endpoint, 
    credential=AzureKeyCredential(key))
```
Y después llamamos el servicio,
And then we can call the service, pasando lotes de hasta 10 documentos a la vez:
```python
inp = [document_1,document_2,...]
poller = text_analytics_client.begin_analyze_healthcare_entities(inp)
res = list(poller.result())
```

Después de este paso, debería poder procesar un montón de resúmenes y producir la lista de entidades con los tipos correspondientes, como se muestra a continuación:
```
Dexmedetomidine (MedicationName)
improve (Course)
organ dysfunction (SymptomOrSign)
critically (ConditionQualifier)
ill (Diagnosis)
randomized controlled trial (AdministrativeEvent)
Dexmedetomidine (MedicationName)
Sepsis (Diagnosis)
...
``` 

## Paso 4: Procesar resúmenes

¡Ahora es el momento de ir a lo grande y procesar resúmenes a escala! Sin embargo, debido a que tenemos un tiempo limitado y no queremos desperdiciar tus recursos en la nube, procesaremos solo una cantidad limitada de resúmenes aleatorios (digamos, 200-500).

Ten en cuenta que algunos resúmenes no están presentes (tendrán 'NaN') en el campo **abstract** correspondiente.

> Es importante seleccionar los resúmenes al azar, porque más adelante queremos explorar el cambio en las ténicas de tratamiento a lo largo del tiempo, y necesitamos tener una representación de artículos uniforme en todo el período de tiempo. Alternativamente, para minimizar aún más el tiempo/gasto, puede seleccionar un subintervalo de tiempo (digamos, solo el año 2020) y luego procesar documentos aleatorios en ese intervalo.

Didica un tiempo a pensar en la forma en que almacenará el resultado del procesamiento. Puedes agregar resultados de procesamiento como columnas adicionales al DataFrame, o puedes usar una lista/diccionario por separado.

> Quieres asegurarte de que para cada artículo se mantenga información esencial, como el título y la fecha de publicación, junto con todas las entidades y relaciones.

El procesamiento puede llevar bastante tiempo. Puedes comenzar (y continuar hasta el final del taller) con un tamaño de muestra pequeño (~50 documentos) para asegurarte de que tu código funciona y que tu estructura de datos sea correcta, y luego aumenta el tamaño de muestra a 200-500 hacia el final para obtener Los resultados.

> Si realmente tienes poco tiempo, puedes omitir este paso y cargar los resultados del procesamiento de 500 documentos aleatorios del archivo `data\processed.pkl.bz2` utilizando el siguiente código:

```python
import pickle, bz2

with bz2.BZ2File('data\processed.pkl.bz2','r') as f:
    store = pickle.load(f)
```

## Paso 5: Obtener los síntomas, medicamentos y diagnósticos más repetidos

¡Ahora es el momento de procesar nuestros datos y obtener algunas ideas! Comencemos por agrupar entidades por su ID de ontología (ID de UMLS) y ver cuáles son las principales menciones en diferentes categorías. Como resultado, debe crear una tabla similar a la siguiente:

| UMLS ID | Name | Category | Count |
|---------|------|----------|-------|
| C0020336 | hydroxychloroquine | MedicationName | 99 |
| C0008269 | chloroquine | MedicationName | 43 |
| C0939237 | lopinavir + ritonavir | MedicationName | 28 |
| ... | ... | ... | ...

También puede crear una nube de palabras de diagnósticos, síntomas o medicamentos.:

![word cloud of diagnoses](../../images/wordcloud.png)

## Paso 6: Visualizar el cambio en las estrategias de tratamiento

Además de calcular el conteo total de menciones, puedes ver cómo se distribuyen por mes, y así detectar cambios en las estrategias de tratamiento. Seleccione los principales medicamentos/estrategias y calcule la distribución de sus menciones por meses (o semanas). Primero, obtenga la lista de los 5 ID de UMLS principales para medicamentos y clases de medicamentos (también conocidas como estrategias de tratamiento), y luego use solo esas clases para trazar gráficos similares a los siguientes:

![visualización](../../images/strat_1.png)

![visualización](../../images/strat_2.png)

## Paso 7: Visualizar la co-ocurrencia de términos

Es interesante ver qué términos aparecen juntos en un artículo, porque nos puede dar una idea de las relaciones, por ejemplo, entre diagnósticos y medicamentos, o síntomas y tratamientos. También deberías poder ver qué medicamentos se usan juntos con frecuencia y qué síntomas ocurren juntos.

Puedes usar dos tipos de diagramas para eso:

* **Diagrama de Sankey** nos permite investigar relaciones entre dos tipos de términos, por ejemplo, diagnostico y tratamiento
* **Diagrama de cuerdas** ayuda a visualizar la concurrencia de términos del mismo tipo (por ejemplo, qué medicamentos se mencionan juntos)

Para trazar ambos diagramas, necesitamos calcular la matriz de co-ocurrencia, que en la fila i y la columna j contiene el número de co-ocurrencias de los términos i y j en el mismo resumen (se puede notar que esta matriz es simétrica).

Para trazar los diagramas, podemos usar la biblioteca de gráficos [Plotly](https://plotly.com/python/). Este proceso está descrito [aquí](https://plotly.com/python/sankey-diagram/). Para el diagrama de cuerdas, puedes utilizar [Holoviews](https://holoviews.org/)

![Diagrama de Sankey](../../images/sankey.png) | ![Diagrama de cuerdas](../../images/chord.png)
----|----

## Próximos pasos

Si quieres saber más:

* Ruta de aprendizaje de MS Learn: [Microsoft Azure AI Fundamentals: exploración del procesamiento de lenguaje natural](https://docs.microsoft.com/learn/paths/explore-natural-language-processing/?WT.mc_id=academic-49822-dmitryso )
* Obtén más información sobre el proyecto a gran escala sobre el análisis de conjuntos de datos de COVID mediante CosmosDB/PowerBI/AzureML en [esta publicación de blog](https://soshnikov.com/science/analyzing-medical-papers-with-azure-and-text-analytics-for-health/)
* Si planeas utilizar esta propuesta en tu investigación, cita este artículo: [arXiv:2110.15453](https://arxiv.org/abs/2110.15453)

## Práctica

La extracción de conocimiento que hemos realizado en este taller fue posible gracias al servicio Text Analytics for Health, que hizo la mayor parte del trabajo por nosotros. Para diferentes dominios de conocimiento, necesitará entrenar su propio modelo de red neuronal NER, y para eso también necesitará un conjunto de datos. El servicio [Custom Named Entity Recognition](https://docs.microsoft.com/azure/cognitive-services/language-service/custom-named-entity-recognition/overview/?WT.mc_id=academic-49822-dmitryso) puede ayudarte a hacer eso.

Sin embargo, el [Servicio de Text Analytics](https://azure.microsoft.com/services/cognitive-services/text-analytics/?WT.mc_id=academic-49822-dmitryso) tiene un [mecanismo de extracción de entidades preconstruido](https://docs.microsoft.com/azure/cognitive-services/language-service/named-entity-recognition/concepts/named-entity-categories/?WT.mc_id=academic-49822-dmitryso), así como extracción de palabras clave. Como desafío adicional, experimenta con texto de un dominio de problema diferente y vea si puede extraer algunas ideas significativas de ellos.

Cosas que puedes construir:

* Analiza las publicaciones de un blog o una red social y obtén una idea de los diferentes temas sobre los que escribe el autor. Vea cómo cambian los intereses con el tiempo, así como el estado de ánimo. Puede usar el blog de [Scott Hanselman](https://www.hanselman.com/) que se remonta a [2002](https://www.hanselman.com/blog/archive/2002).
* Analiza el [Feed de Twitter de COVID 19](https://github.com/thepanacealab/covid19_twitter) para ver si puedes extraer cambios en los temas principales de Twitter.
* Analiza tu archivo de correo electrónico para ver cómo los temas que discutes y tu estado de ánimo cambian con el tiempo. La mayoría de los clientes de correo electrónico le permiten exportar sus correos electrónicos a texto sin formato o formato CSV (aquí hay un [ejemplo para Outlook](https://support.microsoft.com/office/import-and-export-outlook-email-contacts-and-calendar-92577192-3881-4502-b79d-c3bbada6c8ef/?WT.mc_id=academic-49822-dmitryso)).

Obtenga más información sobre análisis de texto siguiendo [este módulo](https://docs.microsoft.com/learn/modules/analyze-text-with-text-analytics-service/?WT.mc_id=academic-49822-dmitryso).

## Feedback

Asegúrate de dejarnos tus [comentarios sobre este taller](https://forms.office.com/r/MdhJWMZthR).

[Código de Conducta](../../../../CODE_OF_CONDUCT.md)
