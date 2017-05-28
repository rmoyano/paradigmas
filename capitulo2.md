#GHCi: El ambiente interactivo de Haskell. 

En ésta sección del documento, se explicará como utilizar el ambiente interactivo del
lenguaje, cuyo uso va a facilitar la tarea de desarrollo al programador.

Antes de continuar vamos a explicar la diferencia entre lenguajes interpretados y
lenguajes compilados. 
La compilación es el proceso de traducir el código fuente de un programa a código objeto, generando 
el ejecutable o binario. El programa encargado de compilar se llama compilador.
Para los lenguajes interpretados, cada instrucción debe pasar por una interpretación en tiempo de ejecución, 
intenta realizar "al vuelo" lo que se expresa en los archivos fuente. El encargado de hacer esto es un 
programa llamado intérprete. A diferencia del compilador, el intérprete de un lenguaje no produce una 
traducción a código máquina.

La tarea de GHCi consiste en evalúar las expresiones de Haskell interactivamente además de soportar 
la carga de código compilado, así como el soporte para todas las extensiones del lenguaje que GHC provee.
Asimismo, GHCi incluye un depurador interactivo (GHCi Debugger).

## Manejo del ambiente
Al ejecutar GHCi, va mostrando por la terminal:
1. La versión del software (7.6.3).
2. Enlace a la página del proyecto.
3. Comando para mostrar la ayuda (:?).
4. Los paquetes que carga (ghc-prim, integer-gmp, base.).
5. Prelude

```Shell
   rafa@pc:~/home/unlar$ ghci
   GHCi, version 7.6.3: http://www.haskell.org/ghc/  :? for help
   Loading package ghc-prim ... linking ... done.
   Loading package integer-gmp ... linking ... done.
   Loading package base ... linking ... done.
   Prelude> 
```
###Prelude
Prelude es el módulo que GHCi automáticamente llama y carga en memoria. Es un módulo que posee el conjunto de funciones destinadas a proporcionar las funcionalidades básicas para el ambiente.

###Built-in functions
Entre las diversas funciones que *Prelude* provee por defecto están los operadores matemáticos (Suma, resta, multiplicación, división, potencia, etc.) que permiten utilizar el ambiente como una calculadora. Cuando se tipea una expresión en la consola, inmediatamente es evaluada por GHCi e imprime el resultado: 
```Shell
   Prelude> 2+2
   4
   Prelude> 2*3
   6
   Prelude> 2**4
   16.0
```
También se puede utilizar funciones como *redondeo hacia arriba* (Superior en éste caso):
```Shell
  Prelude> ceiling 10.4
  11
  Prelude> ceiling 10.2
  11
  Prelude> ceiling 8.9
  9
```
Otro ejemplo es la función *par* (Devuelve verdadero o falso):
```Shell
  Prelude> even 10
  True
  Prelude> even 11
  False
```
##Comandos
Los comandos son las instrucciones que utiliza el ambiente para el manejo del mismo. No están relacionadas con las funciones del lenguaje en sí mismo.

La tecla TAB nos permite autocompletar las funciones y comandos mostrando las opciones disponibles para terminar de completar de acuerdo a los caracteres que fuimos presionamos.
```Shell
  Prelude> a
  abs         acos        acosh       all         and         any         appendFile  asTypeOf    asin        asinh       atan        atan2       atanh
  Prelude> as
  asTypeOf  asin      asinh
```

Utilizando las teclas de dirección para arriba(↑) o abajo (↓) permiten navegar por el historial de ejecución.
Ejemplo utilizando la tecla de dirección para arriba 3 veces después de ejecutar las operaciones matemáticas:
```Shell
   Prelude> 2+2
   4
   Prelude> 2*3
   6
   Prelude> 2**4
   16.0
   Prelude> 2**4
   Prelude> 2*3
   Prelude> 2+2
```
Para ejecutar la mayoría de los comandos la sintaxis involucra el uso del caracter *:*  como prefijo: 
**:[comando]<expresión>**

