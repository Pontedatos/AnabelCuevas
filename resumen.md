# Resumen de todo lo aprendido en Periodismo de Datos

A continuación se ofrece un resumen de los principales contenidos aprendidos en la asignatura Periodismo de Datos. 

## Instalación de un programa de emulación de la terminal

El programa que emula a la terminal con el que trabajé primero fue **WSL**, la terminal de Linux dentro de Windows. Según la [página de Microsoft](https://docs.microsoft.com/es-es/windows/wsl/about), WSL es un subsistema de Windows para Linux que “permite a los desarrolladores ejecutar un entorno de GNU/Linux, incluida la mayoría de herramientas de línea de comandos, utilidades y aplicaciones, directamente en Windows, sin modificar y sin la sobrecarga de una máquina virtual tradicional o una configuración de arranque dual”.

A continuación, pasé a usar **Ubuntu**, un sistema operativo basado en Linux. La [Wikipedia](https://es.wikipedia.org/wiki/Ubuntu) asegura que “es una distribución Linux basada en Debian GNU/Linux, que incluye principalmente software libre y de código abierto”.

Sin embargo, más adelante, por recomendación del profesor comenzamos a usar **Cygwin** de manera generalizada en toda la clase. Según su [página web](https://www.cygwin.com/), Cygwin es “una gran colección de herramientas GNU y de código abierto que brindan una funcionalidad similar a una distribución de Linux en Windows”.

### Instalación de Ubuntu

La instalación de Ubuntu la realizamos a través de la PoweShell de Windows, la terminar de Microsoft. Para ello, es necesario que seamos administradores, y a continuación ejecutar `wsl --install -d Ubuntu`. Una vez reiniciado el ordenador, ya es posible ejecutar Ubuntu. 

### Instalación de Cygwin

Para instalar esta última terminal, solo fue necesario acudir a su [página web](http://cygwin.com/) e instalar el programa. Esto es necesario porque no se trata de una herramienta propia de Microsoft. Una vez ejecutado el instalador, tuvimos que configurar algunos paquetes: `curl`, `wget`, `certificates`, `lynx` `ca-certificates-letsencrypt` y `opennsl`. 

## Configuración del programa

El propósito de instalar estos programas de emulación de la terminal ha sido durante todo el curso aprender a manejarlos. Para poder movernos por la terminal con mayor facilidad, establecimos un alias (para no tener que escribir la ruta de la carpeta de Periodismo de Datos completa cada vez que nos hacía falta). 

En primer lugar es necesario escribir `echo $HOME` para que el programa nos diga nuestra carpeta principal del ordenador. Nos muestra la variable de entorno de `HOME`. Una vez que nos hemos movido hasta la carpeta donde queremos crear el alias (mediante el comando `cd`) y tenemos localizada la ruta, definimos la variable micasa mediante `alias` . También es necesario editar el archivo de configuración de Bash, que se encuentra en nuestra “HOME”: `$HOME/.bashrc`. 

`echo “alias micasa=“cd ‘/mnt/c/Users/anabe/Desktop/periodismodatos’” >>$HOME/.bashrc`

Mediante `echo` enviaremos el archivo al final de `.bashrc` (empleando `>>`). 

## Configuración de un programa de edición de texto

Como programa de edición de texto empleamos `nano`. La configuración que hicimos de este programa contemplaba dos aspectos distintos. En primer lugar, buscábamos que las líneas se ajustaran al tamaño de la pantalla, para así hacer más fácil la lectura de los textos. Por otro lado, también numeramos las líneas. Para hacer estas dos cosas, editamos el archivo de configuración de nano, al que accedemos mediante `nano $HOME/.nanorc`. 

En el archivo de configuración escribimos lo siguiente:

`## Esto lo hago para ajustar el texto a pantalla`
´set softwrap´
`## Esto numera las líneas`
`set linenumbers` 

Los `#` permiten escribir comentarios sin que estos afecten al archivo, es decir, son para orientar al propio usuario. 

- Caso de Cygwin 

Cuando cambiamos a Cygwin tuvimos que repetir esta operación, ya que no poseíamos `nano` en este nuevo emulador de la terminal. El proceso fue distinto, ya que primero era necesario establecer la home en Windows (algo que este programa no posee por defecto). Para ello hicimos: En primer lugar instalamos nano (para poder modificar los archivos de configuración): `apt-cyg install nano`, después nos dirigimos al archivo de configuración, al que accedimos mediante `nano /etc/nsswitch.conf`. Al final de este archivo escribimos `db_home: windows`. De esta manera fijamos la home (en mi caso) en `/cygdrive/c/Users/anabe`. 

A continuación editamos el archivo `nano .nanorc`. Una vez que tuvimos el nano abierto, con `Control W` pusimos `linenumbers` y borramos el `#` y el espacio que tenía delante.  Después hicimos lo mismo con `softwrap`. Lo guardamos medianet `Control O`. 

## Configuración y funcionamiento de un gestor de paquetes/programas del emulador de la terminal

Como explica [Wikipedia](https://es.wikipedia.org/wiki/Sistema_de_gesti%C3%B3n_de_paquetes), un sistema de gestión de paquetes o gestor de paquetes es un conjunto de herramientas que “sirven para automatizar el proceso de instalación, actualización, configuración y eliminación de paquetes de software”. APT (Advanced Packaging Tool) es el programa de gestión de paquetes con el que nos hemos familiarizado este curso. Según [Wikipedia](https://es.wikipedia.org/wiki/Advanced_Packaging_Tool), APT simplifica “la instalación y eliminación de programas en los sistemas GNU/Linux”. 

En el caso de Ubuntu es `apt`, mientras que Cygwin tiene `apt-cyg`. Para instalar `apt-cyg` nos basamos en una página que proporciona [GitHub](https://github.com/transcode-open/apt-cyg), de donde copiamos varias líneas:

`lynx -source rawgit.com/transcode-open/apt-cyg/master/apt-cyg > apt-cyg`

A continuación instalamos la apt: `install apt-cyg /bin`

Como ya se ha comentado, esta apt ya nos permitió instalar nano (`apt-cyg install nano`).

## Versión del lenguaje de SHELL utilizado

Shell, como hemos visto en esta asignatura, es el idioma de la terminal (dentro está BASH y CSH: Windows y Mac respectivamente). En el caso de no conocer el lenguaje Shell que se está empleando, se puede escribir en la terminal la variable de entorno `$0`(mediante `echo $0`) para que nos indique el lenguaje. En ambos casos (en Ubuntu y en Cygwin) el lenguaje usado es `bash`. 

## Valor de la variable de entorno PATH

Según la [página de Microsoft](https://support.microsoft.com/es-es/topic/c%C3%B3mo-administrar-variables-de-entorno-en-windows-xp-5bf6725b-655e-151c-0b55-9a8c9c7f747d), una variable de entorno es una cadena que contiene información acerca del entorno para el sistema y el usuario que ha iniciado sesión en ese momento. Las variables de entorno empiezan por el símbolo `$` (que no se debe confundir con el que aparece al principio de la línea en Cygwin). 

Un ejemplo de variable de entorno es `$HOME`, que indica la ruta de nuestro usuario. Otro ejemplo es `$PATH`,  que muestra las rutas de los programas instalados que puede ejecutar la terminal. 
Para conocer estas variables necesitamos ayudarnos de `echo`, de manera que pondríamos: `echo $PATH` o `echo $HOME`. Además, para conocer todas las variables de entorno podemos emplear el comando `env`. 

## Comandos utilizados 

- `cat` → comando que se usa para concatenar (unir o enlazar) dos o más cosas, pero también lo hemos usado para previsualizar, por ejemplo ponemos `cat README.md` para previsualizar este archivo
- `cd` → sirve para cambiar el directorio, pero también para cambiar de sitio un archivo 
- `cd- ` → te lleva a home
- `cd -` → te lleva al anterior sitio donde estabas
- `cp` → es un comando que sirve para copiar un archivo o carpeta a otra. Ejemplo: `cp nombre de la carpeta/nombre del archivo.md  carpeta a donde lo quieres mover/.`
- `curl [enlace]` → comando que descarga un archivo o contenido de una web. Es igual que `wget` pero con más opciones
- `echo` → es un comando que sirve para que la terminal nos devuelva un texto. Por ejemplo si ponemos `echo “hola mundo”`, la terminal nos devuelve `hola mundo`. También se emplea para conocer variables de entorno (como `$PATH` o `$HOME`)
- `env` → este comando viene de *environment*. Sirve para mostrarte las variables de entorno
- `git init` →  este comando hace que la carpeta dentro de la cual lo ejecutes tenga las mismas “propiedades” que una carpeta de GitHub 
- `git clone http://….` → clona en la carpeta en la que estés el repositorio de GitHub que indiques en el enlace
- `git status` → comando que te permite saber qué diferencias hay entre la carpeta en la que te encuentras y el repositorio que tienes en GitHub (tienes que tenerlo enlazado previamente): modificaciones, elementos que has eliminado o añadido…
- `Git add .` → mediante este comando añades todos los cambios realizados en la carpeta enlazada al repositorio de GitHub. Si sólo quisieras añadir un archivo en concreto se emplearía: `git add “nombre-archivo”`
- `git commit -m “nombre-del-cambio-realizado”` → sirve para nombrar el cambio que vas a realizar en tu repositorio de GitHub
- `git pull` → prepara los archivos para ser subidos, en caso de que fuera a haber algún problema con la subida de cambios, este comando te lo indica
- `git push` → paso final para guardar los cambios en GitHub. Te pide el nombre de usuario y el token para realizarlos
- `grep` → comando con el que puedes buscar palabras dentro de archivos de texto desde la terminal. Por ejemplo, si queremos saber dónde está escrito “micasa” pero no sabemos en qué carpeta puede estar, lo podemos usar
- `lolcat` → comando que agrega color arcoiris al texto
- `ls` →es el comando “listar”, te dice qué tienes. Por ejemplo, qué tienes en una carpeta. `ls -l` es lístame con más detalle,  `ls -a`  lista los archivos y directorios ocultos y `ls -la`  lista los archivos y directorios ocultos con más detalle
- `mnt` → WSL se relaciona con Windows 
- `mv` es para mover las cosas de un sitio a otro (en los argumentos de este comando es donde tenemos que indicar el destino a donde queremos mover nuestra cosa). Este comando también se puede usar para cambiar de nombre un archivo o carpeta. Ejemplos:
`mv capeta/ nuevo destino/.` 
`mv carpeta/ carpeta` 
- `mkdir` → es el comando que crea nuevas carpetas
- `man` →  con este comando se muestra información del comando que se especifique. Viene de “manual”. Por ejemplo, poniendo `man ls` nos dice qué hace `ls`. El manueal lo abre con el programa `man`, que es como una biblioteca, lo abre con un paginador (que es un lector de texto). Los paginadores son dos: `more` / `less` 
- `nano` →  es el comando que sirve para editar archivos `.md`, de texto
- `pwd` → este comando indica “donde estamos”, es decir, nos indica la ruta de donde nos encontremos en la terminal. Por ejemplo: `/mnt/c/Users/anabe/Desktop/periodismodatos`
- `rm` → sirve para borrar (si no funciona, podríamos probar con `rm -r`)
- `touch` →  crea un archivo en blanco 
- `whoami` → es un comando que te dice quién eres (en mi caso, “anabe”)
- `wget [enlace]` → comando que descarga un archivo o contenido de una web. Se debe incluir el enlace de lo que nos queramos descargar
- `&&` →sirve para unir comandos, es decir, hacer dos comandos de una vez. Ejemplo: `mkdir __ && cd __`
- `../` → es para ir al repositorio anterior
- Si ponemos `>` envía la salida a un archivo, pero pisa el archivo existente, lo reescribe entero
- Si ponemos `>>`, lo sitúa al final del archivo, en el caso de que tenga líneas escritas anteriormente
- Si ponemos `|` , envía la salida a un comando
