![image](https://github.com/ingjuanrps/proyIndivi_DataScience_01/assets/114045466/5ad8b500-c8ea-4c33-9abc-b7448cc620eb)

# proyecto_Individual02
## Accidentes Aereos.
* La Organización de Aviación Civil Internacional (OACI), organismo de la Organización de las Naciones Unidas, quiere investigar en profundidad los accidentes producidos desde inicios del siglo XX. Para ello, el objetivo principal es poder obtener un análisis de datos relacionado a esto, junto a un dashboard que complemente los análisis con sus visualizaciones.
## Con el archivo.csv de la Organización de Aviación Civil Internacional (OACI). Se realizo lo siguiente:


#### Preprocesamiento de Datos.
1. *Limpieza de Datos:* Identificar y tratar valores faltantes, duplicados o incorrectos en el conjunto de datos.

2. *Transformación de Datos:* Realizar transformaciones necesarias en los datos, como normalización, escalamiento o codificación de variables categóricas.

3. *Selección de Características:* En algunos casos, seleccionar un subconjunto relevante de las características disponibles para reducir la dimensionalidad o mejorar la calidad del análisis.

4. *Manejo de Valores Atípicos:* Identificar y decidir cómo manejar valores atípicos que pueden afectar el análisis.

5. *Tratamiento de Datos Desbalanceados:* Si los datos están desequilibrados en términos de clases o categorías, se pueden aplicar técnicas para abordar este desequilibrio.
### ETL.
#### Imporatcion de Librerias.
#### Lectura de Archivo csv. para:
* Creacion del DataFrame travez de la lectura del Archivo csv.
* Observando el DataFrame.
* Ver su dimención.
* Ver la información de cada columna.
* Descripción Estadística.
* Cuantificación de la presencia del caracter "?".
#### Normalización de Columnas.
* Información de las columnas.
* Renombrar y normalizar nombres de las columnas.
* Analizamos los distintos tipos de datos por columna.
* Eliminación de Columnas inecesarias.
* Vemos como queda Dimensionado.
#### Modificando Columnas.
##### 01-Columna Date. (Fecha del accidente).
* Observamos los datos Unicos de la columna date.
* Función para la conversion de fecha.
* Reemplazando valores en la columna fecha.
* Cambiamos la columna date al tipo fecha.
* Observamos los valores en la columna date.
* Obtenemos los valores únicos de la columna time.
##### 02-Columna Time. (Hora local, en 24 h. en el formato hh:mm).
* Observamos los valores unicos de la columna time.
* Agregamos ':' entre los números en la columna time.
* Observamos el cambio con la agregacion de los :.
* Usamos la función para convertir los valores de la columna "time" a tipo datetime.time.
* Obtenemos los valores únicos de la columna time.
* Colocamos algunos faltantes en valores Nulos.
* Procederemos a eliminar esa cantidad de Nulos, en la columna time.
##### 03-Columna Location. (Ubicación del accidente).
* Obteniendo los valores únicos de la columna location.
* Obteniendo cuantos valores únicos tenemos.
* Reemplazando valores en la columna location.
* Análisis de las palabras que más se repiten, para reducir la cantidad de lugares.
* Modificaremos la columna 'location' para extraer el país en función a las coincidencias con la siguiente lista.
* Función para la colocación de valores, en una nueva columna llamada country.
* Observamos como quedo la nueva columna.
* Observamos los valores unicos de la columna country.
* Total de valores únicos.
* Observando que muchos de los valores corresponden a estados de los EU. reemplazamos en la columnas country el valor other por United States en una nueva columna llamada location que contiene los estados de los EU.
* Observamos como quedo la columna location.
* Separamos vuelos en una nueva columna llamada surface, considerando si la aeronave colisionó en agua o suelo.
* Observamos la columna surface.
* Observamos los valores únicos de la columna surface.
* Filtramos los registros para water, para tener un número razonable para el análisis.
* Obtendremos un top 10 de los países con más accidentes, para verificar que nuestra columna country contiene varios de los valores observados en la nube de palabras.
* Filtramos las filas donde el campo country es igual a other.
* Filtramos registros donde la superficie sea ground y other en país.
  * Vemos si estos filtros representan una gran cantidad dentro del dataset, para crear una nuva columna para nuestro futuro análisis.
  * Observamos que por lo general corresponen a valores mal escritos, y no usaremos estos filtros por el momento,ya que tenemos la columna country con los paises más representativos.
##### 04-Columna Airline_Operador. (Línea aérea u operador de la aeronave).
* Analizamos operadores de aerolíneas.
* Contando cuantos valores únicos .
* Reemplazando valores en la columna airline_operator.
* Obtenemos los valores únicos de la columna airline_operator.
* Creamos una nube de palabras para observar las palabras que más se repiten.
  * Basada en operador o aeronave.
* Verificamos si alguna de las palabras clave está presente en la columna airline_operator.
* Observamos y Instanciamos  la columna category, para obtener el valor.
##### 05-Columna Flight_no. (Número de vuelo asignado por el operador de la aeronave).
* Obteniendo valor únicos de la columna flight_no.
* Reemplazando valores en la columna airline_operator.
* Obtenemos los valores únicos de la columna flight_no.
* Observando su hay valores Nulos en la columna flight_no.
##### 06-Columna Route. (Ruta completa o parcial realizada antes del accidente.)
* Vemos los valores únicos de la columna route.
* Reemplazando valores en la route.
* Obtenemos los valores únicos de la columna flight_no, para despues ir recoriendo los valores únicos optenidos.
  * Observamos más de 1 valor dentro de las rutas y por ende consideramos que no es posible hacer transformaciones sobre los valores en este paso
  * No podemos saber en qué tramo ocurrió el accidente y nos quedaremos solamente con el país y la superficie donde ocurrió el mismo.
* Obtniendo el total de valores únicos.
##### 07-Columna Aircraft_Type. (Tipo de aeronave).
* Obteniendo los valores únicos de la columna aircraft_type.
* Reemplazando valores en la aircraft_type.
* Obtniendo el total de valores únicos.
* Categorizando las aeronaves por marca (50 históricas).
* Creamos Función para asignar valores a una nueva columna llamada brand (marca).
* Observando como va quedando nuestro DataFrame.
##### 08-Columna Total_aboard. (Total Abordo).
* Observando si hay valores Nulos y cuantos hay si es que existen.
  * Observamos que nos muestra que tenemos 0 valores Nulos.
* Mostrando los valores únicos de la columna total_aboard.
* Contando los valores únicos.
* Remplazando valores en la columna total_aboard.
* Convertimos la columna total_abord a tipo numérico.
* Obteniendo los valores únicos despues deremplazar los valores.
* Obteniendo el total de los valores únicos déspues de reemplazar valores, en la columna total_aboard.
  * Nos muestra un registro menos que al principio.
* Filtramos el DataFrame para registros con total_aboard con valores vacios.
* Filtramos el DataFrame para registros con total_aboard con calores igual a 0.
* Eliminamos registros de la columna total_aboard con valores vacios al ser pocos estos registros.
* Observamos si nos queda algún Nulo, y contamos cuantos tenemos en total en caso de tener valores Nulos.
* Observando los valores unicos de la columna total_aboard.
* Obtenemos el total de los valores únicos.
##### 09-Columna Passengers_Aboard. (Pasajeros Abordo).
* Reemplazando valores de la columna passengers_aboard.
* Convertimos la columna passengers_aboard a tipo numérico.
* Observando la cantidad total de valores Nulos.
##### 10-Columna Crew_Aboard. (Tripulacion Abordo).
* Reemplazando valors en la columna crew_aboard.
* Convertimos la columna crew_abord a tipo numérico.
* Observando la cantidad total de valores Nulos.
* Filtramos el DataFrame para las filas con los valores Nulos.
##### 11-Columna Total_Fatalities. (Muertes totales).
* Reemplazando valores en la columna total_fatalities.
* Convertimos la columna total_fatalities a tipo numérico.
* Obteniendo el total de valores Nulos, enla columna total_fatalities.
  * Nos da como resultado un total de 0 valores Nulos.
##### 12-Columna Passengers_Fatalities. (Muerte de Pasajeros).
* Reemplazando valores en la columna passengers_fatalities.
* Convertimos la columna 'passengers_fataliteis' a tipo numérico.
* Obteniendo el valor de los valores Nulos en la columna passengers_fatalities.
##### 13-Columna Crew_Fatalities. (Muertes de tripulacion.)
* Reemplazar valores en la columna crew_fatalities.
* Convertimos la columna crew_fatalities a tipo numérico.
* Obtener el total de valores Nulos.
* Al ser la misma cantidad filtramos el DataFrame para las filas donde las columnas passengers_fatalities y crew_fatalities son nulos.
  * Probablemente no podamos análizar dichos registros para esas características porque tenemos datos faltantes.
##### 14-Columna Total_Aboard. (Total Abordo)
* Calculamos la cantidad de sobrevivientes para cada vuelo y creamos la columna survivors.
* Observamos nuestro DataFrame, para ver como va quedando, con nuestra limpieaza de datos.
* Volvemos a mirar la información del dataframe.


### EDA.

#### Aspectos minimos a realizar.
*  Búsqueda de valores faltantes.
*  Valores atípicos.
*  Extremos u outliers.
*  Registros duplicados.
*  La utilización de gráficos coherentes según la tipología de variable que corresponda.

#### Importación de librerías.
#### Importacion de mi variable que contiene mi dataframe con el ETL.
* Imporatnado la variable donde se genero un DtaFrame para la depuración de los datos.
* Instanciando la variable importada.
* Observando mi DataFrame.
* Observando las columnas en una tabla.
#### Tratamiento de valores duplicados.
* Buscamos filas con valores duplicados.
  * Observamos que no hay duplicados.
#### Tratamiento de valores nulos.
* Obteniendo la cantidad de valores Nulos en cada columna.
* Porcentajes de los valores Nulos son muy pocos, y mantendremos los valores nulos de dichas columnas para no eliminar registros. 
  * No obstante no usaremos dichas columnas.
* Observamos la dimencion del DataFrame.
* Observamos la dimencion del DataFrame.
#### Medidas descriptivas.
* Obteniendo la cantidad de valores Nulos en cada columna.
* Mostrando como se va visualizando mi DataFrame.
* Obteniendo la descrición estadistica del DataFrame.
#### Histogramas.
* Reaizamos un Histograma con las siguientes columnas: total_aboard,passengers_aboard,crew_aboard,total_fatalities,passengers_fatalities,crew_fatalities,survivors.
  * Todas las distribuciones presentan un gran sesgo a la derecha.
#### Outliers.
* Graficamos las siguientes variables que podemos utilizar (ya que no tienen valores nulos).
* Filtramos outliers de crew_aboard.
* Criterio de selección.
* Filtramos outliers de crew_fatalities.
* Criterio de selección crew_fatalities.
* Criterio de selección, si crew_aboard > crew.fatalities.
#### Gráficos de barras.
### Metricas.
#### ¿Cuántos accidentes estamos analizando?
* la cantidad de accidentes analizada en el dataframe es de: 4770.
* Observando la dimencion del dataframe.
  * Tenemos 4770 filas y 23 columnas, para trabajar.
#### ¿Cuál es el país con mayor cantidad de accidentes?
* Filtramos los datos para excluir la categoría other de country.
* Observamos los valores en una tabla.
  * Estados Unidos es el país con mayor cantidad de accidentes históricos.
#### ¿Cuál es la aerolínea con mayor cantidad de accidentes?
* Calculamos el recuento de accidentes por aerolinea (tomamos las 10 más representativos).
* Observamos los valores en una tabla.
  * En el gráfico podemos observar que Aeroflot tiene la mayor cantidad de accidentes aéreos.
#### ¿Cuál es la aeronave con mayor cantidad de accidentes?
* Calculamos el recuento de accidentes por tipo de aeronave (tomamos las 10 más representativas).
  * Observamos que el Douglas DC-3 es la aeronave con mayor cantidad de accidentes.
* Observamos los valores en una tabla.
#### ¿Cuál es la marca de aeronave con mayor cantidad de accidentes?
* Calculamos el recuento de accidentes por marca (tomamos las 10 más representativas).
  * McDonnell Douglas es la marca con mas accidentes.
#### ¿Qué categoría posee mayor cantidad de accidentes?
* Calculamos el recuento de accidentes por categoría.
  * Observamos que los vuelos no militares poseen mayor cantidad de accidentes a lo largo de la historia.
#### Análisis temporal.
* Accidentes a lo largo de los años.
#### Primer y último vuelo del dataset.
* Vuelo más antiguo:
  * Número de vuelo: 
  * Operador de la aerolínea: Military - U.S. Army
  * Fecha: 1908-09-17T00:00:00.000000000
* Vuelo más reciente:
  * Número de vuelo: 251
  * Operador de la aerolínea: Kamchatka Aviation Enterprise
  * Fecha: 2021-07-06T00:00:00.000000000
#### ¿Resultan más seguros los vuelos en los últimos años?
* Podemos observar que a partir de 1908 la tendencia comenzó fuertemente alcista hasta llegar a 1946 donde tuvimos el máximo histórico
* La tendencia marcó una consolidación entre 1946 y el año 2000, con máximos entre 70 y 80
* Para finalmente comenzar una tendencia a la baja a partir de 1990
* Para los últimos años del dataset, la cantidad de accidentes se encuentra en mínimos históricos
* La media móvil de 10 años resulta un factor importante a considerar, puesto que todas las veces que hemos estado por encima de la misma, los accidentes han sido altos en cantidad
* En los últimos años los vuelos resultaron más seguros que durante mediados del siglo XX.
#### ¿Cuál ha sido el mes histórico con mayor cantidad de accidentes?
* Realizamos grafico de barras.
* Mostramos resultado en una tabla.
* El mes con mayor cantidad de accidentes :
  * Diciembre con 473 accidentes.
* Descripción estadistica de mes.
  * La media de accidentes por mes está en 415

### KPI's
#### KPI.
Evaluar la disminución de un 10% la tasa de fatalidad de la tripulación en los últimos 10 años, comparado a la década anterior.
* Definimos la tasa de fatalidad de la tripulación como el número total de tripulantes fallecidos en los accidentes registrados en la década a considerar, dividido en la cantidad total de accidentes aéreos ocurridos en este período de tiempo.
* Su fórmula es (Suma total de fallecidos en el período de tiempo / Suma total de accidentes en el período de tiempo).
#### KPI.
#### Tasa de Sobrevivencia por decada.

### Conexion a MySQL.
### DashBoard.

