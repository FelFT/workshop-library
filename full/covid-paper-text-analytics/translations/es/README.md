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

## Reto 4: Procesar resúmenes

Now it's time to go big and process abstracts at scale! However, because we are limited in time, and we do not want to waste your cloud resources, we will process only a limited number of random abstracts (say, 200-500). 

Keep in mind that some abstracts are not present (they will have 'NaN' ) in the corresponding **abstract** field.

> It is important to select abstracts randomly, because later on we will want to explore the change is treatment tactics over time, and we need to have uniform paper representation across all time period. Alternatively, to further minimize time/spend, you can select a time sub-interval (say, only year 2020), and then process random papers in that interval. 

Spend some time thinking about the way you will store the result of processing. You can add processing results as additional columns to the DataFrame, or you can use separate list/dictionary.

> You want to make sure that for each paper you keep essential info such as title and publication time, together with all entities and relations.

Processing can take quite a long time. You may start (and proceed until the end of the workshop) with small sample size (~50 papers) to make sure your code works and your data structure is right, and then increase the sample size to 200-500 towards the end to obtain the results. 

> If you are really short on time, you can skip this step and load the results of processing random 500 papers from `data\processed.pkl.bz2` file using the following code:

```python
import pickle, bz2

with bz2.BZ2File('data\processed.pkl.bz2','r') as f:
    store = pickle.load(f)
```

## Milestone 5: Get Top Symptoms, Medications and Diagnoses

Now it is time to process our raw data and get some insights! Let's start by grouping entities together by their ontology ID (UMLS ID) and seeing which are the top mentions in different categories. As a result, you should build a table similar to the following:

| UMLS ID | Name | Category | Count |
|---------|------|----------|-------|
| C0020336 | hydroxychloroquine | MedicationName | 99 |
| C0008269 | chloroquine | MedicationName | 43 |
| C0939237 | lopinavir + ritonavir | MedicationName | 28 |
| ... | ... | ... | ...

You can also build a word cloud of diagnoses, symptoms or medications:

![word cloud of diagnoses](images/wordcloud.png)

## Milestone 6: Visualize Change in Treatment Strategies

In addition to calculating the total count of mentions, you can see how they are distributed by month, and thus detect changes in treatment strategies. Select top medications/strategies and compute the distribution of their mentions by months (or weeks). First, get the list of top-5 UMLS IDs for medications and medication classes (AKA treatment strategies), and then use only those classes to plot graphs similar to the following:

![visualization](images/strat_1.png)

![visualization](images/strat_2.png)

## Milestone 7: Visualize Co-occurrence of Terms

It is interesting to see which terms occur together within one paper, because it can give us an idea about relationships between, for example, diagnoses and medications, or symptoms and treatments. You should also be able to see which medications are often used together, and which symptoms occur together.

You can use two types of diagrams for that:

* **Sankey diagram** allows us to investigate relations between two types of terms, eg. diagnosis and treatment
* **Chord diagram** helps to visualize co-occurrence of terms of the same type (eg. which medications are mentioned together)

To plot both diagrams, we need to compute the co-occurrence matrix, which in the row i and column j contains the number of co-occurrences of terms i and j in the same abstract (one can notice that this matrix is symmetric).

To actually plot the diagrams, we can use the [Plotly](https://plotly.com/python/) graphics library. This process is well described [here](https://plotly.com/python/sankey-diagram/). For the Chord diagram, you can use [Holoviews](https://holoviews.org/)

![sankey diagram](images/sankey.png) | ![sankey diagram](images/chord.png)
----|----

## Next steps

If you want to learn more:

* MS Learn Learning Path: [Microsoft Azure AI Fundamentals: Explore natural language processing](https://docs.microsoft.com/learn/paths/explore-natural-language-processing/?WT.mc_id=academic-49822-dmitryso)
* Read more about full-scale project on analyzing COVID dataset using CosmosDB/PowerBI/AzureML in [this blog post](https://soshnikov.com/science/analyzing-medical-papers-with-azure-and-text-analytics-for-health/)
* If you are planning to use this approach in your research, cite this paper [arXiv:2110.15453](https://arxiv.org/abs/2110.15453)

## Practice

The knowledge extraction that we have performed in this workshop was possible thanks for Text Analytics for Health service, which did most of the job for us. For different knowledge domains, you would need to train your own NER neural network model, and for that you will also need a dataset. The [Custom Named Entity Recognition](https://docs.microsoft.com/azure/cognitive-services/language-service/custom-named-entity-recognition/overview/?WT.mc_id=academic-49822-dmitryso) service can help you do that. 

However, the [Text Analytics Service](https://azure.microsoft.com/services/cognitive-services/text-analytics/?WT.mc_id=academic-49822-dmitryso) has some pre-built [entity extraction mechanism](https://docs.microsoft.com/azure/cognitive-services/language-service/named-entity-recognition/concepts/named-entity-categories/?WT.mc_id=academic-49822-dmitryso), as well as keyword extraction. As an additional challenge, experiment with text from a different problem domain, and see if you can extract some meaningful insights from them.

Things you can build:

* Analyze a blog or social network posts and get the idea of different topics that author is writing about. See how interests change over time, as well as the mood. You can use the blog of [Scott Hanselman](https://www.hanselman.com/) that goes back to [2002](https://www.hanselman.com/blog/archive/2002).
* Analyze [COVID 19 twitter feed](https://github.com/thepanacealab/covid19_twitter) to see if you can extract changes in major topics on twitter. 
* Analyze your e-mail archive to see how the topics you discuss and your mood change over time. Most e-mail clients allow you to export your e-mails to plain text or CSV format (here is an [example for Outloook](https://support.microsoft.com/office/import-and-export-outlook-email-contacts-and-calendar-92577192-3881-4502-b79d-c3bbada6c8ef/?WT.mc_id=academic-49822-dmitryso)).

Learn more about text analytics by following [this module](https://docs.microsoft.com/learn/modules/analyze-text-with-text-analytics-service/?WT.mc_id=academic-49822-dmitryso).

## Feedback

Be sure to give [feedback about this workshop](https://forms.office.com/r/MdhJWMZthR)!

[Code of Conduct](../../CODE_OF_CONDUCT.md)
