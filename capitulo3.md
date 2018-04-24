#Variables y tipos de datos en Haskell.

Valores, funciones y tipos son los bloques fundamentales de construcción de un programa en
Haskell. Los conceptos de funciones y valores fueron desarrollados en el capítulo previo, lo
que resta es introducir los tipos de datos disponibles y el comportamiento de las variables.

## Variables
Hasta ahora los ejemplos que estuvimos realizando fueron cálculos simples, por lo que para
cálculos de mayor complejidad precisamos mantener un seguimiento de los valores iniciales,
resultados intermedios y finales de las operaciones. Acá es donde ingresan las variables, una
variable es utilizada para identificar y almacenar datos o información, es útil pensar en la
variable como contenedor de información. Al definir un nombre descriptivo para identificarla,
se facilita la utilización de la misma y por consiguiente la comprensión del programa.
Durante la etapa de diseño del programa necesitaremos crear, modificar o eliminar tantas
variables como se precisen en los cálculos y tareas demandadas.
Pasemos a un ejemplo, vamos a crear un archivo Haskell, yo lo nombré *variables.hs* y
definimos una variable dentro del mismo:

*variables.hs*
```Shell
   numero = 5
```

Compilamos el código en GHCi:

```Shell
   Prelude> :l variables.hs
   [1 of 1] Compiling Main   ( variables.hs, interpreted )
   Ok, modules loaded: Main.
   *Main> variable
   5
```

Vemos que la variable está definida y tiene una valor asignado. La podemos emplear en una
función, por ejemplo digamos que precisamos calcular la potencia cúbica de un número y
elegimos a la base como variable:

*variables.hs*
```Shell
   numero = 5
   potencia_cubica = numero ^ 3
```

Compilamos y llamamos a la función:

```Shell
   Prelude> :l variables.hs
   [1 of 1] Compiling Main   ( variables.hs, interpreted )
   Ok, modules loaded: Main.
   *Main> potencia_cubica
   125
```
A medida que se continúe con el desarrollo y aumente la cantidad de líneas en el código,
utilizar una variable llamada *numero* no va a ser representativo de su objetivo, por lo que es
renombrada a *base*.

*variables.hs*
```Shell
   base = 5
   potencia_cubica = base ^ 3
```
Se puede apreciar cómo se mejoró la legibilidad del código, ya que si el ciclo de vida del
sistema es de varios años, es muy probable que sea leído y mantenido por otras personas
distintas de las que lo diseñaron y programaron.

Llamo a la función en GHCi:

```Shell
   *Main> potencia_cubica
   125
```

Si quiero realizar otro cálculo, modifico el valor asignado a la variable:

```Shell
   *Main> base = 10
   *Main> potencia_cubica
   125
```
¿Por qué si llamamos a la función siendo el valor de *base* 10 continúa devolviendo 125 como
resultado? Hay que tener cuidado, ya que el comportamiento quizás no vaya a ser el esperado,
la función siempre va a devolver el resultado dependiendo del valor con el que fué inicializada
cada variable al momento de compilar el archivo fuente.

```Shell
   *Main> potencia2 = base ^ 3
   *Main> potencia2
   1000
```
Ahora si definimos dinámicamente una nueva función *potencia2*, la cual emplee la variable
*base*, el resultado es el esperado previamente.

Modifiquemos el código fuente y cambiemos el valor de la variable:

*variables.hs*
```Shell
   base = 10
   potencia_cubica = base ^ 3
```

Volvemos a compilar el código:

```Shell
   Prelude> :l variables.hs
   [1 of 1] Compiling Main   ( variables.hs, interpreted )
   Ok, modules loaded: Main.
   *Main> potencia_cubica
   1000
```
Al llamar la función obtenemos el resultado deseado.

Hay que tener en claro y poder diferenciar entre el código fuente compilado y cargado para su
uso en GHCi y lo que estamos operando propiamente en GHCi.
Las pruebas constituyen una parte esencial para cumplir con los requerimientos definidos
durante el proceso de codificación. Sin embargo, puede resultar tedioso hacer los cambios en
el código fuente, compilar y volver a probarlo en GHCi como pudimos verificar en los
ejercicios previos. Una alternativa, es definir las variables directamente utilizando la palabra
reservada *let* dentro de GHCi:

```Shell
   *Main> let numero = 5.0
   *Main> numero * pi
   15.707963267948966
   
   Prelude> numero = 10
   Prelude> numero * pi
   31.41592653589793
```

Hemos definido una variable llamada *numero* y la empleamos en una multiplicación con el
número π. A la variable se le puede asignar un nuevo valor sin inconveniente alguno y de ésta
manera realizar las pruebas que se consideren necesarias sin necesidad de recurrir a escribir el
código en un archivo fuente.

## Tipos
Los valores pueden ser agrupados en conjuntos con propiedades similares, llamamos tipos a
esos conjuntos de valores. Algunos tipos que maneja Haskell son similares a la mayoría de los
lenguajes de programación como por ejemplo:

