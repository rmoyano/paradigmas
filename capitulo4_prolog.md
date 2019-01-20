#Instalación de SWI-Prolog

Para poder iniciarse en la programación lógica, proponemos que tanto su estudio como los ejercicios que se 
consideren necesarios sean realizados en las computadoras o notebooks de los propios alumnos. Por tal motivo, se 
ha de descargar e instalar un ambiente libre e integral junto con el conjunto de librerías y compilador 
correspondiente de Prolog. Dentro de las opciones disponibles en Internet, la cátedra ha elegido *SWI-Prolog* por 
ser uno de los proyectos dentro del software libre más activo y documentado dentro de la comunidad de programación 
a nivel mundial. El código del proyecto se encuentra alojado en [Github](https://www.github.com/SWI-Prolog "SWI-Prolog").



##Microsoft Windows##

###Pasos:

1. Ir al sitio oficial del lenguaje de programación [SWI-Prolog](http://www.swi-prolog.org/ "SWI-Prolog"). 
2. Buscar y hacer click en la sección [Download](http://www.swi-prolog.org/Download.html "Descargas") y luego la subsección SWI-Prolog:

   ![Sitio oficial del proyecto.](/images/prolog/0_project_pagebb.png "Sitio oficial")
   
3. SWI-Prolog provee tres opciones: Estable, desarrollo y versiones diarias. Vamos a elegir la versión estable, por lo que hacemos click en el enlace a esa
sección:

   ![Versión estable.](/images/prolog/1_select_installerbb.png "Versión estable.")

4. Seleccionar y hacer click para descargar el instalador de acuerdo a la arquitectura de su computadora (32 o 64 bits) [64 bits](http://www.swi-prolog.org/download/stable/bin/swipl-8.0.0-1.x64.exe):

   ![Windows 64 bits.](/images/prolog/2_select_architecturebb.png "Windows 64 bits")
                  
5. Guarde el instalador en su computadora (Se puede demorar un par de minutos dependiendo de su velocidad de conexión a Internet):

   ![Guardar.](/images/prolog/3_save_exe_b.png "Guardar")

6. Una vez finalizada la descarga, ejecutar el instalador y hacer click en *Acepto* el acuerdo de licencia (I agree): 

   ![Instalar.](/images/prolog/4_ejecutar_exebb.png "Instalar")

7. Seleccionar el directorio a dónde se va instalar y hacer click en *Siguiente* (Next): 

   ![Path.](/images/prolog/5_select_folder.png "Seleccionar path")

8. Seleccionar la extensión para el código fuente Prolog (Por defecto es .pl ) y hacer click en *Instalar* (Install):

   ![Selección de extensión.](/images/prolog/6_select_file_extension.png "Start menu")

9. Una vez que que la instalación ha culminado exitosamente, hacer click en Finalizado (Finished):

   ![Instalación exitosa.](/images/prolog/7_installation_completed.png "Instalación exitosa")

10. Ir al Menú de Inicio, buscar la carpeta SWI-Prolog y hacer click en *Prolog* para abrir el ambiente interactivo *swipl*:
   
   ![swipl.](/images/prolog/8_start_swiplbb.png "Ejecutar swipl")
   
   Otra manera de ejecutar el ambiente es ir al *Menú de Inicio*, hacer click en *Buscar*. Una vez que se abra la ventana, 
   escribir *Prolog* y hacer click en el logo del programa:
   
   ![swipl.](/images/prolog/9_ejecutar_directo_swiplbb.png "Ejecutar directo swipl")


##GNU/Linux

Para esta plataforma, la instalación de SWI-Prolog se realizará en la distribución Debian que dispone
 del gestor de instalación APT, el cual también es utilizado en distribuciones derivadas como Ubuntu, 
 Trisquel, Linux Mint, etc. Para otras distribuciones, el procedimiento de instalación puede ser similar pero se
emplean otros gestores de instalación como YUM (Red Hat y Derivados) o YAST (Suse y derivados).

###Pasos:

1. Configurar las fuentes del gestor de paquetes (APT) editando el archivo *sources.list*:
```bash
# vi /etc/apt/sources.list
```
2. Agregar alguno de los repositorios disponibles en Argentina, yo elegí ARSAT:
```bash
   deb http://mirrors.dcarsat.com.ar/debian/ stable main contrib non-free
   deb-src http://mirrors.dcarsat.com.ar/debian/ stable main contrib non-free
```
3. Actualizar el índice de paquetes para verificar que se tiene conectividad con el repositorio de Debian:
```bash
   # apt-get update
```
4. Buscar los paquetes de SWI-Prolog: 
```bash
   # apt search swi-prolog
   swi-prolog/stable,now 7.2.3+dfsg-6 amd64 
   Intérprete de ISO/Edinburgh Prolog
   
   swi-prolog-doc/stable 5.6.59-2 all
     Documentación del intérprete SWI-Prolog y XPCE
   
   swi-prolog-java/stable 7.2.3+dfsg-6 amd64
     Bidirectional interface between SWI-Prolog and Java
   
   swi-prolog-nox/stable,now 7.2.3+dfsg-6 amd64 
   ISO/Edinburgh-style Prolog interpreter (without X support)
   
   swi-prolog-odbc/stable 7.2.3+dfsg-6 amd64
   ODBC library for SWI-Prolog
   
   swi-prolog-x/stable,now 7.2.3+dfsg-6 amd64 
   User interface library for SWI-Prolog (with X support)
```
5. Instalar las librerías y sus respectivas dependencias:
```ShellSession
   # apt-get install swi-prolog
   Leyendo lista de paquetes... Hecho
   Creando árbol de dependencias       
   Leyendo la información de estado... Hecho
   Se instalarán los siguientes paquetes adicionales:
     libncursesw5-dev libossp-uuid16 libreadline-dev swi-prolog-nox swi-prolog-x
   Paquetes sugeridos:
     ncurses-doc uuid readline-doc prolog-el
   Se instalarán los siguientes paquetes NUEVOS:
     libncursesw5-dev libossp-uuid16 libreadline-dev swi-prolog swi-prolog-nox swi-prolog-x
   0 actualizados, 6 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
   Se necesita descargar 0 B/5.413 kB de archivos.
   Se utilizarán 30,4 MB de espacio de disco adicional después de esta operación.
```
6. Para verificar la instalación exitosa, abra una terminal y ejecute el comando para abrir el ambiente interactivo de Haskell:
```Shell
   $ swipl
   Welcome to SWI-Prolog (Multi-threaded, 64 bits, Version 7.2.3) Copyright (c) 1990-2015 University of Amsterdam, VU Amsterdam SWI-Prolog comes with ABSOLUTELY NO WARRANTY. This is free software, and you are welcome to redistribute it under certain conditions.
   Please visit http://www.swi-prolog.org for details.
   For help, use ?- help(Topic). or ?- apropos(Word).
   ?- 
```