La ayuda es un ejemplo rápido de ello, se lo invoca utilizando *:?* y muestra una lista de comandos disponibles:
```Shell
   Prelude> :?
   Commands available from the prompt:

      <statement>                 evaluate/run <statement>
      :                           repeat last command
      :add [*]<module> ...        add module(s) to the current target set
      :browse[!] [[*]<mod>]       display the names defined by module <mod> (!: more details; *: all top-level names)
      :cd <dir>                   change directory to <dir>
      :cmd <expr>                 run the commands returned by <expr>::IO String 
      :def <cmd> <expr>           define command :<cmd> (later defined command has precedence, ::<cmd> is always a builtin command)
      :edit <file>                edit file
      ...
      ...
```
Por ejemplo si ejecutamos *:show*:
```Shell
   Prelude> :show
   options currently set: none.
   base language is: Haskell2010
   with the following modifiers:
   -XNoDatatypeContexts
   -XNondecreasingIndentation
   GHCi-specific dynamic flag settings:
   other dynamic, non-language, flag settings:
   -fimplicit-import-qualified
   warning settings:

   Para volver a ejecutar el último comando empleamos *:*
   Prelude> :
   options currently set: none.
   base language is: Haskell2010
   with the following modifiers:
   -XNoDatatypeContexts
   -XNondecreasingIndentation
   GHCi-specific dynamic flag settings:
   other dynamic, non-language, flag settings:
   -fimplicit-import-qualified
   warning settings:
```

##Carga de archivos
Dado que Haskell es un lenguaje funcional, vamos a comenzar creando un archivo y escribiendo una función en el mismo. Para tal fin necesitamos cualquier editor
de texto plano como [Notepad++](https://notepad-plus-plus.org/) y guardamos el código con el nombre ejemplo.hs,
siendo .hs la extensión para el código fuente de Haskell como lo es .cpp para C++:
```Haskell
   doble x = x * 2 
```
Para cargar el código en GHCi debemos indicarle la ruta a dónde se encuentra el archivo, en el que caso que se encuentre en el mismo lugar dónde ejecutamos GHCi, sólo con pasar como argumento el nombre del archivo es suficiente:
```Shell
   Prelude> :load ejemplo.hs 
   [1 of 1] Compiling Main             ( ejemplo.hs, interpreted )
   Ok, modules loaded: Main.
   *Main>
```
El mensaje nos indica que el código fué compilado exitosamente y el módulo cargado por lo que lo probamos llamando a la función doble con el valor 4 como argumento:
```Shell
   *Main> doble 4
       8

```
En el caso de haber guardado el código en otro directorio diferente, ingresamos el path absoluto hasta donde se encuentre el archivo:
```Shell
   Prelude> :load c:\directorio\subdirectorio\subdirectorio\ejemplo.hs
   [1 of 1] Compiling Main             ( ejemplo.hs, interpreted )
   Ok, modules loaded: Main.
   *Main>
```
También podemos comentar el objetivo que cumple la función empleando dos guiones consecutivos:
```Haskell
   -- Función que calcula el doble del número ingresado como argumento.
   doble x = x * 2 
```

Guardamos los cambios y en vez escribir el comando *load*, podemos utilizar otro comando llamado *reload* que sirve para volver a cargar el último módulo utilizado:
```Shell
   Prelude> :reload
   [1 of 1] Compiling Main             ( ejemplo.hs, interpreted )
   Ok, modules loaded: Main.
   *Main>
```
Sin utilizar GHCi el procedimiento para ejecutar el código sería muy similar a C o C+
+. Escribimos el código fuente en un archivo con extensión .hs y después hay que
compilarlo para generar el ejecutable. Utilizando GHCi, una vez realizada la
compilación del código que escribimos, queda listo para ser utilizado dentro del
ambiente, pudiendo realizar todas las pruebas que hagan falta para encontrar posibles
errores y corregirlo hasta que cumpla con el requerimiento definido previamente.

###Resumen de comandos útiles
|Comando             |Función                                                                       |Ejemplo               |
|--------------------|------------------------------------------------------------------------------|----------------------|
|:?, :help           |Muestra la ayuda por consola, listando los principales comandos disponibles.  |Prelude> :?           |
|:                   |Ejecuta la última sentencia que se haya empleado en el ambiente.              |Prelude> :            |
|:q, :quit, CTRL+D   |Termina la ejecución del ambiente interactivo.                                |Prelude> :q           |
|:!clear             |Limpia el historial de ejecución en pantalla.                                 |Prelude> :!clear      |
|:load               |Carga un archivo de código fuente a GHCi.                                     |Prelude> :load hola.hs|
|:reload             |Recarga el último archivo utilizado en GHCi.                                  |Prelude> :reload      |
|:show               |Muestra los módulos cargado en el ambiente.                                   |Prelude> :show        |
|↑, ↓                |Permiten navegar por el historial de ejecución en el ambiente.                |                      |
|TAB                 |Permite autocompletar los comandos.                                           |                      |
