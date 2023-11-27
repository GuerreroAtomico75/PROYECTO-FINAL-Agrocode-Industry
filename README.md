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

---

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

---

### Datalles a tener en cuenta al momento crear el código
* **Tema**: El tema de la sopa de letras será de conceptos que se vieron en el curso.
* **Tiempo**: No tendremos un tiempo límite para encontrar todas las palabras de la sopa de letras, pero al final de la sopa de letras al encontrar todas las palabras se brindará el tiempo que se tardó el usuario en encontrar todas las palabras.
* **Tamaño**: La matriz será de 15x15 palabras.

---

### Código

En este momento se podrá ver el código que generará el juego de la sopa de letras, pero más adelante se analizará cada parte del código.

```python
import random
import string
import time

def generar_sopa(dificultad):
    if dificultad == "noob":
        palabras = ["algoritmo", "instrucciones", "pseudocodigo", "variables", "entero", "lenguaje", "flotante",
                    "constante", "booleano", "strings", "operadores", "listas"]
    elif dificultad == "decente":
        palabras = ["condicional", "input", "indentacion", "if", "elif", "else", "funcion", "libreria", "alcance",
                    "import", "while", "break", "continue", "for", "rango"]
    elif dificultad == "good":
        palabras = ["arreglo", "mutabilidad", "indice", "concatenar", "pertenencia", "slicing", "len", "append",
                    "pop", "insert", "remove", "count", "sort", "matriz", "split", "replace", "format", "tupla",
                    "diccionario", "find", "identidad"]

    sopa = [[random.choice(string.ascii_lowercase) for _ in range(15)] for _ in range(15)]

    for palabra in palabras:
        colocar_palabra(sopa, palabra)

    # Imprimir las posiciones de las palabras
    for palabra in palabras:
        for fila in range(15):
            for columna in range(15):
                if verificar_palabra(sopa, palabra, fila, columna):
                    print(f'Palabra "{palabra}" empieza en la fila {fila}, columna {columna}')

    return sopa

def colocar_palabra(sopa, palabra):
    direccion = random.choice(["horizontal", "vertical"])
    if direccion == "horizontal":
        fila = random.randint(0, 14)
        columna = random.randint(0, 15 - len(palabra))
        for i in range(len(palabra)):
            sopa[fila][columna + i] = palabra[i]
    else:
        fila = random.randint(0, 14 - len(palabra))
        columna = random.randint(0, 14)
        for i in range(len(palabra)):
            sopa[fila + i][columna] = palabra[i]

def mostrar_sopa(sopa):
    for fila in sopa:
        print(" ".join(fila))
    print()

def jugar_sopa(sopa):
    palabras_encontradas = set()
    inicio_tiempo = time.time()

    while True:
        mostrar_sopa(sopa)
        x = int(input("Ingrese la fila (0-14): "))
        y = int(input("Ingrese la columna (0-14): "))

        palabra = input("Ingrese la palabra encontrada: ")

        if palabra in palabras_encontradas:
            print("¡Ya encontraste esa palabra!")
            continue

        if verificar_palabra(sopa, palabra, x, y):
            print("¡Correcto! Palabra encontrada.")
            palabras_encontradas.add(palabra)
        else:
            print("Incorrecto. Inténtalo de nuevo.")

        if len(palabras_encontradas) == len(set(palabra for palabra in palabra)):
            break

    tiempo_total = time.time() - inicio_tiempo
    print(f"Felicidades, has encontrado todas las palabras en {tiempo_total:.2f} segundos.")

def verificar_palabra(sopa, palabra, x, y):
    # Verificar horizontal
    if y + len(palabra) <= 15 and all(sopa[x][y + i] == palabra[i] for i in range(len(palabra))):
        return True
    # Verificar vertical
    if x + len(palabra) <= 15 and all(sopa[x + i][y] == palabra[i] for i in range(len(palabra))):
        return True
    return False

def mostrar_instrucciones():
    print("Instrucciones:")
    print("1. Encuentra todas las palabras en la sopa de letras.")
    print("2. Ingresa las coordenadas (fila y columna) y la palabra encontrada.")
    print("3. Puedes ingresar 'salir' en cualquier momento para terminar el juego.")

def mostrar_definiciones():
    print("Definiciones:")
    print(" - Algoritmo: Conjunto de pasos ordenados para realizar una tarea.")
    print(" - Condicional: Estructura de control que ejecuta cierto bloque de código si se cumple una condición.")
    print(" - Arreglo: Colección de elementos del mismo tipo, accesibles mediante un índice.")
    # ... Agrega más definiciones según tus necesidades.

def main():
    print("¡Bienvenido al juego de Sopa de Letras!")
    mostrar_instrucciones()

    while True:
        print("\nSelecciona el nivel:")
        print("1. Noob")
        print("2. Decente")
        print("3. Good")
        print("4. Salir")

        seleccion_nivel = input("Ingresa el número de nivel o 'salir': ")

        if seleccion_nivel == "salir":
            print("Gracias por jugar. ¡Hasta luego!")
            break

        if seleccion_nivel not in ["1", "2", "3"]:
            print("Selección no válida. Inténtalo de nuevo.")
            continue

        nivel = {"1": "noob", "2": "decente", "3": "good"}[seleccion_nivel]
        sopa = generar_sopa(nivel)

        print(f"\n¡Nivel {nivel.capitalize()} seleccionado!")
        mostrar_definiciones()
        input("Presiona Enter para comenzar...")

        jugar_sopa(sopa)

if __name__ == "__main__":
    main()
```

#### Análisis del código

---

```python
import random
import string
import time
```

* Lo primero que hacemos es importar la librería random, string y time.
* La librería random se utilizará a la hora de elegir un número del código ASCII de las letras minúsculas, para que así se elijan letras al azar.
* La librería string se utilizará para el método .ascii_lowercase, el cual devuelve letras en minúscula del código ASCII.
* La librería time se utilizará para contar el tiempo que se demore el usuario en completar la sopa de letras.

---

```
