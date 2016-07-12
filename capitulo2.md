#GHCi: El ambiente interactivo de Haskell. 

En éste capítulo vamos a aprender como utilizar el ambiente interactivo del lenguaje, que facilita la tarea de desarrollo al programador. 
En GHCi se evalúan las expresiones de Haskell interactivamente y los programas interpretados. GHCi también tiene soporte para cargar interactivamente 
código compilado, así como soporte para todas las extensiones del lenguaje que GHC provee. GHCi además incluye un depurador interactivo (see The GHCi Debugger).

## Manejo del ambiente
Al ejecutar GHCi, va mostrando por la terminal:
1. La versión del software, es 7.6.3 para nuestro ejemplo. 
2. Enlace a la página del proyecto.
3. :? Comando para mostrar la ayuda.
4. Los paquetes que carga (ghc-prim, integer-gmp, base.)
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
Entre las diversas funciones que *Prelude* provee están los operadores matemáticos (Suma, resta, multiplicación, división, potencia, etc.) que permiten utilizar el ambiente como una calculadora: 

```Shell
   Prelude> 2+2
   4
   Prelude> 2*3
   6
   Prelude> 2**4
   16.0
```
También se puede utilizar funciones como redondeo a enteros (Superior en éste caso):
```Shell
  Prelude> ceiling 10.4
  11
  Prelude> ceiling 10.2
  11
  Prelude> ceiling 8.9
  9
```
Otro ejemplo es la función par (Devuelve verdadero o falso):
```Shell
  Prelude> even 10
  True
  Prelude> even 11
  False
```

GHCi muestra un cursor
-Utilizando los cursores para arriba(↑) o abajo (↓) permiten navegar por el historial de ejecución.
Ejemplo apretando el cursor para arriba:
```Shell
   Prelude> 2**4
   Prelude> 2*3
   Prelude> 2+2
```
- La tecla TAB nos permite autocompletar los comandos y también muestra las opciones disponibles para terminar de completar los caracteres que fuimos presionamos.
```Shell
  Prelude> a
  abs         acos        acosh       all         and         any         appendFile  asTypeOf    asin        asinh       atan        atan2       atanh
  Prelude> as
  asTypeOf  asin      asinh
```

##Manejo
###Listado de comandos útiles
|Comando             |Función                                                                       |Ejemplo               |
|--------------------|------------------------------------------------------------------------------|----------------------|
|:? :help            |Muestra la ayuda por consola, listando los principales comandos disponibles.  |Prelude> :?           |
|:q :quit CTRL+D     |Termina la ejecución del ambiente interactivo.                                |Prelude> :q           |
|:!clear             |Limpia el historial de ejecución en pantalla.                                 |Prelude> :!clear      |
|:load               |Carga un archivo de código fuente a GHCi.                                     |Prelude> :load hola.hs|
|:reload             |Recarga el último archivo utilizado en GHCi.                                  |Prelude> :reload      |
|:show               |Muestra los módulos cargado en el ambiente.                                   |Prelude> :show        |
|↑ ↓                 |Permiten navegar por el historial de ejecución en el ambiente.                |                      |
|TAB                 |nos permite autocompletar los comandos.                                       |                      |

###Ejecución:
:help
```Shell
   Prelude> :?
   Prelude> 
```
1. Ir al sitio oficial del lenguaje de programación [Haskell](https://www.haskell.org "Haskell"). 
2. *Buscar* y hacer click en la sección [Downloads](https://www.haskell.org/downloads "Descargas").

   ![Sitio oficial del proyecto.](/images/1_haskell.png "Sitio oficial")
