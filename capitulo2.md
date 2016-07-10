#GHCi: El ambiente interactivo de Haskell. 

En éste capítulo vamos a aprender como utilizar el ambiente interactivo del lenguaje que facilita la tarea de desarrollo al programador. 
En GHCi se evalúan las expresiones de Haskell interactivamente y los programas interpretados. GHCi también tiene soporte para cargar interactivamente 
código compilado, así también como soporte para todas las extensiones del lenguaje que GHC provee. GHCi además incluye un depurador interactivo (see The GHCi Debugger).

##Prelude
Al ejecutar GHCi automáticamente realiza la carga de Prelude, que es un conjunto de librerías destinadas a proporcionar las funcionalidades básicas para el ambiente.
```Shell
   rafa@pc:~/home/unlar$ ghci
   GHCi, version 7.6.3: http://www.haskell.org/ghc/  :? for help
   Loading package ghc-prim ... linking ... done.
   Loading package integer-gmp ... linking ... done.
   Loading package base ... linking ... done.
   Prelude> 
```
###Built-in functions
Entre las diversas funciones que provee *Prelude* permite utilizar el ambiente como una calculadora, empleando los diferentes operadores aritméticos como suma, resta,
multiplicación, división, potencia, etc.:

```Shell
   Prelude> 2+2
   4
   Prelude> 2*3
   6
   Prelude> 2**4
   16.0
```
##Manejo
###Listado de comandos útiles
|Comando             |Función                                                                       |Ejemplo             |
|--------------------|------------------------------------------------------------------------------|--------------------|
|:? - :help          |Muestra la ayuda por consola, listando los principales comandos disponibles.  |Prelude> :?         |
|:q - :quit - CTRL+D |Termina la ejecución del ambiente interactivo.                                |Prelude> :q         |
|:!clear             |Limpia el historial de ejecución en pantalla.                                 |Prelude> :!clear    |
|:load               |Compila y carga el módulo en GHCi.                                            |Prelude> :load      |
|:reload             |Recarga el último módulo utilizado en GHCi.                                   |Prelude> :reload    |
|:show               |Muestra los módulos cargado en el ambiente.                                   |Prelude> :show      |

###Ejecución:
:help
```Shell
   Prelude> :?
   Prelude> 
```
1. Ir al sitio oficial del lenguaje de programación [Haskell](https://www.haskell.org "Haskell"). 
2. *Buscar* y hacer click en la sección [Downloads](https://www.haskell.org/downloads "Descargas").

   ![Sitio oficial del proyecto.](/images/1_haskell.png "Sitio oficial")
