# **Minitaller de OpenCV**

Para este minitaller aprenderemos algunas funciones básicas que podemos usar con OpenCV. Como requisitos para este tutorial tenemos:
* Una computadora con Windows 10, 11 o Linux.
* Jupyter Notebook.
* Python 3.

Primero debemos entrar a Jupyter Notebook en el siguiente [link](https://jupyter.org/try-jupyter/lab/) y copiar los archivos que se encuentran en este repositorio a una carpeta dentro del entorno de Jupyter como se muestra en la imagen.

Una vez hecho esto podemos comenzar con el tutorial.

## Combinación de imágenes
1. Abra dentro de jupyter el archivo llamado **mezclador.ipynb**. Dentro del script notará que está segmentado por bloques. 

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

## Ecualizador de imágenes (Histograma)
Este ecualizador se usa para una representación de la intensidad de una imagen. Por eso es que vamos a usar una imagen con un bajo contraste como la que se muestra a continuación.

![imagen_equalizador](https://github.com/Mercurio1509/Minitaller_OpenCV/assets/125401207/210ad2da-a8bd-4d79-8022-7aabbb4ea34e)


La manera en la funciona es cuantificando el número de pixeles por cada valor considerado.

Para el tutorial abra el archivo llamado `ecualizador.ipynb`. De igual manera este tutorial se divide en bloques.

1. Corra el bloque 1 donde se importan las librerias y se lee la imagen de entrada.

```ruby
#Bloque 1
#!pip install opencv-contrib-python

import cv2 as cv
import argparse
import matplotlib.pyplot as plt
 
src=cv.imread('imagen_equalizador.jpg')

if src is None:
    print('Could not open or find the image:', src)
    exit(0)
```

2. En el segundo bloque podemos ver que la imagen se transforma a una paleta de color gris con la función `cvtColor()`

```ruby
#Bloque 2
src = cv.cvtColor(src, cv.COLOR_BGR2GRAY)
```

3. Corremos el bloque 3 donde usaremos la función `equalizeHist()`.

```ruby
#Bloque 3
dst = cv.equalizeHist(src)
```
4. Pasamos al bloque 4 donde finalmente se van a imprimir los resultados de la ecualización, como podrá observar se usa `cv.imshow()` para graficar, además de esta función se usa matplotlib, donde se hace un arreglo con la función `img2_rgb = cv.cvtColor(dst, cv.COLOR_BGR2RGB)` que hace pasar la imagen de BGR a RGB ya que matplotlib necesita que la imagen use este ultimo formato, a diferencia de OpenCV que usa el formato BGR.

```ruby
# Bloque 4
cv.imshow('Source image', src)

img1_rgb = cv.cvtColor(src, cv.COLOR_BGR2RGB)
plt.imshow(img1_rgb)
plt.show()


cv.imshow('Equalized Image', dst)
img2_rgb = cv.cvtColor(dst, cv.COLOR_BGR2RGB)
plt.imshow(img2_rgb)
plt.show()

 
cv.waitKey(0)
cv.destroyAllWindows()
```

Una vez hecho esto podra ver como la imagen se aclara de la siguiente manera:

![image](https://github.com/Mercurio1509/Minitaller_OpenCV/assets/125401207/c3c64831-e16a-4fb8-b11b-52687909476c)


5. Ahora usted descargue una imagen de internet y guardela en la misma carpeta del repositorio, para poder asignar la imagen dentro del código vaya al bloque 1 y dentro de la variable `src=cv.imread('imagen_equalizador.jpg')` cambie la sección donde dice *imagen_equalizador.jpg* por el nombre de su imagen, observe los resultados.
