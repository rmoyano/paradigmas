#Instalación de Haskell

Para poder programar en Haskell necesitamos descargar e instalar el conjunto de librerías, 
intérprete y compilador. La distribuciónn más activa es GHC (Glasgow Haskell Compiler). 
ghc es el compilador optimizado para generar rápido código nativo; ghci es el intérprete y depurador interactivo. 

##Microsoft Windows##

Pasos:

1. Ir al sitio oficial del lenguaje de programación [Haskell](https://www.haskell.org "Haskell"). 
2. Buscar y hacer click en la sección [Downloads](https://www.haskell.org/downloads "Descargas").

   ![Sitio oficial del proyecto.](/images/haskell.png "Sitio oficial")
   
3. Seleccionar Windows.

   ![Windows.](/images/haskell_download.png "Windows")
   
4. Seleccionar y hacer click para descargar el ejecutable MinGHC, dependiendo de la arquitectura de su computadora (32 o 64 bits).

   ![Arquitectura.](/images/haskell_arch.png "Arquitectura")
   
5. Guarde el instalador en su computadora.

   ![Guardar.](/images/haskell_save_file.png "Guardar")

6. Una vez finalizada la descarga, ejecutar el instalador.

7. Seleccionar el directorio a dónde se va instalar y darle aceptar. (En netbooks con escasa memoria RAM, se puede demorar varios minutos.)

8. Buscar la carpeta a donde se instaló y ejecutar ghci.exe para abrir el intérprete de Haskell.

##GNU/Linux

La instalación de Haskell la vamos a realizar en la distribución Debian; por lo cual en distribuciones derivadas como Ubuntu o Linux Mint el procedimiento de instalación es similar y también debería funcionar sin inconvenientes.

Pasos:
......

1. Configurar las fuentes del gestor de paquetes (APT) editando el archivo sources.list:

.. code-block:: console

   # vi /etc/apt/sources.list

2. Agregar alguno de los repositorios de Argentina:

.. code-block:: console

   deb http://mirrors.dcarsat.com.ar/debian/ stable main contrib non-free
   deb-src http://mirrors.dcarsat.com.ar/debian/ stable main contrib non-free

2. Verificar que se tiene conectividad con el repositorio de Debian, actualizando el índice de paquetes: 

.. code-block:: console

   # apt-get update

3. Buscar los paquetes de ghc (Glasgow Haskell Compiler): 

.. code-block:: console

   # apt-cache search glasgow
   bnfc - Compiler front-end generator based on Labelled BNF
   ghc - The Glasgow Haskell Compilation system
   ghc-doc - Documentation for the Glasgow Haskell Compilation system
   ghc-dynamic - Dynamic libraries for the Glasgow Haskell Compilation system
   ghc-prof - Profiling libraries for the Glasgow Haskell Compilation system

   
4. Instalar las librerías y respectivas dependencias:

.. code-block:: console

   # apt-get install ghc
   Leyendo lista de paquetes... Hecho
   Creando árbol de dependencias       
   Leyendo la información de estado... Hecho
   Se instalarán los siguientes paquetes extras:
       binutils cpp cpp-4.9 gcc gcc-4.9 libasan0 libasan1 libatomic1 libbsd-dev libcilkrts5
       libcloog-isl4 libffi-dev libgcc-4.8-dev libgcc-4.9-dev libgmp-dev libgmpxx4ldbl libgomp1
       libisl10 libitm1 liblsan0 libmpc3 libmpfr4 libquadmath0 libstdc++-4.8-dev libtsan0 libubsan0
   Paquetes sugeridos:
       binutils-doc cpp-doc gcc-4.9-locales gcc-multilib make autoconf automake libtool flex bison
       gdb gcc-doc gcc-4.9-multilib gcc-4.9-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg
       libasan1-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg libquadmath0-dbg
       ghc-prof ghc-doc haskell-doc llvm libgmp10-doc libmpfr-dev libstdc++-4.8-doc
   Se instalarán los siguientes paquetes NUEVOS:
       binutils cpp cpp-4.9 gcc gcc-4.9 ghc libasan0 libasan1 libatomic1 libbsd-dev libcilkrts5
       libcloog-isl4 libffi-dev libgcc-4.8-dev libgcc-4.9-dev libgmp-dev libgmpxx4ldbl libgomp1
       libisl10 libitm1 liblsan0 libmpc3 libmpfr4 libquadmath0 libstdc++-4.8-dev libtsan0 libubsan0
   0 actualizados, 27 nuevos se instalar�n, 0 para eliminar y 23 no actualizados.
   Se necesita descargar 47,1 MB de archivos.
   Se utilizarán 384 MB de espacio de disco adicional después de esta operación.
   ¿Desea continuar? [S/n]
   
5. Para verificar la instalación exitosa, abra una consola y ejecute el intérprete de Haskell:

.. code-block:: console

   $ ghci
   Prelude>
