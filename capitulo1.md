#Instalación de Haskell

Para poder programar en Haskell necesitamos descargar e instalar el conjunto de librerías, 
intérprete y compilador. La distribución más activa es GHC (Glasgow Haskell Compiler). 
*ghc* es el compilador optimizado para generar rápido código nativo; ghci es el intérprete y depurador interactivo. 

##Microsoft Windows##

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
   
6. Guarde el instalador en su computadora (Se puede demorar un par de minutos dependiendo de su velocidad de conexión a Internet):

   ![Guardar.](/images/5_save_exe.png "Guardar")

7. Una vez finalizada la descarga, ejecutar el instalador: 

   ![Instalar.](/images/6_execute_exe.png "Instalar")

8. En *Selección de componentes* (Choose components) dejar tildadas las opciones por defecto y hacer click en *Continuar* (Next):

   ![Seleccionar componentes.](/images/7_choose_components.png "Seleccionar componentes")

9. Seleccionar el directorio a dónde se va instalar y hacer click en *Instalar*. (En netbooks con escasa memoria RAM, se puede demorar varios minutos.)

   ![Path.](/images/8_choose_install_location.png "Seleccionar path")

10. Una vez que que la instalación ha culminado exitosamente, hacer click en *Cerrar* (Close).

   ![Instalación exitosa.](/images/9_installation_successful.png "Instalación exitosa")

11. Buscar la carpeta a donde se instaló y ejecutar ghci.exe para abrir el intérprete de Haskell. Dependiendo la versión de Windows puede variar la ubicación de la misma.

    + Windows XP: C:\Documents and Settings\rafael\Configuración local\Datos de programa\Programs\minghc-7.10.2-i386\ghc-7.10.2\bin

   ![Ejecutar intérprete.](/images/10_kickoff_interpreter.png "Abrir intérprete")

   Otra manera de ejecutar el ínterprete es ir al menú de *Inicio* y hacer click en *Ejecutar*. Una vez que se abra la ventana, escribir ghci y aceptar:

   ![Utilizando Ejecutar.](/images/11_kickoff_interpreter_another_way.png "Abrir intérprete")

##GNU/Linux

La instalación de Haskell la vamos a realizar en la distribución Debian; por lo cual en distribuciones derivadas como Ubuntu o Linux Mint el procedimiento de instalación es similar y también debería funcionar sin inconvenientes.

###Pasos:

1. Configurar las fuentes del gestor de paquetes (APT) editando el archivo sources.list:
```bash
# vi /etc/apt/sources.list
```
2. Agregar alguno de los repositorios de Argentina:
```bash
   deb http://mirrors.dcarsat.com.ar/debian/ stable main contrib non-free
   deb-src http://mirrors.dcarsat.com.ar/debian/ stable main contrib non-free
```
3. Actualizar el índice de paquetes para verificar que se tiene conectividad con el repositorio de Debian:
```bash
   # apt-get update
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
5. Instalar las librerías y respectivas dependencias:
```ShellSession
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
```
6. Para verificar la instalación exitosa, abra una consola y ejecute el intérprete de Haskell:
```Shell
   $ ghci
   Prelude>
```
