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
├── Dockerfile
├── train.py
├── predict.py
├── requirements.txt
└── train.csv    	# Archivo de entrenamiento

Cómo ejecutar con Docker
1. Construir la imagen


docker build -t mi_imagen_entrenamiento

2. Entrenar el modelo

docker run --rm -v "$(pwd)":/app mi_imagen_entrenamiento python train.py train.csv

Hacer predicciones

docker run --rm -v "$(pwd)":/app mi_imagen_entrenamiento python predict.py train.csv

Esto generará predicciones.csv con una nueva columna rentable_pred.
Requisitos
Docker  version 28.1.1


CSV de entrada con al menos las columnas: budget, popularity


Dependencias gestionadas por requirements.txt:
pandas
scikit-learn
joblib

