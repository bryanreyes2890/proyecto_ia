# RECONOCEDOR DE TIPOS DE ANIMALES UTILIZANDO LA API DE TENSORFLOW

## MI PRIMER INTREGABLE DE MI DETECTOR DE ANIMALES 
Para este proyecto se utilizara un modelo preentrenado de Tensorflow el cual se llama: faster_rcnn_resnet101_coco

# PASOS PARA EJECUTAR EL PROYECTO

### 1. DEBEMOS DE CLONAR EL REPOSITORIO

### 2. PASO NO.2 DEBEMOS DE COMPLEMENTAR EL MODELO
###### para esto es necesario descargar las carpetas ["modelo y modelo congelado"](https://drive.google.com/drive/folders/1OHRv3jrybEzI392G229zrnB6dS3AiiJd?usp=sharing) abrir la carpeta de  deteccion y pegarla ai

### 3. tener instalado [Anaconda](https://www.anaconda.com/products/individual) 
este programa es indispensable para crear diferentes entornos  y poder montar nuestras librerias

### 4. [crear un entorno virtual en anaconda](https://riptutorial.com/es/python/example/10797/realizacion-de-entornos-virtuales-utilizando-anaconda-)

### 5. DEBEMOS DE INSTALAR LAS SIGUIENTES LIBRERIAS 
#### 1. [tensorflow](https://www.tensorflow.org/install/pip) version 1.14
se debe instalar la version 1.14 porque sobre esta version de tensorflow corre este proyecto
#### 2. [numpy](https://pypi.org/project/numpy/1.16.4/) version 1.16.4
se debe instalar esta version de numpy porque es la que es compatible con tensorflow 1.14
#### 3. [matplotlib](https://anaconda.org/conda-forge/matplotlib)
#### 4. [pandas](https://anaconda.org/anaconda/pandas)
#### 5. [Pillow](https://anaconda.org/anaconda/pillow)
#### 6. [pycocotools](https://anaconda.org/conda-forge/pycocotools)

### 6. descargar la ultima version de [labelimg]() 
con este programita convertimos nuestras imagenes jpg a archivos xml ya que esos archivos son los que reconoce el modelo

### 7. DEBEMOS DE COPIAR NUESTRAS CAPERTAS
adentro de deteccion_objetos>slim copiar las carpetas "development" y "nets" y pegar estas dos carpetas dentro de las carpetas "library" y "lib" que se encuentran en el direcctorio en donde se esta instalado anaconda navigator 

### 8. HAY QUE DESCARGAR NUESTRAS IMAGENES PARA LA DETECCION 
debemos de contar con al menos 100 imagenes para la deteccion de objetos entre mas imagen mejor porque mas preciso va ser nuestro detector

### 9. AHORA CON EL PROGRAMA LABEL IMAGEN DEBEMOS SELECCIONAR SOLO DONDE APARECE LA GUACAMAYA 
con los comandos w y control+s seleccionamos y guardamos nuestras etiquetas

### 10. creamos nuestros  de archivos .CSV y .Record
###### LOS COMANDO QUE DEBEMOS UTILIZAR SON:
###### 1. python xml_a_csv.py --inputs=img_test --output=test
###### 2. python xml_a_csv.py --inputs=img_entrenamiento --output=entrenamiento
###### 3. python csv_a_tf.py --csv_input=CSV/test.csv --output_path=TFRecords/test.record --images=images
###### 4. python csv_a_tf.py --csv_input=CSV/entrenamiento.csv --output_path=TFRecords/entrenamiento.record --images=images

### 11. DEBEMOS DE COMENZAR CON NUESTRO ENTRENAMIENTO
###### Debemos de utilizar el siguiente comando en el promt
###### python object_detection/train.py --logtostderr --train_dir=train --pipeline_config_path=modelo/faster_rcnn_resnet101_coco.config
esperamos hasta que nuestro modelo entrene lo suficiente aunque en promedio en una maquina core i5 de 10 generacion que tengo me tardo un aproximado de 8 horas para complementar 2315 pasos eso significaria que tenemos que contar con mas de  80 horas sin parar para entrenar al 100 % el modelo pero lo que isimos es parar el modelo a un nivel de exactitud considerable

