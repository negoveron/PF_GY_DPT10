# <h1 align=center> **Desarrollo de agrupamiento geoespacial con dbscan y pairwise** </h1>

## <h1 align=center>**`Proyecto grupal`**</h1>

En el transcurso del proyecto surguio la iniciativa de poder generar recomendaciones de ubicaciones para nuevos restaurantes, para lo cual se consideró necesario poder establecer agrupamientos de diferentes tipos (categorias, puntuaciones entre portales,etc), y entre estos tipos tambien de agrupamiento por distancia entre ellos.
Para esta clase de tareas existen los algoritmos de clusterizacion y contamos con librerias del estilo pairwise que nos ayudan a poder calcular distancias entre puntos (x,y) , para lo cual debemos contar los datos de latitud y longitud de los restaurantes.

### Importamos las galerias

```python
  # Importacion de galerias
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import folium
from sklearn.cluster import DBSCAN
import numpy as np
from sklearn.metrics import pairwise_distances
```

```python
# Cargar el archivo .pkl como un DataFrame
df = pd.read_pickle('../Datasets/Yelp/business.pkl') # `test01-440321.test001.business`
df #PK business_id 
```
### DBScan
```python
# Creo un array con las coordenadas
coords = df[['latitude', 'longitude']].values

dbscan = DBSCAN(eps=0.09, min_samples=10) #Considero una cantidad de 10 restaurantes distanciados a un radio menor a 0.09 para considerarlo un polo

# Entreno el modelo con las coordenadas
dbscan.fit(coords) #clusters = dbscan.fit_predict(coords)
clusters = dbscan.fit_predict(coords)

# Agrega la columna de clusters al DataFrame
df['cluster'] = clusters
```
### Comprobaciones
```python
print(df['cluster'].unique())
cluster_qty = len(df['cluster'].unique())-1 #el polo (-1) se considera ruido para el algoritmo
print(f"Cantidad de polos gastronomicos: {cluster_qty}")
```
#### __vemos que se generaron 13 cluster (polos gastronomicos), al trabajar con un dataset recortado y al trabajar con hiperparametros seleccionados para la velocidad consideramos que es correcta la generacion de 13 cluster__

### Mapas con Folium

```python
# defino una lista de colores para asignar a cada cluster
marker_colors = [
    'darkgreen',
    'blue',
    'gray',
    'darkred',
    'lightred',
    'green',
    'beige',
    'red',
    'orange', #canada city: edmonton
    'lightgreen',
    'darkblue',
    'lightblue',
    'purple',
    'darkpurple',
    'pink',
    'cadetblue',
    'lightgray',
    'black']
```

```python
#Creacion del mapa
map_center = [32.2437, -89.736] #Centro el mapa en EEUU
mapa = folium.Map(location=map_center, zoom_start=4)

for cluster_id in df['cluster'].unique():
  if cluster_id != -1:  # Ignora los puntos ruido (cluster = -1)
    cluster_df = df[df['cluster'] == cluster_id]
    for _, row in cluster_df.iterrows():
      folium.CircleMarker(
          location=[row['latitude'], row['longitude']],
          radius=15,
          icon=folium.Icon(color=marker_colors[cluster_id]),  # Cambiar el color según el cluster_id
          fill=True,
          fill_color=marker_colors[cluster_id],  # Cambiar el color según el cluster_id
          fill_opacity=.3
      ).add_to(mapa)
mapa
```
<p align="center">
<img src="Imagenes\mapa1_yelp.png"  
height=450>
</p>

#### __En el mapa se puede ver que los restaurantes que estan cercanos a un epsilon de distancia y que estan rodeados de un grupo minimo de 10 estan coloreados del mismo color (fue agrupado por el algoritmo al mismo cluster), dando otra comprobacion de que el algoritmo esta funcionando correctamente para esos hiperparametros (epsilon=0.09 y samples=10)__

<p align="center">
<img src="Imagenes\mapa1_yelp_zoom.png"  
height=450>
</p>

#### al realizar zoom se puede ver cada restaurant que pertenece a cada cluster:

