#Instalación de Haskell

Para poder iniciarse en la programación en Haskell, proponemos que su estudio como las pruebas que 
se consideren necesarias, se realicen en los equipos particulares. Por lo tanto se hace necesario 
descargar e instalar el conjunto de librerías, ambiente interactivo y compilador correspondiente.
Dentro de los proyetos de software libre disponibles, la cátedra ha elegido una de las distribuciones
más activas de la comunidad de programación llamada Glasgow Haskell Compiler (GHC). 
Mas precisamente, al hacer referencia a *GHC*, debemos relacionarlo con un compilador optimizado para 
generar código nativo y *GHCi*, hace referencia al ambiente y depurador interactivo.

##Microsoft Windows##

###Pasos:

1. Ir al sitio oficial del lenguaje de programación [Haskell](https://www.haskell.org "Haskell"). 
2. Buscar y hacer click en la sección [Downloads](https://www.haskell.org/downloads "Descargas"):

   ![Sitio oficial del proyecto.](/images/2_haskell.png "Sitio oficial")
   
3. Haskell provee tres opciones para instalarlo. Vamos a utilizar la Plataforma Haskell [(Haskell Platform)](https://www.haskell.org/downloads#platform), que es la recomendada por el proyecto. La plataforma incluye el Stack Haskell y lo instala como un componente independiente. A continuación, hacemos click en el enlace a esa sección:

   ![Haskell Platform.](/images/3_haskell_downloads.png "Haskell Platform.")

4. Seleccionar el sistema operativo [Windows](https://www.haskell.org/platform/windows.html):

   ![Windows.](/images/4_haskell_os.png "Windows")
                  
5. Una vez que ingresamos a la página de *Windows*, hacemos scroll-down en la página para seleccionar la descarga. Elegir el ejecutable dependiendo de la arquitectura de su computadora (32 o 64 bits) y se recomienda la versión core, ya que la versión full incluye librerías que no vamos a llegar a cubrir en el curso:

   ![Arquitectura.](/images/5_haskell_arch.png "Arquitectura")
   
6. Guarde el instalador en su computadora (Se puede demorar un par de minutos dependiendo de su velocidad de conexión a Internet):

   ![Guardar.](/images/6_save_exe.png "Guardar")

7. Una vez finalizada la descarga, ejecutar el instalador: 

   ![Instalar.](/images/7_execute_exe.png "Instalar")

8. En *Acuerdo de Licenciamiento* (License Agreement) hay que *Aceptar* (I agree) los términos de las licencias: 

   ![Seleccionar componentes.](/images/8_license.png "Licencia.")

9. Seleccionar el directorio a dónde se va instalar y hacer click en *Siguiente* (Next): 

   ![Path.](/images/9_choose_install_location.png "Seleccionar path")

10. En *Selección de componentes* (Choose components) dejar tildadas las opciones por defecto y hacer click en *Continuar* (Next):

   ![Seleccionar componentes.](/images/10_choose_components.png "Seleccionar componentes")

11. En *Selección de directorio de inicio* (Start menu folder) utilizar la opción por defecto y hacer click en *Instalar* (Install):

   ![Selección de directorio de inicio.](/images/11_start_menu.png "Start menu")

12. Elegir el directorio de instalación del *Stack Haskell* (Haskell Stack setup) y hacer click en *Siguiente* (Next):

   ![Directorio de instalación.](/images/12_haskell_stack_setup.png "Haskell Stack setup")

13. En *Selección de componentes* (Choose components) dejar tildadas las opciones por defecto y hacer click en *Instalar* (Install):

   ![Seleccionar componentes.](/images/13_haskell_stack_components.png "Seleccionar componentes")

14. Una vez que que la instalación del Stack Haskell ha culminado exitosamente, hacer click en *Cerrar* (Close):

   ![Instalación exitosa.](/images/14_stack_successful_installation.png "Instalación exitosa")

15. El resto de los componentes de la plataforma continuarán instalándose:

   ![Progreso de instalación.](/images/15_platform_progress.png "Progreso de instalación")

16. Una vez que que la instalación ha culminado exitosamente, hacer click en *Siguiente* (Next):

   ![Instalación exitosa.](/images/16_successful_installation.png "Instalación exitosa")

17. Para cerrar el asistente de instalación, hacer click en *Terminar* (Finish):

   ![Cerrar asistente.](/images/17_close_installer.png "Cerrar asistente de instalación")

18. Para ejecutar el ambiente interactivo GHCI vamos al menú *Inicio*, click en *Todos los programas*, seleccionamos *Haskell Platform* y hacemos click en *WinGHCi*: 

   ![Ejecutar GHCi.](/images/18_kickoff_winghci.png "Abrir GHCi")

    Otra forma es buscar la carpeta donde se instaló y ejecutar winghci.exe para abrir el ambiente interactivo de Haskell. La ubicación puede variar dependiendo de la versión de Windows:

    + *Windows XP*: C:\Archivos de Programa\Haskell Platform\8.0.2\winghci.exe


   ![Ejecutar GHCi.](/images/18b_winghci_exe.png "Abrir GHCi")

19. Finalmente, *WinGHCi* se abrirá para poder empezar a probar Haskell:

   ![WinGHCi.](/images/19_winghci.png "Abrir GHCi")


##GNU/Linux
Para esta plataforma, la instalación de Haskell se realizará en la distribución Debian
que dispone del gestor de paquetes APT. En distribuciones derivadas como Ubuntu, 
Trisquel, Linux Mint, etc. el procedimiento de instalación es similar y debería culminar sin inconvenientes.
Para otras distribuciones como Centos, Fedora, Mageia, etc. el procedimiento de instalación puede ser similar
pero se ajusta a los propios gestores de paquetes. 

###Pasos:

1. Configurar las fuentes del gestor de paquetes (APT) editando el archivo sources.list:
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
4. Buscar los paquetes de GHC (Glasgow Haskell Compiler): 
```bash
   # apt-cache search glasgow
   bnfc - Compiler front-end generator based on Labelled BNF
   ghc - The Glasgow Haskell Compilation system
   ghc-doc - Documentation for the Glasgow Haskell Compilation system
   ghc-dynamic - Dynamic libraries for the Glasgow Haskell Compilation system
   ghc-prof - Profiling libraries for the Glasgow Haskell Compilation system
```
5. Instalar las librerías y sus respectivas dependencias:
```ShellSession
   # apt-get install ghc
   Leyendo lista de paquetes... Hecho
   Creando árbol de dependencias       
   Leyendo la información de estado... Hecho
   Se instalarán los siguientes paquetes extras:
       libbsd-dev libffi-dev libgmp-dev libgmpxx4ldbl
   Paquetes sugeridos:
       ghc-prof ghc-doc haskell-doc llvm libgmp10-doc libmpfr-dev
   Se instalarán los siguientes paquetes NUEVOS:
       ghc libbsd-dev libffi-dev libgmp-dev libgmpxx4ldbl
   0 actualizados, 5 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
   Se necesita descargar 26,3 MB de archivos.
   Se utilizarán 295 MB de espacio de disco adicional después de esta operación.
   ¿Desea continuar? [S/n]
```
6. Para verificar la instalación exitosa, abra una terminal y ejecute el comando para abrir el ambiente interactivo de Haskell:
```Shell
   $ ghci
   GHCi, version 7.6.3: http://www.haskell.org/ghc/  :? for help
   Loading package ghc-prim ... linking ... done.
   Loading package integer-gmp ... linking ... done.
   Loading package base ... linking ... done.
   Prelude>
```
