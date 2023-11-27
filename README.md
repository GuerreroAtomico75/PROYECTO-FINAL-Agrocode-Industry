# PROYECTO-FINAL-Agrocode-Industry

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

#### Análisis del problema

Los puntos que tuvimos en cuenta para resolver el problema antes de editar código fueron los siguientes:

* 

**Código**
```python
# Primero creamos una función que nos dará los digitos separados del número 'n' ingresado por el usuario. Es decir, digitosSeparados en función de n
def digitosSeparados(n: int) -> int: #Aplicaremos la función recursiva
    #La función base es si n es igual a 0, el dígito será 0, aunque si no aparecía nada en la lista no habría problema ya que 0 no representa un valor
    if n == 0:
        digitosListaRev.append(n)
        return digitosListaRev
    # La función recursiva es la siguiente:
    else:
        #Para esto creamos un ciclo, el cual funcionará siempre que 'n' sea mayor que 0
        while n > 0:
            #Vamoa a separar los digitos de la siguiente manera: Creamos la variable 'd' que será el dígito que en ese momento se esté trabajando. El resultado de 'd' será 'n' módulo 10.
            #El residuo de la división anterior será el digito que se trabaje.
            d = n % 10
            #Ese resultado lo añadimos a la lista creado en la función main
            digitosListaRev.append(d)
            #Tenemos que actualizar 'n' en diviendo el valor de 'n' en 10, esto hará que el dígito que ya se ingresó a la lista no se tome en cuenta en el siguiente ciclo
            n = n // 10
        # Creamos una nueva variable que será la lista creada aplicando slicing para que la lista quede ordenada.
        digitosLista = digitosListaRev[::-1]
        # Se nos retorna la variable de la lista ordenada
        return digitosLista

if __name__ == "__main__":
    #En la función main creamos la variable 'n' que será un entero ingresado por el usuario
    n : int = int(input("Ingrese el número entero que usted desee: "))
    #Esta es la lista en la cual ingresamos los digitos.
    digitosListaRev = []
    #Creamos la variable digitos donde llamamos a la función que hicimos al inicio
    digitos = digitosSeparados(n)
    #Imprimimos
    print("Los digitos del número deseado por el usuario son los sigueintes", digitos)
```

