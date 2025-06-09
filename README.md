# Modelos-I
Proyecto para la materia de modelos I




# Modelos_1

Integrantes :<br>
Steven Alipio Berrio - cc: 1036661504 - Ing. Sistemas<br>
Alexander de Jesus Ramirez Marulanda - cc: 98552564 - Ing. Sistemas

<br>
<br>
para nuestra primera entrega se trabajaron dos archivos , el primero se trato de la exploracion de datos y el segundo el tratamiento con dos modelos predictivos 
que serian el random forest y el SVM aplicados a un un conjunto de daros llamado TMDB Box Office Prediction, el cual trata de estimar la recaudacion de dinero de las
peliculas teniendo en cuenta varios factores como actores, genero, lenguaje, popularidad entre otros.
<br>
Pasos Fase-1 <br>
1. ingresar a la carpeta fase-1 donde se encontraran los archivos trabajados <br>
2. cada uno de los archivos esta trabajado en google colab por que para abrirlos solo es necesario seleccionar el archivos y dar click en el boton de abrir en colab
<br>
3. una vez dentro del los archivos de colab simplemente es ejecutar cada una de las celdas ya que los archivos necesarios estan cargados directamente desde google drive <br>

es ejecutar cada una de las celdas ya que los archivos necesarios estan cargados directamente desde google drive <br>


FASE 2. Despliegue en container:

Este proyecto entrena un modelo de aprendizaje automático para predecir si una película será rentable, usando datos como el presupuesto y la popularidad. El modelo se despliega en un contenedor Docker con scripts separados para entrenamiento y predicción.

Cómo funciona este proyecto
train.py: Entrena un modelo RandomForestClassifier usando un CSV de películas, y guarda el modelo en disco (modelo_tmdb.joblib).


predict.py: Carga el modelo y predice la rentabilidad de nuevas películas a partir de un CSV de entrada.
Estructura del Proyecto
.
├── Dockerfile <br>
├── train.py <br>
├── predict.py <br>
├── requirements.txt <br>
└── train.csv    	# Archivo de entrenamiento <br>

Cómo ejecutar con Docker   <br>
1. Construir la imagen  <br>


docker build -t mi_imagen_entrenamiento   <br>

2. Entrenar el modelo  <br>

docker run --rm -v "$(pwd)":/app mi_imagen_entrenamiento python train.py train.csv  <br>

Hacer predicciones  <br>

docker run --rm -v "$(pwd)":/app mi_imagen_entrenamiento python predict.py train.csv

Esto generará predicciones.csv con una nueva columna rentable_pred.<br>
Requisitos <br>
Docker  version 28.1.1  <br>


CSV de entrada con al menos las columnas: budget, popularity  <br>


Dependencias gestionadas por requirements.txt:<br>
pandas  <br>
scikit-learn  <br>
joblib  <br>

FASE 3. API REST:
# API REST para Predicción de Rentabilidad de Películas 🎬  <br>

Este proyecto implementa una aplicación REST en Flask que permite: <br>

- Entrenar un modelo de predicción con datos de películas (`/train`) <br>
- Predecir si una película será rentable (`/predict`)<br>

Se utiliza aprendizaje automático (Random Forest) para predecir la rentabilidad basándose en el presupuesto y la popularidad.<br>
---

## 🚀 Estructura del Proyecto<br>


├── apirest.py # Script principal de la API REST<br>
 ├── train.py # Entrenamiento del modelo<br>
 ├── predict.py # Script standalone para predecir desde CSV
 ├── train.csv # Datos de entrenamiento<br>
 ├── modelo_tmdb.joblib # Modelo entrenado guardado<br>
 ├── requirements.txt # Dependencias del proyecto<br>
 ├── Dockerfile # Construcción del contenedor<br>
 ├── README.md # Documentación (este archivo)<br>
 └── client.py # Script de prueba de la API (opcional)<br>



Para construir la imagen en docker se utilizo <br>
docker build -t modelo_tercera_entrega .<br>

Para ejecución del contenedor<br>
docker run -p 5000:5000 modelo_tercera_entrega<br><br>

La API quedará disponible en:<br>
http://localhost:5000<br>

Endpoints Disponibles<br>
GET /<br>
Mensaje de prueba<br>
{"message": "API REST activa"}<br>

GET /train<br>
Ejecuta el entrenamiento del modelo usando train.csv. El modelo se guarda en modelo_tmdb.joblib.<br>


POST /predict<br>
Devuelve la predicción (0 = no rentable, 1 = rentable).<br>
Ejemplo de cuerpo JSON:<br>
{<br>
  "budget": 500000,<br>
  "popularity": 10.5<br>
}<br>
Respuesta:<br>
{<br>
  "rentable_pred": 1<br>
}<br>

Pruebas<br>
Se puede usar:<br>
client.py<br>



