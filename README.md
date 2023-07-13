1.	Código de procesamiento de ofertas

### Cargue de librerias y ejecución de funciones de la georreferenciación

En esta parte se cargan las librerías básicas para el procesamiento que se realizará a continuación. Las funciones "get_google_maps_url()" y "geocoder_igac(address)" se definieron en su momento para realizar el proceso de georreferenciación. Para asignar las coordenadas (latitud y longitud) se hace uso de la paquetería de geocoder. 

### Preprocesamiento de la información de direcciones

Previo a ejecutar la función elaborada, se requiere el preprocesamiento sobre las direcciones, de manera que se excluyan caracteres que dificulten el proceso de georreferenciación. De igual manera se excluyen algunas palabras como Bloque, Etapa, Interior, Apartamento, entre otras, con su respectiva numeración, de tal forma que se tenga una georreferenciación efectiva. Para ejecutar esta parte se debe correr el segundo chunck de código del jupyter notebook. Se obtendrá una base de ofertas, con una columna "direccion2" 

### Ejecución de la función geocoder_igac()

En el tercer chunk de código se ejecuta la función elaborada sobre las diferentes direcciones procesadas.

### Almacenamiento de información

En el cuarto chunk de código se guarda la información en un archivo csv para posteriores procesos.


2.	Código revisión de resultado georreferenciación (se anexa las sugerencias para la elaboración del código)

### Cargue de librerias y ejecución de funciones de la georreferenciación

En esta parte se cargan las librerías básicas para el procesamiento que se realizará a continuación. 

Se realiza la lectura de los archivos resultantes en el proceso de georreferenciación. Es decir, se leen los csv resultantes del código titulado "CÓDIGO_PROCESAMIENTO_OFERTAS.ipynb"

Se elabora un procesamiento adicional para evitar tíldes y caracteres extraños para posteriormente realizar el pegue de las coordenadas a partir de las direcciones.

Lectura y cruce de un archivo con códigos Divipola.

Se hace un join espacial buscando poligonos de las capas "R_TERRENO" y "U_TERRENO", que coincidan con las coordenadas generadas en el proceso de georreferenciación. En aquellos casos donde no hay un match exacto de las coordenadas con los poligonos, se busca realizar este join espacial a partir de aproximaciones. Esto se realiza a partir de la función "function_join_shp()".

Una vez se asignan los códigos prediales (de treinta dígitos), se realiza el pegado de esta información a la base de avalúos original. De esta forma, a la información de avalúos se asignan aquellos casos donde se encontró un código predial que se pueda asignar de manera exacta y de manera aproximada.

Se guarda esta base para posteriores análisis.