- **Int**: Se emplea para números enteros. Los valores máximos y mínimos dependen del
tipo de arquitectura del procesador. Int es limitado, tiene un límite para el valor mínimo
y máximo que almacena. Para máquinas de 32-bit el valor máximo posible es
2147483647 y el mínimo es -2147483648.
Int: Int = {..., -3, -2, -1, 0, 1, 2, 3, ...}
- **Integer**: e diferencia de int en que no tiene un límite para el valor máximo o mínimo,
por lo que sirve para representar números de varios dígitos. Como contrapartida, es
menos eficiente que *Int*.
- **Float**: Tipo de dato para números de punto flotante o decimales con precisión simple
(32 bits). Realiza una aproximación porque no pueden ser representados de forma
precisa en una computadora con un número fijo de bits.
Float = {..., -1232.42342, ..., 1.0, 3.141, ...}
- **Double**: Tiene el doble de precisión que float, empleando el doble de bits para
almacenar la información.
Double = {... , -1232.42342, ..., 1.0, 3.141, ...}
- **Char**: Representa un caracter que puede ser letra, dígito, nueva línea, tab entre otros
símbolos. Haskell incluye la codificación Unicode completa. Su contenido se define en
comillas simples.
Char = {..., 'a', 'A', 'b', 'B', ...'1', ..., '@', '#', ...}
- **String**: Son secuencias de caracteres. Su contenido se define en comillas dobles.
String = {"", "a", "b", ..., "Hi" ,"3423#", ...}
- **Bool**: Representan un tipo booleano y puede tener únicamente 2 valores: Verdadero o
Falso.
Bool = {False, True}

*Ejecución en GHCi*:
```Shell
   Prelude> entero = 12
   Prelude> print entero
   12
   Prelude> flotante = 12.987
   Prelude> print flotante
   12.987
   Prelude> doble =
   12.98733333444445566777764542122121212323234354345
   Prelude> print doble
   12.98733333444445566777764542122121212323234354345
   Prelude> caracter = 'a'
   Prelude> putChar caracter
   a
   Prelude> cadena = "hola"
   Prelude> putStrLn cadena
   hola
   Prelude> booleano = False
   Prelude> print booleano
   False
```

## Tipos de datos

Las variables son de un cierto tipo, el cual define su representación lógica y tamaño en
memoria.
	Haskell posee tipo de dato estático, significa que el tipo de dato se define previamente antes de
realizar la compilación. Al definir una variable el compilador sabe qué pieza de código es un
número, un caracter, etc.; esto quizás les parezca familiar de C y C++ pues también poseen
ésta propiedad.
	En otros lenguajes de programación como Python o Ruby el tipo de dato es dinámico. Esto
significa que el tipo de una variable puede cambiar y ser resuelto al momento exacto en el
código es parseado por el intérprete. Se puede definir una variable a como flotante y unas
líneas posteriores ser empleada para almacenar un entero.
	Haskell es fuertemente tipado como C, C++, Python o Ruby. Si estamos realizando una
operación con números enteros, no puedo utilizar una cadena de texto:

```Shell
   Prelude> 1 + 1
   2
   
   Prelude> 1 + "hola"
   <interactive>:7:3:
   No instance for (Num [Char]) arising from a use of `+'
   Possible fix: add an instance declaration for (Num [Char])
   In the expression: 1 + "hola"
   In an equation for `it': it = 1 + "hola"
```
Haskell fuerza a que se respete el tipo de dato a utilizar.

En otro ejemplo se intenta hacer una operación entre un booleno y la constante *Pi*:

```Shell
   Prelude> let valor = True
   Prelude> pi * valor
   <interactive>:8:1: error:
   • No instance for (Floating Bool) arising from a use of ‘pi’
   • In the first argument of ‘(*)’, namely ‘pi’
   In the expression: pi * valor
   In an equation for ‘it’: it = pi * valor
   <interactive>:8:1: error:
   • No instance for (Num Bool) arising from a use of ‘*’
   • In the expression: pi * valor
   In an equation for ‘it’: it = pi * valor
```
Obteniendo los mensajes de errorers advirtiendo que no es posible realizar la operación.

Por otra parte, en el lenguaje Visual Basic que es débilmente tipado, el siguiente código es
totalmente válido:

```Shell
   Dim edad As Integer, texto As String
   texto = "Tú edad es: "
   edad = 23
   MsgBox texto & edad
   
```

En Haskell no hubiera sido posible imprimir la cadena de texto y concatenar un número para
completar la oración, se tiene que forzar (Casteo) a que el número (Entero) se imprima como
string empleando la función *show* para tal fin:

```Shell
   Prelude> texto = "Tú edad es: "
   Prelude> edad = 23
   Prelude> putStrLn (texto ++ show edad)
   Tú edad es: 23

```
La función *putStrLn* toma como argumento la concatenación de las variables *texto* y *edad*.
