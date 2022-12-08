## Obtener la información

En este taller, estaremos analizando los trabajos de investigación médica de COVID. Primero, necesitamos obtener el conjunto de datos que estaremos utilizando. En este directorio, hay un archivo de ejemplo **metadata.csv** que contiene información únicamente de 5 documentos. Necesitas reemplazarlo con el conjunto de datos completo antes de continuar con este taller.

### Acerca del conjunto de datos

Al comienzo de la pandemia de COVID, se lanzó un desafío de investigación en [Kaggle](http://kaggle.com)para analizar artículos científicos sobre el tema. El conjunto de datos detrás de esta competencia se llama [CORD](https://www.semanticscholar.org/cord19) y contiene corpus constantemente actualizado de todo lo que se publica sobre temas relacionados con el COVID. Alrededor de la mitad de los artículos tienen el texto completo, mientras que la otra mitad contiene los metadatos.

Este conjunto de datos consite en las siguientes partes:

* **Archivo de metadatos** [Metadata.csv](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge?select=metadata.csv) contiene la información más importante para todas las publicaciones en un solo lugar. Cada documento en esta tabla tiene un identificado único en `cord_uid` (que de hecho no es completamente único, una vez que comienza a trabajar con el conjunto de datos). La información incluye:
   - Título de la publicación
   - Journal
   - Autores
   - Resumen
   - Fecha de publicación
   - DOI.
* **Artículos completos** en el directorio `document_parses` que contiene texto extructuradoen formato JSON, lo que simplifica el análisis. 
* **Incrustaciones de documentos preconstruidas** que asignan un `cord_uid` a cada vector flotante, los cuales reflejan algunas semánticas generales del artículo de investigación.

En este taller, trataremos solo con resúmenes de artículos de investigación, por lo que solo necesitamos el archivo **metadata.csv**.

### Obtener los datos

El conjunto de datos está disponible en [Kaggle](http://kaggle.com), el cual es un recurso muy conocido para realizar competencias de aprendizaje automático. Puede descargar el archivo **metadata.csv** directamente desde allí.

1. Si no te haz registrado en Kaggle, [hazlo](https://www.kaggle.com/account/login?phase=startRegisterTab). De lo contrario, inicia sesión.
1. Dirígete a la [página del conjunto de datos CORD](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge?select=metadata.csv) y selecciona el archivo **metadata.csv**.
1. Haz clic en el ícono para descargar el archivo en tu máquina local en el directorio actual.
1. Eemplaza el archivo **metadata.csv**. Tendrás que descomprimir el archivo si es necesario.

> Ten en cuenta que el archivo `metadata.csv` es bastante grande, pesa más de 1 Gb. Esto puede hacer que el procesamiento de archivos sea lento en algunos momentos. ¡No deberías sorprenderte, ya que estamos tratando con grandes cantidades de datos del mundo real!

Una vez hecho esto, puedes continuar con el taller.