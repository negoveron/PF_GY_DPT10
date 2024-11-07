# <h1 align=center> **Proyecto Grupal - HENRY DATA ANALYST** </h1>

## <h1 align=center>**`Yelp - Google`**</h1>

<p align="center">
<img src="Imagenes/GastroSphere_portada.jpg"  
height=450>
</p>


<details>
  <summary>Primer Sprint</summary>

## 1.- Objetivos:  
● Análisis de Sentimientos:   
Aplicar técnicas de NLP (Natural Language Processing) para
clasificar reseñas de Yelp y Google Maps como positivas, negativas o neutras. Además
nos enfocaremos en aspectos específicos como:
● Comentarios relacionados con el servicio (amabilidad del personal, tiempo de
espera, atención al cliente).
● Condiciones del ambiente (limpieza, ruido, confort).
● Factores específicos de la cocina (calidad de la comida, temperatura, presentación).
● Predicción de Tendencias del Mercado: Implementar modelos de machine learning para
predecir tendencias en el mercado de restaurantes, basados en datos históricos y actuales,
con el objetivo de identificar tipos de restaurantes con mayor probabilidad de crecimiento
o declive.
● Recomendación de Ubicaciones para Nuevos Restaurantes: Realizar un análisis
geo-espacial a fin de identificar regiones con alta concentración de restaurantes (conocidas
como polos gastronómicos). Este análisis debe segmentar la información según la
cantidad de estrellas y el tipo de restaurante, proporcionando una visión clara y
estratégica para abrir nuevos restaurantes.
● Sistema de Recomendación de Restaurantes: desarrollar un sistema de recomendación
de restaurantes que provea a los usuarios sugerencias personalizadas basadas en sus
preferencias individuales y experiencias previas. Este sistema utilizará técnicas avanzadas
de machine learning y análisis de datos para ofrecer recomendaciones que no solo se
adapten a los gustos y hábitos de los usuarios, sino que también tengan en cuenta
factores contextuales, como la hora del día, la ubicación actual y las tendencias recientes
en las reseñas.
## 2.- Alcance del Proyecto
Análisis del Mercado y Recomendación de Restaurantes
1. Objetivos y Metas del Proyecto:  
● Análisis exhaustivo del mercado: Realizar un análisis detallado del mercado
estadounidense, enfocado en restaurantes, utilizando datos de Yelp y Google Maps.
● Modelo de Machine Learning: Implementar un modelo para el análisis de
sentimientos y predicción de tendencias del mercado de restaurantes.
● Sistema de Recomendación: Desarrollar un sistema de recomendación de
restaurantes personalizado a los usuarios finales.
2. Entregables:  
● DataWarehouse en Google Cloud:
- Configuración de Google Cloud para el almacenamiento y gestión de datos
de Yelp y Google Maps.
- Implementación de procesos ETL (Extracción, Transformación y Carga) para
la integración de datos.
- Realización de un Análisis Exploratorio de Datos (EDA) completo para
descubrir patrones y tendencias.
● .Análisis de Sentimientos:
Informes detallados que clasifiquen las reseñas como positivas, negativas o
neutras.
● Modelos Predictivos:
Predicciones sobre el crecimiento o declive de restaurantes basadas en
datos históricos y actuales.
● Sistema de Recomendación:
Prototipo funcional que ofrezca sugerencias personalizadas de restaurantes.
● Análisis Espacial:
Recomendaciones de ubicaciones óptimas para nuevos restaurantes,
basadas en un análisis espacial y demográfico.
● Dashboard Interactivo:
Visualización de los resultados del análisis de sentimientos, predicciones de
tendencias, recomendaciones de ubicaciones.
3. Tareas y Actividades:
● Recolección y Limpieza de Datos:
Obtención y limpieza de datos desde Google Maps y Yelp.
● Diseño y Desarrollo del DataWarehouse:
Diseño e implementación del DataWarehouse en Google Cloud.
● Implementación de Procesos ETL:
Desarrollo de pipelines para la extracción, transformación y carga de datos.
● Análisis Exploratorio de Datos (EDA):
Realización de EDA para analizar y comprender los datos.
● Desarrollo y Validación de Modelos de Machine Learning:
Entrenamiento y evaluación de modelos para análisis de sentimientos y
predicción de tendencias.
● Creación de Dashboards Interactivos en Power BI:
Desarrollo de dashboards para la visualización de datos y resultados.
● Implementación de la Metodología Scrum:
Gestión del proyecto utilizando la metodología Scrum con sprints y
reuniones diarias.
● Desarrollo de Pipelines de Datos:
Diseño y desarrollo de pipelines para la automatización de procesos de
datos.
● Documentación:
Elaboración de documentación técnica.
4. Exclusiones del Proyecto:
● No se realizará una implementación física de nuevos restaurantes.
● No se incluirán datos fuera del mercado estadounidense.
● No se cubrirán otros rubros de negocio distintos a los restaurantes.
Restricciones:
● Tiempo: El proyecto debe completarse en un plazo de 6 semanas.
● Presupuesto: Limitado a la infraestructura de Google Cloud y herramientas de desarrollo
(ClickUp, Python).
● Recursos: Equipo limitado con roles definidos (Scrum Master, Product Owner, Equipo de
Desarrollo).
## 3.- KPIs
● Aumentar en 5% la razón de reseñas positivas de un trimestre con respecto al anterior
para un restaurante particular. La razón de reseñas positivas se calcula como: reseñas
positivas (por trimestre) / total de reseñas (por trimestre).
● Aumentar trimestralmente en 1 (uno) la cantidad de categorías de reviews donde la
relación de las positivas sobre sea mayor a 1. Las categorías de reviews salen de la
clasificación del análisis de sentimientos y pueden ser positivas, negativas o neutrales.
● Bajar trimestralmente en 10% la calificación negativa (2 o menos estrellas).
## 4.- EDA
La realización de un ETL y EDA preliminar permiten tener un primer acercamiento a la
consistencia de los datos, identificar qué datos están disponibles y aumentar el entendimiento de
los mismos.
Para la Demo # 1 se realizaron ETL y EDA preliminares los que arrojaron las primeras
impresiones:
● Las reviews son en su mayoría positivas
● La mayoría de las calificaciones son de 3 o más estrellas, 2 estrellas es lo menos
frecuente.
● La categoría useful es la más frecuente a la hora de clasificar una review.
● Más del 50% de los usuarios hizo 6 o menos reviews.
● Los rubros más frecuentes son restaurant y food.
● La mayoría de los negocios cuenta con menos de 20 reviews, con la media en 10 reviews.
● Los restaurantes con calificaciones más bajas (alrededor de 1 y 2 ) tienden a tener muy
pocas reseñas.
## 5.- Metodología
Metodología de Trabajo: Scrum dentro del Marco Ágil
Enfoque Ágil
El proyecto se gestionará utilizando el marco Ágil (Agile), que permite un desarrollo flexible,
adaptable y basado en la retroalimentación continua. Este enfoque prioriza la entrega
incremental de valor al cliente y responde eficazmente a los cambios y necesidades del entorno.
Dentro de este marco, implementaremos Scrum, una metodología ágil ampliamente utilizada para
gestionar proyectos de software y desarrollo de productos. Scrum nos permitirá dividir el trabajo
en ciclos cortos, llamados sprints, facilitando la evaluación continua y la mejora del producto a
través de reuniones periódicas y retroalimentación constante.
Etapas de la Metodología Scrum
1. Product Backlog
Se recopilarán todas las historias de usuario, requisitos y tareas necesarias para el
desarrollo del proyecto. Estas historias representan las funcionalidades clave y se
priorizarán según su impacto en los objetivos del sistema de alertas y predicción.
2. Sprint Planning
Al inicio de cada sprint (2 semanas), se llevará a cabo una reunión de planificación del
sprint donde el equipo seleccionará las historias de usuario más relevantes del backlog.
Estas se dividirán en tareas más pequeñas y manejables, asegurando que el equipo tenga
una carga de trabajo realista y alcanzable.
3. Sprints
Durante cada sprint, el equipo trabajará en las tareas seleccionadas, siguiendo los
principios de desarrollo iterativo e incremental. El progreso se monitoreará mediante
ClickUp, permitiendo transparencia en el avance y las prioridades.
Para cada tarea decidimos entre el grupo desarrollador que haya un encargado que haga
la revisión técnica, divida tareas y también escriba código.
4. Daily Scrum (Reuniones Diarias)
Se realizarán reuniones cortas diarias (~60 minutos) para que cada miembro del equipo
reporte lo siguiente:
○ Qué se hizo el día anterior.
○ Qué se va a hacer hoy.
○ Si hay algún obstáculo o problema.
Van a ser 3 veces por semana (Lunes, Miércoles y Viernes) con el Scrum Master y Martes y
Jueves solo el grupo desarrollador e implementando mas si es necesario durante los fines
de semana
Esto fomenta la comunicación, identifica problemas rápidamente y asegura que todos
estén alineados con los objetivos del sprint.
5. Sprint Review (Demo)
Al final de cada sprint, se presentará el producto o incremento desarrollado a los
interesados clave. El objetivo es recibir retroalimentación directa para adaptar el desarrollo
a las expectativas del cliente y hacer ajustes para futuros sprints.
6. Sprint Retrospectiva
Después de la revisión del sprint, el equipo participará en una retrospectiva donde se
reflexionará sobre:
○ Qué se hizo bien.
○ Qué se puede mejorar.
○ Acciones para optimizar el proceso en el siguiente sprint.
Esto asegura una mejora continua no solo en el producto, sino también en la metodología
y colaboración del equipo.
Roles Clave en Scrum
1. Product Owner : Pia Ruiz Jaimes
Es el responsable de definir las prioridades del backlog, asegurando que el equipo trabaje
en las tareas más importantes para el cliente. Además, se encarga de asegurar que el
producto cumpla con los objetivos estratégicos.
2. Scrum Master : Alfredo Trujillo
El Scrum Master facilita el proceso de Scrum, eliminando impedimentos y ayudando al
equipo a seguir las prácticas de Scrum correctamente. También protege al equipo de
interrupciones externas y facilita la colaboración.
3. Development Team : Guillermo Veron, Joaquin Costamagna, Jose Cruz, Maria Jose
Atencio, Fernando Garcias Corts
Un equipo auto organizado de desarrolladores, analistas de datos y otros roles técnicos
que se encargan de llevar a cabo las tareas seleccionadas del sprint backlog. El equipo es
responsable de entregar incrementos de valor al final de cada sprint.
## 6.- Stack Tecnológico
Backend:
● Lenguaje Principal: Python
● Framework: FastAPI (TBD)
● Base de Datos: PostgreSQL (TBD)
● Algoritmos y Librerías de Recomendación:
○ TextBlob: Para el análisis de sentimiento de las reviews
○ Scikit-learn: Para el cálculo de la similitud de coseno.(TBD)
○ HDBSCAN: Para la clusterización de restaurantes.
○ Pandas: Para la manipulación de los datos.
○ Numpy: Para las operaciones numéricas.
● API REST: Endpoints creados con FastAPI para la comunicación entre el frontend y el
backend. (TBD)
Frontend:
● Lenguaje Principal: Python
● Framework: React (TBD)
● Estilización: CSS/Bootstrap/Tailwind (TBD)
Infraestructura y Deploy:
● Proveedor de Hosting: Render (TBD)
● Contenedores: Google Cloud
● Control de Versiones: Git y GitHub (https://github.com/negoveron/PF_GY_DPT10)
Análisis de Datos y Visualización:
● Power BI: Utilizado para generar reportes interactivos y visualizaciones de los datos del
sistema de recomendación.
○ Visualizaciones: Se presentan gráficos que muestran las métricas de precisión ,
como la cantidad de usuarios que coincidieron en gustos, la precisión de las
recomendaciones, y las restaurants más recomendados.
○ Conexión a Datos: Power BI se conectará a la base de datos Google Cloud para
extraer los datos necesarios y realizar el análisis visual.
Herramientas Adicionales:
● Editor de Código: Visual Studio Code
● Herramientas de Colaboración:
○ Clickup (https://app.clickup.com/9011445165/v/li/901105723447) / Slack / Google Meet

<p align="center">
<img src="Imagenes/stack.png"  
height=450>
</p>


</details>


<details>
  <summary>Segundo Sprint</summary>

### ETL Completo
### Estructura de Datos Implementada (DW)
### Pipeline ETL Automatizado

<p align="center">
<img src="Imagenes/ciclo_de_vida.png"  
height=450>
</p>

### Diseño ER
### Pipeline para alimentar el DW
### Data Warehouse

<p align="center">
<img src="Imagenes/ciclo_de_vida.png"  
height=450>
</p>

### Automatizacion
### Validacion de datos
### Documentacion
### Analisis de datos de muestra
### MVP/Proof of concept de producto ML
### Este Readme 
</details>  



## Autores! 👋

|   <h3 align=center>Foto</h3> | [![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/) |
|--------|-------------|
| <img src="Imagenes/jc2_perfil.png" width="75"/> | Linkedin Miembro. |
| <img src="Imagenes/jc_perfil.png" width="75"/> | Linkedin Miembro. |
| <img src="Imagenes/mj_perfil.png" width="75"/> | Linkedin Miembro. |
| <img src="Imagenes/fmgc_perfil.png" width="75"/> | Linkedin Miembro. |
| <img src="Imagenes/gv_perfil.png" width="75"/> | Linkedin Miembro. |

