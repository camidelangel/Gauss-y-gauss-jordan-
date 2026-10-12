# Método de Gauss-Jordan modularizado

Este proyecto implementa el método numérico de **Gauss-Jordan** en Java para resolver sistemas de ecuaciones lineales. Se utiliza programación modular y reutilización de código, aprovechando el método de eliminación gaussiana desarrollado previamente.

El objetivo es transformar una matriz aumentada en una matriz identidad mediante la normalización de los pivotes y la eliminación de los coeficientes superiores, obteniendo directamente los valores de las incógnitas.

Implementamos el algoritmo de Gauss-Jordan en Java mediante la reutilización del método `Gauss.eliminacionGaussiana(matriz)`, complementándolo con la normalización de los pivotes y la eliminación de los coeficientes que se encuentran por encima de la diagonal principal.

### Descripción de las clases

* **Defmatriz.java:** define y devuelve la matriz aumentada del sistema de ecuaciones.
* **Gauss.java:** contiene el método `eliminacionGaussiana()`, que transforma la matriz en una matriz triangular superior.
* **Lanzador_Gauss.java:** permite ejecutar la implementación original del método de Gauss.
* **GaussJordan.java:** reutiliza la eliminación gaussiana y realiza la normalización de los pivotes y la eliminación de los coeficientes superiores.
* **Lanzador_GaussJordan.java:** ejecuta el método de Gauss-Jordan, muestra la matriz reducida y presenta las soluciones del sistema.

La clase `GaussJordan` pertenece al paquete `Ecuaciones_Lineales.GaussJordan`, independiente del paquete `Ecuaciones_Lineales.Gauss`. Para reutilizar el método existente se importa la clase `Gauss`.

## Funcionamiento

El método de Gauss-Jordan se desarrolla en los siguientes pasos:

1. **Definición de la matriz:** se construye la matriz aumentada que representa el sistema de ecuaciones lineales.
2. **Eliminación gaussiana:** se invoca `Gauss.eliminacionGaussiana(matriz)` para obtener una matriz triangular superior.
3. **Normalización de los pivotes:** se divide cada fila entre su pivote para convertir los elementos de la diagonal principal en unos.
4. **Eliminación de coeficientes superiores:** se realizan operaciones elementales entre filas para convertir en cero los coeficientes que están por encima de los pivotes.
5. **Obtención de las soluciones:** se extraen los valores de la última columna de la matriz aumentada.
6. **Presentación de resultados:** se imprime la matriz reducida y el valor de cada incógnita.

Al finalizar, la matriz aumentada adopta la forma `[I | X]`, donde `I` es la matriz identidad y `X` contiene el vector de soluciones.

##  Requisitos

Para compilar y ejecutar el proyecto se necesita:

* Tener instalado el JDK de Java.
* Contar con una terminal o consola de comandos.
* Disponer de los archivos fuente `.java` organizados en sus respectivos paquetes.

## Compilación y ejecución

### Paso 1. Abrir una terminal

Ubicarse en el directorio raíz del proyecto, donde se encuentra la carpeta `src`.

### Paso 2. Compilar el proyecto

Ejecutar el siguiente comando:

```bash
javac -d out src/Ecuaciones_Lineales/Gauss/*.java src/Ecuaciones_Lineales/GaussJordan/*.java
```

Este comando compila las clases de ambos paquetes y coloca los archivos `.class` generados en la carpeta `out`.

### Paso 3. Ejecutar el programa

Ejecutar el lanzador de Gauss-Jordan:

```bash
java -cp out Ecuaciones_Lineales.GaussJordan.Lanzador_GaussJordan
```

El programa mostrará la matriz aumentada original, la matriz reducida y las soluciones de las incógnitas.

## Ejemplo de prueba

Se utiliza el siguiente sistema de ecuaciones lineales:

$$
\begin{aligned}
3x_1-0.1x_2-0.2x_3&=7.85\\
0.1x_1+7x_2-0.3x_3&=-19.3\\
0.3x_1-0.2x_2+10x_3&=71.4
\end{aligned}
$$

La matriz aumentada correspondiente es:

```text
[ 3.0  -0.1  -0.2 |   7.85 ]
[ 0.1   7.0  -0.3 | -19.30 ]
[ 0.3  -0.2  10.0 |  71.40 ]
```

### Salida esperada por consola

```text
Matriz aumentada original:
      3.0000     -0.1000     -0.2000      7.8500
      0.1000      7.0000     -0.3000    -19.3000
      0.3000     -0.2000     10.0000     71.4000

Matriz reducida por Gauss-Jordan:
      1.0000      0.0000      0.0000      3.0000
      0.0000      1.0000      0.0000     -2.5000
      0.0000      0.0000      1.0000      7.0000

Soluciones del sistema:
x1 = 3.0000
x2 = -2.5000
x3 = 7.0000
```

Las soluciones obtenidas son:

* \(x_1=3\)
* \(x_2=-2.5\)
* \(x_3=7\)

## Reutilización de código

Una de las características principales de esta implementación es la reutilización del método de eliminación gaussiana:

```java
Gauss.eliminacionGaussiana(matriz);
```

Esta llamada evita volver a implementar el proceso de eliminación de los coeficientes inferiores. Después, la clase `GaussJordan` completa la reducción de la matriz mediante la normalización de los pivotes y la eliminación de los coeficientes superiores.

Además, al pasar la matriz como argumento, los cambios se realizan sobre el mismo arreglo bidimensional, por lo que no es necesario crear otra matriz para continuar el procesamiento.

* La implementación requiere una matriz aumentada cuadrada en sus coeficientes, con una columna adicional para los términos independientes.
* El algoritmo necesita pivotes distintos de cero para poder normalizar las filas.
* La implementación reutilizada de eliminación gaussiana no contempla necesariamente el pivoteo parcial; por ello, algunos sistemas pueden requerir un intercambio de filas para evitar pivotes nulos o numéricamente inestables.
* El resultado depende de que la matriz y los métodos utilizados sean correctos.

## Conclusión

La implementación del método de Gauss-Jordan permite resolver sistemas de ecuaciones lineales mediante operaciones elementales sobre una matriz aumentada. Al reutilizar el método de eliminación gaussiana previamente desarrollado, se evita duplicar código y se mejora la organización del programa.

La separación en paquetes y clases facilita el mantenimiento, la comprensión y la ampliación del proyecto. Finalmente, la normalización de los pivotes y la eliminación de los coeficientes superiores permiten obtener directamente las soluciones del sistema, sin necesidad de aplicar sustitución regresiva.

## Datos del alumno
Instituto Tecnológico Superior de Xalapa.

Métodos Numéricos.

Víctor Hugo Vásquez Herrera

**Unidad 3 — Método de Gauss**

Sistemas Computacionales 3ro "B"

Camila amor del angel cervantes 

11/10/2026
