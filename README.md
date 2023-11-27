t# PROYECTO-FINAL-Agrocode-Industry

**Nombre del grupo:**

Agrocode Industry

**Integrantes:**

* Paula Jiménez Quiñones
* Mario Alejandro Martinez
* David Rodriguez Rueda

**Logo:**

![logo](https://github.com/pjimenezq/Taller_1/assets/141860508/136373ec-f9a4-4b51-a52a-1b1e893e1859)

## Solución del problema:

#### Problema
**Instrucción**

Construir una aplicación que emule una sopa de letras utilizando Python.

Condiciones:

* Código original
* Uso de herramientas vistas en el curso
* Interacción y manejo a través de la consola
* Definidido por el usuario:
* Matriz del tamaño de la sopa de letras (Min: 10x10, Max: 30x30)
* Ingreso de las palabras: Lista de coordenadas, Strings.
* Nivel de dificultad: Asociado a cantidad de palabras, verticales, horizontales, diagonal.

### Análisis del problema

#### Análisis del problema antes de crear el código

Los puntos que tuvimos en cuenta para resolver el problema antes de editar código fueron los siguientes:

* Primero se tiene en cuenta que será una sopa de letras por nivel de dificultad, para ello se le pedirá al usuario que ingrese un carácter o una cadena de carácteres con el cual se sabrá cuál nivel de dificultad está escogiendo.
* Los niveles de dificultad que tendremos para la sopa de letras son los siguientes:
  * Noob
  * Decente
  * God
* La diferencia de dificultad se observará en la cantidad de palabras que hay que encontrar.
* Al momento de escoger la dificultad se generará la matriz, esta matriz tendrá 15 arreglos (que son la cantidad de filas) de un tamaño de 15 elementos. Cada letra puede corresponder a una palabra o a una una letra al azar.
* Se necesitará generar letras al azar, que no intercedan con letras de las palabras que estarán en la sopa de letras.
* Será necesario que al momento que el usuario encuentre una palabra pueda seleccionarla, teniendo en cuenta las filas y las columnas de la sopa de letras.
* Si cada vez que se escoge una letra a través de las coordenadas, es una letra que conforma una de las palbras que se va a encontrar; entonces se le pedirá al usuario que ingrese la palabra que encontró. Si los dos pasos anteriores son correctos entonces se habrá encontrado una palabra; sino entonces se avisará que no es una palabra que es parte de las que hay que encontrar y se vuelve a tener la oportunidad de seguir escogiendo palabras.

#### Datalles a tener en cuenta al momento crear 

**Código**
```python
```

