# RECONOCEDOR DE TIPOS DE ANIMALES UTILIZANDO LA API DE TENSORFLOW

## MI PRIMER INTREGABLE DE MI DETECTOR DE ANIMALES 
Para este proyecto se utilizara un modelo preentrenado de Tensorflow el cual se llama: faster_rcnn_resnet101_coco

# PASOS PARA EJECUTAR EL PROYECTO

### 1. DEBEMOS DE CLONAR EL REPOSITORIO

### 2. PASO NO.2 DEBEMOS DE COMPLEMENTAR EL MODELO
###### para esto es necesario descargar las carpetas ["modelo y modelo congelado"](https://drive.google.com/drive/folders/1OHRv3jrybEzI392G229zrnB6dS3AiiJd?usp=sharing) abrir la carpeta de  deteccion y pegarla ai

### 3. tener instalado [Anaconda](https://www.anaconda.com/products/individual) 
Anaconda es un programa el cual nos sirve para crear distintos entornos en nuestra computadora para la instalacion de librerias

### 4. [crear un entorno virtual en anaconda](https://riptutorial.com/es/python/example/10797/realizacion-de-entornos-virtuales-utilizando-anaconda-)

### 5. instalar en anaconda las siguientes librerias desde el promt de anaconda
#### 1. [tensorflow](https://www.tensorflow.org/install/pip) version 1.14
se debe instalar la version 1.14 porque sobre esta version de tensorflow corre este proyecto
#### 2. [numpy](https://pypi.org/project/numpy/1.16.4/) version 1.16.4
se debe instalar esta version de numpy porque es la que es compatible con tensorflow 1.14
#### 3. [matplotlib](https://anaconda.org/conda-forge/matplotlib)
#### 4. [pandas](https://anaconda.org/anaconda/pandas)
#### 5. [Pillow](https://anaconda.org/anaconda/pillow)
#### 6. [pycocotools](https://anaconda.org/conda-forge/pycocotools)

### 6. descargar la ultima version de [labelimg]() 
este programa nos sirve para etiquetar las imagenes y da como salida un archivo .xml 

### 7. copiar carpetas
adentro de deteccion_objetos>slim copiar las carpetas "development" y "nets" y pegar estas dos carpetas dentro de las carpetas "library" y "lib" que se encuentran en el direcctorio en donde se esta instalado anaconda navigator 

### 8. descargar imagenes
se deben descargar como minimo 100 imagenes del objeto que se desea reconocer y guardarlas adentro de la carpeta
deteccion_objetos>images 

### 9. etiquetar las imagenes
se deben etiquetar las imagenes con el programa labelimg 

### 10. creacion de archivos .CSV y .Record
###### en el promt de anaconda utilizar los comandos:
###### 1. python xml_a_csv.py --inputs=img_test --output=test
###### 2. python xml_a_csv.py --inputs=img_entrenamiento --output=entrenamiento
###### 3. python csv_a_tf.py --csv_input=CSV/test.csv --output_path=TFRecords/test.record --images=images
###### 4. python csv_a_tf.py --csv_input=CSV/entrenamiento.csv --output_path=TFRecords/entrenamiento.record --images=images

### 11. iniciar el entrenamiento 
###### en el promt utilizar el siguiente comando
###### python object_detection/train.py --logtostderr --train_dir=train --pipeline_config_path=modelo/faster_rcnn_resnet101_coco.config
permitimos que el modelo entrene hasta que llegue a tener una perdida maxima del 0.9 para poder tener un modelo con una buena exactitud
a mayor entrenamiento mayor sera la exactitud del model para detener el entrenamiento usar ctrl+C

### 12. crear el modelo congelado 
###### en el promt utilizar el siguiente comando:
###### python object_detection/export_inference_graph.py --input_type image_tensor --pipeline_config_path modelo/faster_rcnn_resnet101_coco.config  --trained_checkpoint_prefix train/model.ckpt-684 --output_directory modelo_congelado

### 13. probar el modelo 
###### 1. para probar el modelo debemos pegar las imagenes en las que querramos reconocer objetos en la carpeta deteccion_objetos>imp_pruebas
###### 2. en el promt utilizar el siguiente comando: python object_detection/object_detection_runner.py
###### 3. el resultado de la prediccion se encontrara en la carpeta deteccion_objetos>output>imp_pruebas

## ejemplo del funcionamiento 
![fotos-de-guacamayas-9 jpg imgo](https://user-images.githubusercontent.com/36108193/82746063-f31a1380-9d48-11ea-8069-909677724933.jpeg)
![0002-16 (1) jpg imgo](https://user-images.githubusercontent.com/36108193/82746064-f44b4080-9d48-11ea-9d94-141e68fd18d7.jpeg)