<p align="center">
<img src="Imagenes\mapa1_yelp_zoom.png"  
height=450>
</p>

### Carga de BD de Google (en esta instancia local las BD estan separadas en 2 archivos)

```python
# Crear el DataFrame
dfgoogle = pd.read_parquet("..\Datasets\Yelp\metadata-sitios_restaurantes.parquet") #`test01-440321.test001.restaurante`
dfgoogle # PK gmap_id

dfgoogle.info()
```
```python
#tratamiento del DB para el desarrollo del ML
dfgoogle = dfgoogle.iloc[:3310] #me quedo con las primeras 3310 lineas para optimizar pruebas
dfgoogle = dfgoogle[['gmap_id','name', 'latitude','longitude','avg_rating']] #Solo me quedo con las columnas intervenientes en el ML
dfgoogle = dfgoogle.drop_duplicates(subset=['name'], keep='first') # sacamos lineas duplicadas
dfgoogle
```
#### Para asignar los restaurant de la nueva BD a los cluster ya generados por la anterior desarrollamos una funcion que calcula la distancia de cada nuevo punto con los anteriores y en base a un epsilon y un sample nuevo define si pertenecen a un cluster o no

```python
def predict_dbscan_point(dbscan_model, X_train, new_point, epsilon, min_samples):
        # Calcular distancias del nuevo punto a todos los puntos en X_train
    distances = pairwise_distances([new_point], X_train).flatten()
    
    # Encontrar puntos dentro del radio epsilon
    neighbors_in_radius = np.where(distances <= epsilon)[0]
    
    # Verificar si cumple con la densidad mínima
    if len(neighbors_in_radius) >= min_samples:
        # Etiqueta de los vecinos en el radio epsilon
        neighbor_labels = dbscan_model.labels_[neighbors_in_radius]
                
        # Filtrar etiquetas de ruido (-1) y obtener la etiqueta de cluster más común
        cluster_labels = neighbor_labels[neighbor_labels != -1]
        
        if len(cluster_labels) > 0:
            # Devolver el cluster más común entre los vecinos
            return np.bincount(cluster_labels).argmax()
    
    # Si no cumple los criterios, clasificar como ruido (-1)
    return -1
```
```python
# Creo un array con las coordenadas de los nuevos puntos
nuevos_coords = dfgoogle[['latitude', 'longitude']].values
#Clasifico los nuevos puntos
predictions = [predict_dbscan_point(dbscan, coords, point, 1 , 10) for point in nuevos_coords]
print("Predicción de clusters para nuevos puntos:", predictions)
#el resultado de la funcion lo agrego a la BD
dfgoogle['cluster'] = predictions
```
### Comprobaciones
```python
print(dfgoogle['cluster'].unique())
cluster_qty = len(dfgoogle['cluster'].unique())-1
print(f"Cantidad de polos gastronomicos: {cluster_qty}")
```
### Mapa de los restaurante de Google asignando un color a cada cluster con Folium
```python
#Creacion del mapa
map_center = [32.2437, -89.736] #Centro el mapa en EEUU
mapa = folium.Map(location=map_center, zoom_start=4)

for cluster_id in dfgoogle['cluster'].unique():
  if cluster_id != -1 and cluster_id < 16:  # Ignora los puntos ruido (cluster = -1) y mayores a 16 por colores
    cluster_df = dfgoogle[dfgoogle['cluster'] == cluster_id]
    for _, row in cluster_df.iterrows():
      folium.CircleMarker(
          location=[row['latitude'], row['longitude']],
          radius=15,
          icon=folium.Icon(color=marker_colors[cluster_id]),  # Cambiar el color según el cluster_id
          fill=True,
          fill_color=marker_colors[cluster_id],  # Cambiar el color según el cluster_id
          fill_opacity=.3
      ).add_to(mapa)
mapa
```
<p align="center">
<img src="Imagenes\mapa2_google.png"  
height=450>
</p>
<p align="center">
<img src="Imagenes\mapa2_google_zoom.png"  
height=450>
</p>

### Podemos notar que la funcion generó las asignaciones de clusters en base a los clusters previamente definidos por el algoritmo DBscan