### 12. AHORA CREAMOS NUESTRO MODELO CONGELADO
###### en el promt utilizar el siguiente comando:
###### python object_detection/export_inference_graph.py --input_type image_tensor --pipeline_config_path modelo/faster_rcnn_resnet101_coco.config  --trained_checkpoint_prefix train/model.ckpt-684 --output_directory modelo_congelado

### 13. PROBAMOS A VER QUE TAL NOS QUEDO NUESTRO MODELO CONGELADO
###### 1. para probar el modelo debemos pegar las imagenes en las que querramos reconocer objetos en la carpeta deteccion_objetos>imp_pruebas
###### 2. en el promt utilizar el siguiente comando: python object_detection/object_detection_runner.py
###### 3. el resultado de la prediccion se encontrara en la carpeta deteccion_objetos>output>imp_pruebas

## BUENO ING SANTOS ASI ME QUEDO MI DETECCION DE GUACAMAYAS AZUL ES INSPIRADO EN LA PELICULA DE RIO 
![fotos-de-guacamayas-9 jpg imgo](https://user-images.githubusercontent.com/36108193/82746063-f31a1380-9d48-11ea-8069-909677724933.jpeg)
![0002-16 (1) jpg imgo](https://user-images.githubusercontent.com/36108193/82746064-f44b4080-9d48-11ea-9d94-141e68fd18d7.jpeg)


## Segundo entregable 
### 1. obtencion de imagenes
para el segundo entregable lo que se realizo fue conseguir imagenes de todos los animales solicitados los cuales fueron:
#### 1.Ardilla
#### 2.Guacamaya
#### 3.Pitbull
#### 4.Jirafa
#### 5.Gato

### 2. configuracion de label_map.pbtxt
en este archivo se encuentra en deteccion_objetos>configuracion la siguiente estructura:
###### .item {
######  id: 1
######  name: 'Gato'
###### }

este objeto consta de 2 campos los cuales son id y name en los cuales se debe escribir el id y nombre de cada una de las etiequetas
 para declarar una nueva solamente se debe copiar esta estructura y llenarla con el id siguiente y el nombre de la etiqueta 
### 3. configuracion de labels.txt
este archivo se encuentra en deteccion_objetos>configuracion y es un archivo de texto en el cual se debe indicar todas las etiquetas 
que se utilizaran en este caso son 5
###### 0.null
###### 1.Gato
###### 2.Pitbull
###### 3.Jirafa
###### 4.Guacamaya
###### 5.Ardilla

la primera linea siempre debe ser null
### 4. configurar numero de clases en el archivo faster_rcnn_resnet101_coco.config
este archivo se encuentra en deteccion_objetos>modelo lo unico que se debe configurar en este archivo es el numero de clases que hace 
referencia a la cantidad de etiquetas que se utilizaran que en este caso seran 5
###### num_classes: 5

### 5. eliminacion de los archivos .CSV y .Record de la primera entrega 
estos archivos se encuentran en deteccion_objetos>CSV y deteccion_objetos>TFRecords es necesario dejar estas dos carpetas vacias para
crear los nuevos archivos .CSV y .Record 

### 6. creacion de archivos .CSV y .Record
###### en el promt de anaconda utilizar los comandos:
###### 1. python xml_a_csv.py --inputs=img_test --output=test
###### 2. python xml_a_csv.py --inputs=img_entrenamiento --output=entrenamiento
###### 3. python csv_a_tf.py --csv_input=CSV/test.csv --output_path=TFRecords/test.record --images=images
###### 4. python csv_a_tf.py --csv_input=CSV/entrenamiento.csv --output_path=TFRecords/entrenamiento.record --images=images

### 7. reentrenamiento del modelo 
###### en el promt utilizar el siguiente comando
###### python object_detection/train.py --logtostderr --train_dir=train --pipeline_config_path=modelo/faster_rcnn_resnet101_coco.config
permitimos que el modelo entrene hasta que llegue a tener una perdida maxima del 0.9 para poder tener un modelo con una buena exactitud
a mayor entrenamiento mayor sera la exactitud del model para detener el entrenamiento usar ctrl+C para este segundo entregable se entreno
el modelo durante 7,190 pasos como podemos ver acontinaucion

![WhatsApp Image 2020-05-30 at 6 33 45 AM (1)](https://user-images.githubusercontent.com/36108193/84105920-f9f68680-a9d6-11ea-9f54-7b128d0a3fa3.jpeg)


### 8. congelado del nuevo modelo 
###### en el promt utilizar el siguiente comando:
###### python object_detection/export_inference_graph.py --input_type image_tensor --pipeline_config_path modelo/faster_rcnn_resnet101_coco.config  --trained_checkpoint_prefix train/model.ckpt-684 --output_directory modelo_congelado

![WhatsApp Image 2020-05-30 at 6 37 40 AM](https://user-images.githubusercontent.com/36108193/84105922-fc58e080-a9d6-11ea-840f-8f4818194b4d.jpeg)

### 9. probar el modelo 
###### 1. para probar el modelo debemos pegar las imagenes en las que querramos reconocer objetos en la carpeta deteccion_objetos>imp_pruebas
###### 2. en el promt utilizar el siguiente comando: python object_detection/object_detection_runner.py
###### 3. el resultado de la prediccion se encontrara en la carpeta deteccion_objetos>output>imp_pruebas
#### reconociendo 

## RESULTADOS DEL SEGUNDO ENTREGABLE 

![deforestacion-guacamaya-azul (15)](https://user-images.githubusercontent.com/36108193/84106174-ad5f7b00-a9d7-11ea-8de3-37829b91cfda.jpeg)
![descarga (1)eee](https://user-images.githubusercontent.com/36108193/84106177-b05a6b80-a9d7-11ea-9019-c0d5ee2fdfdf.jpeg)
![Pitbull66](https://user-images.githubusercontent.com/36108193/84106179-b18b9880-a9d7-11ea-839d-dde04357bd80.jpeg)
![5-curiosidades-de-la-jirafa-1-655x368 (1)](https://user-images.githubusercontent.com/36108193/84106183-b2bcc580-a9d7-11ea-801f-e8e36895f8c0.jpeg)
![5-curiosidades-de-la-jirafa-1-655x368 (3)](https://user-images.githubusercontent.com/36108193/84106186-b3edf280-a9d7-11ea-9a51-e5449b7b5fa2.jpeg)
![59802d52c75f06da41524bfa8ea90d26 (1)](https://user-images.githubusercontent.com/36108193/84106189-b5b7b600-a9d7-11ea-99cc-53a1eafc62b4.jpeg)
![235147-original-Jirafa (12)](https://user-images.githubusercontent.com/36108193/84106193-b6e8e300-a9d7-11ea-8f34-5b9594c380b0.jpeg)
![Ardilla46](https://user-images.githubusercontent.com/36108193/84106196-b81a1000-a9d7-11ea-9a0a-45efbdd0cc1a.jpeg)
![Ardilla76](https://user-images.githubusercontent.com/36108193/84106200-b94b3d00-a9d7-11ea-9c51-c004947bc2f2.jpeg)
![deforestacion-guacamaya-azul (1)](https://user-images.githubusercontent.com/36108193/84106203-ba7c6a00-a9d7-11ea-8fd4-dc427dcd78fb.jpeg)
![deforestacion-guacamaya-azul (10)](https://user-images.githubusercontent.com/36108193/84106208-bbad9700-a9d7-11ea-844f-461fb044f979.jpeg)
![deforestacion-guacamaya-azul (13)](https://user-images.githubusercontent.com/36108193/84106211-bcdec400-a9d7-11ea-911b-4b91eb03b7bd.jpeg)
![deforestacion-guacamaya-azul (14)](https://user-images.githubusercontent.com/36108193/84106213-bd775a80-a9d7-11ea-978f-d629ae64f17d.jpeg)
