# Práctica 07. Iteraciones

# Factor de ponderación: 7

### Objetivos
Los objetivos de esta práctica son que el alumnado:
- Sea capaz de resolver problemas sencillos en C++ usando todos los conocimientos adquiridos hasta ahora, y en particular haciendo uso de sentencias iterativas
- Comience a utilizar funciones en sus programas y modularice sus programas en diferentes funciones

### Rúbrica de evaluación de esta práctica
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva) que se tendrán en cuenta a la hora de evaluar esta práctica. Se comprobará que el alumnado:
- Es capaz de escribir programas simples en C++ que resuelvan problemas de complejidad similar a los que se han propuesto para esta práctica
- Hace que sus programas se estructuren en torno a diferentes funciones (sean modulares)
- Ha automatizado la compilación de sus programas usando un fichero `Makefile` para cada uno de los programas que desarrolle 
- Acredita que es capaz de subir programas a la plataforma [Jutge](https://jutge.org/) para su evaluación
- Ha incluido un comentario prólogo en todos los ficheros (`*.cc`, `*.h`) de sus ejercicios
- Hace que todos los programas de sus prácticas se ajusten a la [Guía de estilo de Google para C++](https://google.github.io/styleguide/cppguide.html) 
- Acredita que es capaz de editar ficheros remotos en su VM usando vi
- Demuestra que es capaz de ejecutar comandos Linux en su VM

### Diseño de los programas
Recuerde las que se han estudiado como *Buenas Prácticas* a la hora de diseñar sus funciones:
- El código deberá organizarse en diferentes funciones 
- Cada función deberá realizar una única tarea y hacerlo correctamente 
- El identificador de una función debe reflejar claramente lo que la función hace 

Tal como se indica en [How to design your first programs](https://www.learncpp.com/cpp-tutorial/how-to-design-your-first-programs/), su código debiera estar organizado en torno a funciones que se invocan desde la función `main`. Así, la apariencia habitual de la función principal de cualquier programa debería ser algo similar a:
``` .cpp
int main(int argc, char* argv[]) {
  PrintProgramPurpose();
  if (!CheckCorrectParameters(argc, argv, 3)) {
    return 1;
  }
  int value{GetUserInput()};
  double result{ComputeResult(value)};
  PrintResult(result);
  return 0;
}
```
en el sentido de que la función `main` es una mera *orquestadora* de las funciones que componen el programa. `main` pasa a esas funciones los parámetros necesarios para su funcionamiento y las diferentes funciones devuelven a `main` el valor que calculan (si fuera el caso).

Incluya en todos sus programas dos funciones con la siguiente declaración:
```
void PrintProgramPurpose();
bool CheckCorrectParameters(int argc, char *argv[], int kCorrectNumber);
```
La primera de ella se invocará al comienzo de la ejecución para imprimir un mensaje explicativo de la finalidad del programa en cuestión. La segunda devolverá *verdadero* si al programa se le ha pasado el número adecuado de parámetros por línea de comandos (3 en el ejemplo anterior) y *falso* en caso contrario. Estudie el programa [check-correct-parameters.cc](https://github.com/ULL-IB/code-examples/blob/main/functions/check-correct-parameters.cc) de los ejemplos de código de las clases de teoría, que ilustra el uso de estas dos funciones.

### Material de estudio complementario
Estudie todo lo que se indica en el epígrafe [Comments](https://google.github.io/styleguide/cppguide.html#Comments) de la Guía de Estilo de Google y ponga en práctica todo lo que en ella se propone.

Estudie del [tutorial de referencia](https://www.learncpp.com/) en la asignatura los siguientes apartados:
- [Comments](https://www.learncpp.com/cpp-tutorial/comments/)
- El capítulo 2 [Basics: Functions and Files](https://www.learncpp.com/cpp-tutorial/introduction-to-functions/) (completo)
- [Command line arguments](https://www.learncpp.com/cpp-tutorial/command-line-arguments/)

### Ejercicios
- Dentro de su directorio de trabajo para esta práctica, cree un subdirectorio diferente para cada uno de los ejercicios que realice. Asigne un nombre significativo a cada uno de ellos. 
- Automatice la compilación del programa correspondiente a cada ejercicio con un fichero `Makefile` independiente. Incluya el mismo en el correspondiente subdirectorio.
- Una vez complete un ejercicio, recuerde ejecutar `make clean` para eliminar los ficheros innecesarios y dejarlo listo para entregar.
- Practique a recibir los valores necesarios para la ejecución de cada ejercicio desde la *línea de comandos* (`argc, argv`). Tenga en cuenta sin embargo que los ejercicios que haga para *Jutge* aún tendrán que recibir los datos desde el teclado.

1. Escriba un programa que reciba un número natural (entero positivo) e imprima como por pantalla la suma de sus dígitos. 
    ```
    Public test cases
    Input   Output
    2022    6
    1492    16
    0       0
    ```
    
2. La [serie de Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_number) es aquella en la que cada uno de sus términos se calcula como la suma de los dos términos anteriores. Desarrolle un programa que imprima los *N* primeros términos de la serie de Fibonacci cuyos dos primeros términos son 0 y 1.
    ```
    Public test cases
    Input   Output
    5       0 1 1 2 3
    9       0 1 1 2 3 5 8 13 21
    1       0
    20      0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181
    ```
    
3. Estudie en el tutorial *Learn C++* los epígrafes [Numeral systems (decimal, binary, hexadecimal, and octal)](https://www.learncpp.com/cpp-tutorial/numeral-systems-decimal-binary-hexadecimal-and-octal/) y [Converting between binary and decimal](https://www.learncpp.com/cpp-tutorial/converting-between-binary-and-decimal/).
    
    Escriba un programa `binary-to-decimal.cc` que convierta números binarios a base decimal. No utilice los tipos `std::string`, `std::vector` o `std::array`, se considerará que un número binario se expresa como un valor entero positivo cuyos dígitos son únicamente ceros y unos. Si la entrada no fuera un número binario, el programa debe imprimir en pantalla un mensaje de error y finalizar la ejecución.
    ```
    Public test cases
    Input      Output
    1111       15
    1011110    94
    1018110    Wrong Input
    10010111   151
    ```
    
4. Escriba un programa `decimal-to-binary.cc` que convierta números de decimal a binario, siguiendo el mismo esquema antes descrito. No utilice los tipos `std::string`, `std::vector` o `std::array`.
    ```
    Public test cases
    Input   Output
    15      1111
    94      1011110
    151     10010111
    ```
    
5. Escriba un programa `leap-year.cc` que indique si un año es [bisiesto](https://en.wikipedia.org/wiki/Leap_year) o no. Después de la reforma gregoriana, se determinó que los años bisiestos son aquellos que son divisibles entre 400 o que son divisibles entre 4 pero no entre 100. Así, 1800 y 1900, a pesar de ser múltiplos de cuatro, no fueron años bisiestos; por el contrario, 2000 fue un año bisiesto.

    ```
    Public test cases
    Input   Output
    1999    NO
    1968    YES
    2000    YES
    1800    NO
    ```

Tenga en cuenta que en la evaluación de las prácticas de *Informática Básica* se utilizarán ejercicios de *Jutge*, de modo que resolver problemas en esa plataforma mejorará sus capacidades como programador/a. Realice todos los ejercicios que sea capaz. Recuerde siempre que *Jutge* sólo evalúa la corrección de su programa desde un punto de vista de su correcto funcionamiento. Su código ha de cumplir además con los requisitos de modularidad, formato y estilo.
