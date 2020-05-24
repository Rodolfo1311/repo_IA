# reconocimiento de vehiculos con tensorflow
## primer entregable
Para este proyecto se utilizara un modelo preentrenado de Tensorflow el cual se llama: faster_rcnn_resnet101_coco

# como ejecutar este proyecto 

## lo necesairo
### 1. tener instalado [Anaconda](https://www.anaconda.com/products/individual) 
Anaconda es un programa el cual nos sirve para crear distintos entornos en nuestra computadora para la instalacion de librerias

### 2. [crear un entorno virtual en anaconda](https://riptutorial.com/es/python/example/10797/realizacion-de-entornos-virtuales-utilizando-anaconda-)

### 3. instalar en anaconda las siguientes librerias desde el promt de anaconda
#### 1. [tensorflow](https://www.tensorflow.org/install/pip) version 1.14
se debe instalar la version 1.14 porque sobre esta version de tensorflow corre este proyecto
#### 2. [numpy](https://pypi.org/project/numpy/1.16.4/) version 1.16.4
se debe instalar esta version de numpy porque es la que es compatible con tensorflow 1.14
#### 3. [matplotlib](https://anaconda.org/conda-forge/matplotlib)
#### 4. [pandas](https://anaconda.org/anaconda/pandas)
#### 5. [Pillow](https://anaconda.org/anaconda/pillow)
#### 6. [pycocotools](https://anaconda.org/conda-forge/pycocotools)

### 4. descargar la ultima version de [labelimg]() 
este programa nos sirve para etiquetar las imagenes y da como salida un archivo .xml 

### 5. copiar carpetas
adentro de deteccion_objetos>slim copiar las carpetas "development" y "nets" y pegar estas dos carpetas dentro de las carpetas "library" y "lib" que se encuentran en el direcctorio en donde se esta instalado anaconda navigator 

### 5. descargar imagenes
se deben descargar como minimo 100 imagenes del objeto que se desea reconocer y guardarlas adentro de la carpeta
deteccion_objetos>images 

### 6. etiquetar las imagenes
se deben etiquetar las imagenes con el programa labelimg 

### 7. creacion de archivos .CSV y .Record
###### en el promt de anaconda utilizar los comandos:
###### 1. python xml_a_csv.py --inputs=img_test --output=test
###### 2. python xml_a_csv.py --inputs=img_entrenamiento --output=entrenamiento
###### 3. python csv_a_tf.py --csv_input=CSV/test.csv --output_path=TFRecords/test.record --images=images
###### 4. python csv_a_tf.py --csv_input=CSV/entrenamiento.csv --output_path=TFRecords/entrenamiento.record --images=images

### 8. iniciar el entrenamiento 
###### en el promt utilizar el siguiente comando
###### python object_detection/train.py --logtostderr --train_dir=train --pipeline_config_path=modelo/faster_rcnn_resnet101_coco.config
permitimos que el modelo entrene hasta que llegue a tener una perdida maxima del 0.9 para poder tener un modelo con una buena exactitud
a mayor entrenamiento mayor sera la exactitud del model para detener el entrenamiento usar ctrl+C

### 9. crear el modelo congelado 
###### en el promt utilizar el siguiente comando:
###### python object_detection/export_inference_graph.py --input_type image_tensor --pipeline_config_path modelo/faster_rcnn_resnet101_coco.config  --trained_checkpoint_prefix train/model.ckpt-684 --output_directory modelo_congelado

### 10. probar el modelo 
###### 1. para probar el modelo debemos pegar las imagenes en las que querramos reconocer objetos en la carpeta deteccion_objetos>imp_pruebas
###### 2. en el promt utilizar el siguiente comando: python object_detection/object_detection_runner.py
###### 3. el resultado de la prediccion se encontrara en la carpeta deteccion_objetos>output>imp_pruebas

## ejemplo del funcionamiento 
![RAM](https://user-images.githubusercontent.com/64815890/82742358-4c1e8300-9d1a-11ea-9151-e9c665dcf058.jpeg)
![BT](https://user-images.githubusercontent.com/64815890/82742359-4cb71980-9d1a-11ea-88fe-db434d9e42ac.jpeg)
![carro naranja](https://user-images.githubusercontent.com/64815890/82742361-4de84680-9d1a-11ea-8ca2-eb9bdd3b4e3f.jpeg)
![carro rojo](https://user-images.githubusercontent.com/64815890/82742362-4e80dd00-9d1a-11ea-97be-c6718f56f611.jpeg)
![Hilux](https://user-images.githubusercontent.com/64815890/82742363-4fb20a00-9d1a-11ea-95e5-e0bf066678c0.jpeg)
![Ladera](https://user-images.githubusercontent.com/64815890/82742364-50e33700-9d1a-11ea-94d1-c44421fd5ccc.jpeg)
