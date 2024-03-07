# **Minitaller de OpenCV**

Para este minitaller aprenderemos algunas funciones básicas que podemos usar con OpenCV. Como requisitos para este tutorial tenemos:
* Una computadora con Windows 10, 11 o Linux.
* Jupyter Notebook.
* Python 3.

Primero debemos entrar a Jupyter Notebook en el siguiente [link](https://jupyter.org/try-jupyter/lab/) y copiar los archivos que se encuentran en este repositorio a una carpeta dentro del entorno de Jupyter como se muestra en la imagen.

Una vez hecho esto podemos comenzar con el tutorial.

## Combinación de imágenes
1. Abra dentro de jupyter el archivo llamado **mezclador.ipynb**. Dentro del script notará que está segmentado por bloques. 
//Poner una imagen
2. Corra el bloque 0, quitandole el # a los comandos de *pip install* donde se instalarán las bibliotecas necesarias para correr el programa.

```ruby
#Bloque 0
#! pip install matplotlib
#! pip install opencv-contrib-python
```

3. Corra el bloque 1 donde se instalaran las librerias.

```ruby
#Bloque 1
import cv2
import matplotlib.pyplot as plt
```
4. Corra el Bloque 2 donde se estarán cargando las imágenes. Una vez hecho esto podrá observar una imagen.

```ruby
#Bloque 2
# Cargar las dos imágenes
img1 = cv2.imread('image1.jpg')
plt.imshow(img1)
plt.show()
```
5. Corra el bloque 3 donde obtendrá otra imagen.
```ruby
#Bloque 3
img2 = cv2.imread('image2.jpg')
plt.imshow(img2)
plt.show()
```

6. Ejecutando el bloque 4 podrá observar la misma imagen que obtuvo en el punto anterior con una redimensionamiento.

```ruby
#Bloque 4
# Ajustar la escala de la segunda imagen para que tenga la misma forma que la primera
img2 = cv2.resize(img2, (img1.shape[1], img1.shape[0]))
plt.imshow(img2)
plt.show()
```

7. En el bloque 5 usted podrá ajustar el nivel del traslape entre las imágenes, cambiando el valor de la variable `alpha`.

```ruby
#Bloque 5
# Mezclar las imágenes con un peso de 0.5 para cada una
alpha = 0.5
beta = 1 - alpha
```
8. En el bloque 6 podrá observar la función addWeighted la cual pertenceal módulo de Core Funcionality de OpenCV, está función se encarga de mezclar imágenes de igual tamaño.

```ruby
#Bloque 6
output = cv2.addWeighted(img1, alpha, img2, beta, 0)
```
9. Por último el bloque 7 que se encarga de graficar la imagen generada.

```ruby
#Bloque 7
# Mostrar la imagen mezclada
cv2.imshow('Blended Image', output)
plt.imshow(output)
plt.show()
cv2.waitKey(0)
cv2.destroyAllWindows()
```
