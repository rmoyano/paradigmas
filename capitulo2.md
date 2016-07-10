#GHCi: El ambiente interactivo de Haskell. 

En éste capítulo vamos a aprender como utilizar el ambiente interactivo del lenguaje que facilita la tarea de desarrollo al programador. 
En GHCi se evalúan las expresiones de Haskell interactivamente y los programas interpretados. GHCi también tiene soporte para cargar interactivamente 
código compilado, así también como soporte para todas las extensiones del lenguaje que GHC provee. GHCi además incluye un depurador interactivo (see The GHCi Debugger).

Prelude
Al iniciar GHCi automáticamente carga Prelude que es un conjunto de librerías destinadas a proporcionar el conjunto de funcionalidades básicas para el ambiente.

##Microsoft Windows##

###Listado de comandos útiles
|Comando             |Función                                                                       |Ejemplo             |
|--------------------|------------------------------------------------------------------------------|--------------------|
|:? - :help          |Muestra la ayuda por consola, listando los principales comandos disponibles.  |                    |
|:q - :quit - CTRL+D |Termina la ejecución del ambiente interactivo.                                |                    |
|:!clear             |Limpia el historial de ejecución en pantalla.                                 |                    |
|:load               |Compila y carga el módulo en GHCi.                                            |                    |
|:reload             |Recarga el último módulo utilizado en GHCi.                                   |                    |
|:show               |Muestra los módulos cargado en el ambiente                                    |                    |

###Pasos:

1. Ir al sitio oficial del lenguaje de programación [Haskell](https://www.haskell.org "Haskell"). 
2. Buscar y hacer click en la sección [Downloads](https://www.haskell.org/downloads "Descargas").

   ![Sitio oficial del proyecto.](/images/1_haskell.png "Sitio oficial")
   
3. Haskell provee tres opciones para instalarlo. Vamos a utilizar la instalación mínima [(Minimal installers)](https://www.haskell.org/downloads#minimal) por lo que hacemos click en el enlace a esa sección.

   ![Minimal installers.](/images/2_haskell_downloads.png "Minimal installers")

4. Seleccionar el sistema operativo [Windows](https://github.com/fpco/minghc#using-the-installer):

   ![Windows.](/images/3_haskell_os.png "Windows")
                  
5. Una vez que ingresamos a la página del proyecto *MinGHC* en Github, hacemos scroll-down en la página hasta llegar a la sección *Legacy MinGHC installers*. Seleccionar y hacer click para descargar el ejecutable MinGHC, dependiendo de la arquitectura de su computadora (32 o 64 bits).

   ![Arquitectura.](/images/4_haskell_arch.png "Arquitectura")
   

##GNU/Linux

La instalación de Haskell la vamos a realizar en la distribución Debian; por lo cual en distribuciones derivadas como Ubuntu o Linux Mint el procedimiento de instalación es similar y también debería funcionar sin inconvenientes.

###Pasos:

1. Configurar las fuentes del gestor de paquetes (APT) editando el archivo sources.list:
```bash
# vi /etc/apt/sources.list
```
4. Buscar los paquetes de ghc (Glasgow Haskell Compiler): 
```bash
   # apt-cache search glasgow
   bnfc - Compiler front-end generator based on Labelled BNF
   ghc - The Glasgow Haskell Compilation system
   ghc-doc - Documentation for the Glasgow Haskell Compilation system
   ghc-dynamic - Dynamic libraries for the Glasgow Haskell Compilation system
   ghc-prof - Profiling libraries for the Glasgow Haskell Compilation system
```
6. Para verificar la instalación exitosa, abra una consola y ejecute el intérprete de Haskell:
```Shell
   $ ghci
   Prelude>
```
