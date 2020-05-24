# RECONOCEDOR DE TIPOS DE ANIMALES UTILIZANDO LA API DE TENSORFLOW
##PRIMER INTERACION DEL PROYECTO 
#PASOS NECESARIOS PARA EJECUTAR 
###1. DESCARGAR E INSTALAR EL PROGRAMA DE ANACONDA
###2. DESPUES CREAMOS NUESTRO ENTORNO VIRTUAL EN EL SOFTWARE DE ANACONDA
###3. DESCARGAR LAS SIGUIENTES LIBRERIAS PARA COMPLEMENTAR ANACONDA 
Esto se realiza desde el promt de anaconda
A.pycocotools
B.pandas
c.pillow
D. matplotlib
E.tensorflow version 1.14
F.numpy version 1.16.4
###4sabe que mano ya me aburri de esperar tengo una mejor idea vea esto listo yat iene la estructura solo cambie lo que dice y borre una que otra cosita por allidespues lo subo esta bien va mano y cuando era el ultimo dia pa subir esto pues no era mañana  viejo esque yo tambien ya estoy cansado viejo mano yo se pero el ultimo dia es hoy a las 12 o lo manda o santos no le va a valer sus puntos y desoyes donde lo tengo que subir al blackboard simon  entonces ai estamos dele valla a descanzar yo lo termino y lo envio gracias por su ayuda ai pasa felis noche viejo que usted ya esta mas desvelado que yo incluso va solo voy a hacer una ultima cosa 
# reconocimiento de vehiculos con tensorflow
## primer entregable
Para este proyecto se utilizara un modelo preentrenado de Tensorflow el cual se llama: faster_rcnn_resnet101_coco

# como ejecutar este proyecto 

## lo necesairo

### 1. clonar este repositorio

### 2. completar el modelo 
###### para esto es necesario descargar las carpetas ["modelo y modelo congelado"](https://drive.google.com/drive/folders/1OHRv3jrybEzI392G229zrnB6dS3AiiJd?usp=sharing) y pegarlas  adentro del directorio deteccion de objetos

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
