# Directorios del sistema

/: El directorio root, donde todo comienza.

/bin: Contiene binarios (programas) que deben estar presentes para que el sistema bootee y arranque.

/boot: Contiene el kernel de Linux, la imagen inicial del disco RAM (para los drivers necesarios en el boot time), y el boot loader. Archivos de interés:
- /boot/grub/grub.conf o menu.lst, el cual es usado para configurar el boot loader.
- /boot/vmlinuz, el kernel de Linux.

/dev:  Este es un directorio especial que contiene los nodos de dispositivos. “Todo es un archivo” es la filosofía de los sistemas tipo UNIX que también aplica a los dispositivos, Aquí es donde donde el kernel mantiene una lista de todos los dispositivos que entiende o reconoce.

/etc: Este directorio contiene todos los archivos de configuración general del sistema. También contiene una colección de shell scripts que inician cada uno de los servicios del sistema en el boot time. Archivos de interés (todos son interesantes, pero aquí unos recomendados):
- /etc/crontab: un archivo que define cuándo han de ejecutarse o correr las tareas programadas o los trabajos automatizados.
- /etc/fstab: tabla de los dispositivos de almacenamiento y sus puntos de montaje asociados.
- /etc/passwd: lista de las cuentas de usuario.

/home: En configuraciones normales, a cada usuario le es dado un directorio en /home. Los usuarios ordinarios pueden escribir archivos sólamente en sus directorios de home. Esta limitación protege el sistema de la actividad de usuarios inexpertos.

/lib: Contiene librerías de archivos usadas por los programas del núcleo (core) del sistema. Estas son similares a los DLL en Windows.

/last+found: Cada partición o dispositivo formateado que usa un sistema de archivos, como el ext3, tendrá este directorio. Es usado en el caso de una recuperación parcial de un evento de corrupción de un sistema de archivos.

/media: En los modernos sistemas de linux el directorio /media contiene el punto de montaje para los dispositivos removibles como los discos USB, CD-ROM, etc. que son montados automáticamente en la inserción.

/mnt: En los viejos sistemas, el directorio /mnt contenía los puntos de montaje para los dispositivos removibles que han sido montados manualmente.

/opt: Este directorio es usado para instalar software “opcional”. Es usado principalmente para todos los productos de software comercial que pueden ser instalados en tu sistema.

/proc: Este directorio es especial; no es un sistema de archivos real en el sentido de los sentidos de los archivos almacenados en tu disco duro. Más bien es un sistema de archivos virtual mantenido por el kernel de Linux. Los “archivos” que contiene son rendijas o mirillas hacia el interior del kernel mismo. Los archivos son leíbles y te darán una instantánea o una imágen de cómo el kernel ve tu computadora.

/root: Este es el directorio home para la cuenta root.

/sbin: Este directorio contiene los binarios del “sistema”. Estos son programas que realizan tareas vitales para el sistema que tu generalmente sirven para el superusuario.

/tmp: Este directorio está destinado a ser un almacén temporal de archivos transitorios creados por varios programas. Algunas configuraciones causan que este directorio sea vaciado cada vez que el sistema es reiniciado.

/usr: Es probablemente el árbol de directorios más extensos en el sistema Linux. Contiene todos los programas y soporta los archivos usados por usuarios regulares.

/usr/bin: Contiene los programas ejecutables instalados por tu distribución de Linux. No es extraño para este directorio albergar miles de programas.

/usr/lib: Librerías compartidas por los programas en /usr/bin.

/usr/local: Aquí se alojan los programas que no son instalados con la distribución pero son instalados para ser usados por todo el sistema. Programas compilados desde el código fuente se encuentran normalmente en /etc/local/bin. En una instalación nueva de Linux, este árbol existe, pero estará vacía hasta que el administrador del sistema ponga algo en él.

/usr/sbin: Contiene más programas de administración del sistema.

/usr/share: Contiene todos los datos compartidos usados por los programas en /usr/bin. Esto incluye cosas como archivos de configuración default, iconos,  fondos de pantalla, archivos de sonido, etc.

/usr/share/doc: La mayoría de los paquetes instalados en el sistema incluirán algún tipo de documentación, y en este directorio encontramos la documentación organizada por paquetes.

/var: Con la excepción de /tmp y /home, los directorios vistos anteriormente, permanecen relativamente estáticos; es decir, su contenido no cambia. El árbol de directorios /var es donde se almacenan los datos que probablemente cambiarán. Diferentes bases de datos, archivos en cola, usuarios de correo, etc, están ubicados aquí.

/var/log: contiene archivos de log, archivos que contienen la actividad de varios sistemas. Estos son muy importantes y deberían ser monitoreados de tanto en tanto. Uno de los más útiles es /var/log/messages o /var/log/syslog (a veces cambia según la distro). Por razones de seguridad, en algunos sistemas, es necesario ser superusuario para ver los archivos log. 

agregar directorios a su ruta con el siguiente comando, donde directorio es el nombre del directorio que desea agregar:

[me @ linuxbox me] $ export PATH = $ PATH: directorio

# Abrir archivo desde terminal

- xdg-open $file: abre el archivo con el programa gráfico adecuado. Ejemplos:

- xdg-open http://askubuntu.com/ #abre el navegador web por default

- xdg-open mailto:someone@somewhere.com #abre el procesador de texto del programa de email por default, con el correo en el campo “para”.

Si lo que deseas es visualizar videos en una terminal virtual, sin Xorg, puedes usar mplayer con directfb, fbdev, fbdev2, sdl (con el frame buffer back-end) o svga como salida de video, ejecutando:

- mplayer -vo fbdev2 file.mpg

Para imágenes fijas, puedes instalar el paquete fbi y usarlo para mostrar imágenes en un framebuffer:

- fbi imageFile.jpg

# Identificación de comandos

- type: Muestra a qué tipo pertenece el comando: programa ejecutable, comando interno de la shell (shell builtin), una función de la shell, o un alias. 

# Documentación de comandos

- help [comando]: Muestra la documentación principalmente de comandos shell builtin, aunque también puede funcionar para otros. Cuando aparecen corchetes cuadrados significa que son elementos opcionales, y una barra vertical indica mutua exclusión entre los elementos.
- [comando] --help: Muestra la documentación principalmente de programas ejecutables.
man: Despliega el manual del programa que se encuentra dividido en sencciones: man sección términoAbuscar.
- apropos [terminoBuscado]: Permite buscar un determinado término en la lista de páginas de manuales.
- man -k === apropos.
- whatis: Muestra una breve descripción del comando.
- info: Es similar a man pero muy parecida a una página web por sus hipervínculos.
    - ?: Muestra la ayuda del comando.
    - PAGE UP ó BACKSPACE: Muestra la página anterior.
    - PAGE DOWN ó SPACEBAR: Muestra la página siguiente.
    - n: Siguiente - Muestra el siguiente nodo de texto
    - p: Anterior - Muestra el anterior nodo de texto.
    - u: Arriba - Muestra el nodo padre del nodo actualmente mostrado, usualmente un menú.
    - ENTER: Sigue el hipervínculo en la localización del cursor.
    - q: Quitar, salir.
- info coreutils: Muestra un menú con hipervínculos a cada programa proveído por el paquete coreutils del proyecto GNU.
- README y otros archivos de documentación de programas: Muchos paquetes de software instalado en el sistema contienen archivos de documentación albergados en el directorio /usr/share/doc. Algunos se encuentran en HTML y algunos con la extensión .gz que pueden ser leídos con el comando zless incluido en el paquete de gzip, la mayoría se encuentra en texto plano y se pueden leer con less.

# Información del sistema

- arch: mostrar la arquitectura de la máquina (1). 
- uname -m: mostrar la arquitectura de la máquina (2). 
- uname -r: mostrar la versión del kernel usado. 
- dmidecode -q: mostrar los componentes (hardware) del sistema. 
- hdparm -i /dev/hda: mostrar las características de un disco duro. 
- hdparm -tT /dev/sda: realizar prueba de lectura en un disco duro. 
- cat /proc/cpuinfo: mostrar información de la CPU.
- cat /proc/interrupts: mostrar las interrupciones. 
- cat /proc/meminfo: verificar el uso de memoria. 
- cat /proc/swaps: mostrar ficheros swap. 
- cat /proc/version: mostrar la versión del kernel. 
- cat /proc/net/dev: mostrar adaptadores de red y estadísticas. 
- cat /proc/mounts: mostrar el sistema de ficheros montado. 
- lspci -tv: mostrar los dispositivos PCI. 
- lsusb -tv: mostrar los dispositivos USB. 
- date: mostrar la fecha del sistema. 
- cal 2011: mostrar el almanaque de 2011. 
- cal 07 2011: mostrar el almanaque para el mes julio de 2011. 
- date 041217002011.00: colocar (declarar, ajustar) fecha y hora. 
- clock -w: guardar los cambios de fecha en la BIOS.
- lsb_release -a , cat /etc/\*-release ,  cat  /etc/issue: comprobar la versión de linux.
printenv: muestra las variables del entorno.
- set: variables del entorno más variables de la shell. 

# Apagar (Reiniciar Sistema o Cerrar Sesión)

- shutdown -h now: apagar el sistema (1). 
- init 0: apagar el sistema (2). 
- telinit 0: apagar el sistema (3). 
- halt: apagar el sistema (4). 
- shutdown -h hours:minutes &: apagado planificado del sistema. 
- shutdown -c: cancelar un apagado planificado del sistema. 
- shutdown -r now: reiniciar (1). 
- reboot: reiniciar (2). 
- logout: cerrar sesión.

# Archivos y Directorios

- cd /home: entrar en el directorio “home”.
- cd ..: retroceder un nivel.
- cd ../..: retroceder 2 niveles.
- cd: ir al directorio raíz.
- cd ~user1: ir al directorio user1.
- cd -: ir (regresar) al directorio anterior.
- pwd: mostrar el camino del directorio de trabajo.
- ls: ver los ficheros de un directorio.
- ls -F: ver los ficheros de un directorio.
- ls -l: mostrar los detalles de ficheros y carpetas de un directorio.
- ls -a: mostrar los ficheros ocultos.
- ls \*[0-9]\*: mostrar los ficheros y carpetas que contienen números.
- ls -laR | less → listar recursivamente el contenido del directorio actual y todos los subdirectorios y archivos, incluyendo los ocultos, separados por página.
- tree: mostrar los ficheros y carpetas en forma de árbol comenzando por la raíz. (1)
- lstree: mostrar los ficheros y carpetas en forma de árbol comenzando por la raíz.(2)
- mkdir dir1: crear una carpeta o directorio con nombre ‘dir1′.
- mkdir dir1 dir2: crear dos carpetas o directorios simultáneamente (Crear dos directorios a la vez).
- mkdir -p /tmp/dir1/dir2: crear un árbol de directorios.
- rm -f file1: borrar el fichero llamado ‘file1′.
- rmdir dir1: borrar la carpeta llamada ‘dir1′.
- rm -rf dir1: eliminar una carpeta llamada ‘dir1′ con su contenido de forma recursiva. (Si lo borro recursivo estoy diciendo que es con su contenido).
- rm -rf dir1 dir2: borrar dos carpetas (directorios) con su contenido de forma recursiva.
- mv dir1 newdir: renombrar o mover un fichero o carpeta (directorio). 23.cp file1: copiar un fichero.
- cp file1 file2: copiar dos ficheros al unísono.
- cp dir /\* .: copiar todos los ficheros de un directorio dentro del directorio de trabajo actual. 26.cp -a /tmp/dir1 .: copiar un directorio dentro del directorio actual de trabajo.
- cp -a dir1: copiar un directorio.
- cp -a dir1 dir2: copiar dos directorio al unísono.
- ln -s file1 lnk1: crear un enlace simbólico al fichero o directorio.
- ln file1 lnk1: crear un enlace físico al fichero o directorio.
- touch -t 0712250000 file1: modificar el tiempo real (tiempo de creación) de un fichero o directorio.
- file file1: salida (volcado en pantalla) del tipo mime de un fichero texto. Determina el tipo del archivo.
- iconv -l: listas de cifrados conocidos.
- iconv -f fromEncoding -t toEncoding inputFile > outputFile: crea una nueva forma del fichero de entrada asumiendo que está codificado en fromEncoding y convirtiéndolo a ToEncoding.
- find . -maxdepth 1 -name \*.jpg -print -exec convert ”{}” -resize 80×60 “thumbs/{}” \;: agrupar ficheros redimensionados en el directorio actual y enviarlos a directorios en vistas de miniaturas (requiere convertir desde ImagemagicK).

# Encontrar archivos

- find / -name file1: buscar fichero y directorio a partir de la raíz del sistema.
- find / -user user1: buscar ficheros y directorios pertenecientes al usuario ‘user1′.
- find /home/user1 -name \*.bin: buscar ficheros con extensión ‘. bin’ dentro del directorio ‘/ home/user1′.
- find /usr/bin -type f -atime +100: buscar ficheros binarios no usados en los últimos 100 días.
- find /usr/bin -type f -mtime -10: buscar ficheros creados o cambiados dentro de los últimos 10 días.
- find / -name \*.rpm -exec chmod 755 ‘{}’ \;: buscar ficheros con extensión ‘.rpm’ y modificar permisos.
- find / -xdev -name \*.rpm: Buscar ficheros con extensión ‘.rpm’ ignorando los dispositivos removibles como cdrom, pen-drive, etc....
- locate \*.ps: encuentra ficheros con extensión ‘.ps’ ejecutados primeramente con el command ‘updatedb’.
- whereis halt: mostrar la ubicación de un fichero binario, de ayuda o fuente. En este caso pregunta dónde está el comando ‘halt’.
- which halt: mostrar la senda completa (el camino completo) a un binario / ejecutable.
- which: muestra el Path (senda, camino, ruta) a un binario, programa o ejecutable.

# Montando un sistema de ficheros

- mount /dev/hda2 /mnt/hda2: montar un disco llamado hda2. Verifique primero la existencia del directorio ‘/ mnt/hda2′; si no está, debe crearlo.
- umount /dev/hda2: desmontar un disco llamado hda2. Salir primero desde el punto ‘/ mnt/hda2.
- fuser -km /mnt/hda2: forzar el desmontaje cuando el dispositivo está ocupado.
- umount -n /mnt/hda2: correr el desmontaje sin leer el fichero /etc/mtab. Útil cuando el fichero es de solo lectura o el disco duro está lleno.
- mount /dev/fd0 /mnt/floppy: montar un disco flexible (floppy).
- mount /dev/cdrom /mnt/cdrom: montar un cdrom / dvdrom.
- mount /dev/hdc /mnt/cdrecorder: montar un cd regrabable o un dvdrom.
- mount /dev/hdb /mnt/cdrecorder: montar un cd regrabable / dvdrom (un dvd).
- mount -o loop file.iso /mnt/cdrom: montar un fichero o una imagen iso.
- mount -t vfat /dev/hda5 /mnt/hda5: montar un sistema de ficheros FAT32.
- mount /dev/sda1 /mnt/usbdisk: montar un usb pen-drive o una memoria (sin especificar el tipo de sistema de ficheros).

# Espacio de Disco

- df: mostrar la cantidad de espacio libre en los discos.
- df -h: mostrar una lista de las particiones montadas. 
- ls -lSr |more: mostrar el tamaño de los ficheros y directorios ordenados por tamaño. 
- du -sh dir1: Estimar el espacio usado por el directorio ‘dir1′. 
- du -sk * | sort -rn: mostrar el tamaño de los ficheros y directorios ordenados por tamaño. 
- rpm -q -a –qf ‘%10{SIZE}t%{NAME}n’ | sort -k1,1n: mostrar el espacio usado por los paquetes rpm instalados organizados por tamaño (Fedora, Redhat y otros). 
- dpkg-query -W -f=’${Installed-Size;10}t${Package}n’ | sort -k1,1n: mostrar el espacio usado por los paquetes instalados, organizados por tamaño (Ubuntu, Debian y otros).

# Usuarios y Grupos

- useradd | userdel: es el binario compilado por el sistema operativo.
- adduser | deluser: es un script en Perl que realiza las mismas funciones que useradd pero más amigable que este. Desde las propias páginas de ayuda de Ubuntu recomiendan emplear adduser.
- groupadd nombre_del_grupo: crear un nuevo grupo.
- groupdel nombre_del_grupo: borrar un grupo.
- groupmod -n nuevo_nombre_del_grupo viejo_nombre_del_grupo: renombrar un grupo.
- useradd -c “Name Surname ” -g admin -d /home/user1 -s /bin/bash user1: Crear un nuevo usuario perteneciente al grupo “admin”.
- useradd user1: crear un nuevo usuario.
- adduser nameUser: crea un nuevo usuario.
- userdel -r user1: borrar un usuario (‘-r’ elimina el directorio Home).
- usermod -c “User FTP” -g system -d /ftp/user1 -s /bin/nologin user1: cambiar los atributos del usuario.
- passwd: cambiar contraseña.
- passwd user1: cambiar la contraseña de un usuario (solamente por root).
- chage -E 2011-12-31 user1: colocar un plazo para la contraseña del usuario. En este caso dice que la clave expira el 31 de diciembre de 2011.
- pwck: chequear la sintaxis correcta el formato de fichero de ‘/etc/passwd’ y la existencia de usuarios.
- grpck: chequear la sintaxis correcta y el formato del fichero ‘/etc/group’ y la existencia de grupos.
- newgrp group_name: registra a un nuevo grupo para cambiar el grupo predeterminado de los ficheros creados recientemente.
- deluser userName: elimina un usuario.
- deluser --remove-home userName: elimina un usuario, así como el home y los archivos de éste.
- userdel userName: (CentOS) elimina un usuario.
- userdel -r vozidea: (CentOS) elimina un usuario, así como el home y los archivos de éste.

# Permisos en Ficheros (Usa ”+” para colocar permisos y ”-” para eliminar)

- ls -lh: Mostrar permisos. 
- ls /tmp | pr -T5 -W$COLUMNS: dividir la terminal en 5 columnas. 
- chmod ugo+rwx directory1: colocar permisos de lectura ®, escritura (w) y ejecución(x) al propietario (u), al grupo (g) y a otros (o) sobre el directorio ‘directory1′. 
- chmod go-rwx directory1: quitar permiso de lectura ®, escritura (w) y (x) ejecución al grupo (g) y otros (o) sobre el directorio ‘directory1′. 
- chown user1 file1: cambiar el dueño de un fichero. 
- chown -R user1 directory1: cambiar el propietario de un directorio y de todos los ficheros y directorios contenidos dentro. 
- chgrp group1 file1: cambiar grupo de ficheros. 
- chown user1:group1 file1: cambiar usuario y el grupo propietario de un fichero. 
- find / -perm -u+s: visualizar todos los ficheros del sistema con SUID configurado. 
- chmod u+s /bin/file1: colocar el bit SUID en un fichero binario. El usuario que corriendo ese fichero adquiere los mismos privilegios como dueño. 
- chmod u-s /bin/file1: deshabilitar el bit SUID en un fichero binario. 
- chmod g+s /home/public: colocar un bit SGID en un directorio –similar al SUID pero por directorio. 
- chmod g-s /home/public: desabilitar un bit SGID en un directorio. 
- chmod o+t /home/public: colocar un bit STIKY en un directorio. Permite el borrado de ficheros solamente a los dueños legítimos. 
- chmod o-t /home/public: desabilitar un bit STIKY en un directorio.

# Atributos especiales en ficheros (Usa ”+” para colocar permisos y ”-” para eliminar)

- chattr +a file1: permite escribir abriendo un fichero solamente modo append.
- chattr +c file1: permite que un fichero sea comprimido / descomprimido automaticamente.
- chattr +d file1: asegura que el programa ignore borrar los ficheros durante la copia de seguridad.
- chattr +i file1: convierte el fichero en invariable, por lo que no puede ser eliminado, alterado, renombrado, ni enlazado.
- chattr +s file1: permite que un fichero sea borrado de forma segura.
- chattr +S file1: asegura que un fichero sea modificado, los cambios son escritos en modo synchronous como con sync.
- chattr +u file1: te permite recuperar el contenido de un fichero aún si este está cancelado.
- lsattr: mostrar atributos especiales.

# Archivos y Ficheros comprimidos

- bunzip2 file1.bz2: descomprime un fichero llamado ‘file1.bz2′. 
- bzip2 file1: comprime un fichero llamado ‘file1′. 
- gunzip file1.gz: descomprime un fichero llamado ‘file1.gz’. 
- gzip file1: comprime un fichero llamado ‘file1′. 
- gzip -9 file1: comprime con compresión máxima. 
- rar a file1.rar test_file: crear un fichero rar llamado ‘file1.rar’. 
- rar a file1.rar file1 file2 dir1: comprimir ‘file1′, ‘file2′ y ‘dir1′ simultáneamente. 
- rar x file1.rar: descomprimir archivo rar. 
- unrar x file1.rar: descomprimir archivo rar. 
- tar -cvf archive.tar file1: crear un tarball descomprimido. 
- tar -cvf archive.tar file1 file2 dir1: crear un archivo conteniendo ‘file1′, ‘file2′ y’dir1′. 
- tar -tf archive.tar: mostrar los contenidos de un archivo. 
- tar -xvf archive.tar: extraer un tarball. 
- tar -xvf archive.tar -C /tmp: extraer un tarball en / tmp. 
- tar -cvfj archive.tar.bz2 dir1: crear un tarball comprimido dentro de bzip2. 
- tar -xvfj archive.tar.bz2: descomprimir un archivo tar comprimido en bzip2. 
- tar -cvfz archive.tar.gz dir1: crear un tarball comprimido en gzip. 
- tar -xzvf archive.tar.gz: descomprimir un archive tar comprimido en gzip. 
- zip file1: crear un archivo comprimido en zip
- zip -r file1.zip file1 file2 dir1: comprimir, en zip, varios archivos y directorios de forma simultánea. 
- unzip file1.zip: descomprimir un archivo zip.

# Paquetes RPM (Red Hat, Fedora y similares)

- rpm -ivh package.rpm: instalar un paquete rpm.
- rpm -ivh –nodeeps package.rpm: instalar un paquete rpm ignorando las peticiones de dependencias.
- rpm -U package.rpm: actualizar un paquete rpm sin cambiar la configuración de los ficheros.
- rpm -F package.rpm: actualizar un paquete rpm solamente si este está instalado.
- rpm -e package_name.rpm: eliminar un paquete rpm.
- rpm -qa: mostrar todos los paquetes rpm instalados en el sistema.
- rpm -qa | grep httpd: mostrar todos los paquetes rpm con el nombre “httpd”.
- rpm -qi package_name: obtener información en un paquete específico instalado.
- rpm -qg “System Environment/Daemons”: mostar los paquetes rpm de un grupo software.
- rpm -ql package_name: mostrar lista de ficheros dados por un paquete rpm instalado.
- rpm -qc package_name: mostrar lista de configuración de ficheros dados por un paquete rpm instalado.
- rpm -q package_name –whatrequires: mostrar lista de dependencias solicitada para un paquete rpm.
- rpm -q package_name –whatprovides: mostar la capacidad dada por un paquete rpm.
- rpm -q package_name –scripts: mostrar los scripts comenzados durante la instalación /eliminación.
- rpm -q package_name –changelog: mostar el historial de revisions de un paquete rpm.
- rpm -qf /etc/httpd/conf/httpd.conf: verificar cuál paquete rpm pertenece a un fichero dado.
- rpm -qp package.rpm -l: mostrar lista de ficheros dados por un paquete rpm que aún no ha sido instalado.
- rpm –import /media/cdrom/RPM-GPG-KEY: importar la firma digital de la llave pública.
- rpm –checksig package.rpm: verificar la integridad de un paquete rpm.
- rpm -qa gpg-pubkey: verificar la integridad de todos los paquetes rpm instalados.
- rpm -V package_name: chequear el tamaño del fichero, licencias, tipos, dueño, grupo, chequeo de resumen de MD5 y última modificación.
- rpm -Va: chequear todos los paquetes rpm instalados en el sistema. Usar con cuidado.
- rpm -Vp package.rpm: verificar un paquete rpm no instalado todavía.
- rpm2cpio package.rpm | cpio –extract –make-directories *bin*: extraer fichero ejecutable desde un paquete rpm.
- rpm -ivh /usr/src/redhat/RPMS/`arch`/package.rpm: instalar un paquete construido desde una fuente rpm.
- rpmbuild –rebuild package_name.src.rpm: construir un paquete rpm desde una fuente rpm.

# Actualizador de paquetes YUM (Red Hat, Fedora y similares)

- yum install package_name: descargar e instalar un paquete rpm.
- yum localinstall package_name.rpm: este instalará un RPM y tratará de resolver todas las dependencies para ti, usando tus repositorios.
- yum update package_name.rpm: actualizar todos los paquetes rpm instalados en el sistema.
- yum update package_name: modernizar / actualizar un paquete rpm.
- yum remove package_name: eliminar un paquete rpm.
- yum list: listar todos los paquetes instalados en el sistema.
- yum search package_name: Encontrar un paquete en repositorio rpm.
- yum clean packages: limpiar un caché rpm borrando los paquetes descargados.
- yum clean headers: eliminar todos los ficheros de encabezamiento que el sistema usa para resolver la dependencia.
- yum clean all: eliminar desde los paquetes caché y ficheros de encabezado.
 
# Paquetes Deb (Debian, Ubuntu y derivados)

- dpkg -i package.deb: instalar / actualizar un paquete deb. 
- dpkg -r package_name: eliminar un paquete deb del sistema. 
- dpkg -l: mostrar todos los paquetes deb instalados en el sistema. 
- dpkg -l | grep httpd: mostrar todos los paquetes deb con el nombre “httpd” 
- dpkg -s package_name: obtener información en un paquete específico instalado en el sistema. 
- dpkg -L package_name: mostar lista de ficheros dados por un paquete instalado en el sistema. 
- dpkg –contents package.deb: mostrar lista de ficheros dados por un paquete no instalado todavía. 
- dpkg -S /bin/ping: verificar cuál paquete pertenece a un fichero dado.

# Actualizador de paquetes APT (Debian, Ubuntu y derivados)

- apt-get install package_name: instalar / actualizar un paquete deb. 
- apt-cdrom install package_name: instalar / actualizar un paquete deb desde un cdrom. 
- apt-get update: actualizar la lista de paquetes. 
- apt-get upgrade: actualizar todos los paquetes instalados. 
- apt-get remove package_name: eliminar un paquete deb del sistema. 
- apt-get check: verificar la correcta resolución de las dependencias. 
- apt-get clean: limpiar cache desde los paquetes descargados. 
- apt-cache search searched-package: retorna lista de paquetes que corresponde a la serie «paquetes buscados».

# Ver el contenido de un fichero

- cat file1: ver los contenidos de un fichero comenzando desde la primera hilera. 
- tac file1: ver los contenidos de un fichero comenzando desde la última línea. 
- more file1: ver el contenido a lo largo de un fichero. 
- less file1: parecido al commando ‘more’ pero permite salvar el movimiento en el fichero así como el movimiento hacia atrás. 
- head -2 file1: ver las dos primeras líneas de un fichero. 
- tail -2 file1: ver las dos últimas líneas de un fichero. 7.tail -f /var/log/messages: ver en tiempo real qué ha sido añadido al fichero.

# Manipulación de texto

- cat file1 file2 .. | command <> file1_in.txt_or_file1_out.txt: sintaxis general para la manipulación de texto utilizando PIPE, STDIN y STDOUT. 
- cat file1 | command( sed, grep, awk, grep, etc...) > result.txt: sintaxis general para manipular un texto de un fichero y escribir el resultado en un fichero nuevo. 
- cat file1 | command( sed, grep, awk, grep, etc...) » result.txt: sintaxis general para manipular un texto de un fichero y añadir resultado en un fichero existente. 
- grep Aug /var/log/messages: buscar palabras “Aug” en el fichero ‘/var/log/messages’.
- grep ^Aug /var/log/messages: buscar palabras que comienzan con “Aug” en fichero ‘/var/log/messages’ 6.grep [0-9] /var/log/messages: seleccionar todas las líneas del fichero ‘/var/log/messages’ que contienen números. 
- grep Aug -R /var/log/\*: buscar la cadena “Aug” en el directorio ‘/var/log’ y debajo. 
- sed ‘s/stringa1/stringa2/g’ example.txt: reubicar “string1” con “string2” en ejemplo.txt 
- sed ‘/^$/d’ example.txt: eliminar todas las líneas en blanco desde el ejemplo.txt 
- sed ‘/ \*#/d; /^$/d’ example.txt: eliminar comentarios y líneas en blanco de ejemplo.txt
- echo ‘esempio’ | tr ‘[:lower:]‘ ‘[:upper:]‘: convertir minúsculas en mayúsculas. 
- sed -e ’1d’ result.txt: elimina la primera línea del fichero ejemplo.txt 
- sed -n ‘/stringa1/p’: visualizar solamente las líneas que contienen la palabra “string1”.

# Expansion

- Para los ejemplos se usa echo, pero se puede usar cualquier otro comando como mkdir, ls, mv, etc.
- echo: Imprime sus argumentos de texto en salida estándar (output standard).
- echo \*: Imprime el nombre de los archivos o directorios del directorio, incluso funciona con rutas como echo /usr/\*/share ó /usr.
- echo [wildcards]: Imprime los hombres de los archivos que coincidan con las wildcards usadas.
- echo ~[usuario]: muestra del directorio home del usuario que se escribe delante de la tilde, si no hay nombre de usuario, muestra el del usuario activo.
- echo $((expresión)): Calcula operaciones aritméticas, pero sólo admite y regresa enteros, sus operadores son +, -, \*, /, %, \*\*.
- echo {RegEx}: Se pueden crear múltiples cadenas de texto desde los patrones contenidos en los corchetes. Los corchetes pueden contener una lista de elementos separados por comas ({a,b,c}) o un rango de enteros o caracteres simples ({a..z} ó {1..9}) que pueden estar en orden inverso. No deben contener espacios en blanco. También se pueden anidar corchetes como por ejemplo echo a{A{1,2},B{3,4}}b , mkdir {2009..2011}-0{1..9} {2009..2011}-{10..12}.
- echo $USER: Imprime el contenido de una variable.
- echo $(comando): Nos permite usar la salida de un comando como una expansión como por ejemplo echo ($ls). También admite pipelines (|).

# Quoting

- Es el mecanismo por el cual la shell suprime selectivamente las expansiones indeseadas.
- “” : El texto puesto entre las dobles comillas hace que los caracteres especiales usados por la shell pierdan sus significado especial y sean tratados como caracteres ordinarios; excepto $, \, \`, además de la expansión paramétrica ($USER), expansión aritmética ($((2\*2))), y la sustitución de comando ($(cal)).
- ‘’ : Suprimen todas las expansiones.

# Establecer caracter y conversión de ficheros

- dos2unix filedos.txt fileunix.txt: convertir un formato de fichero texto desde MSDOS a UNIX. 
- unix2dos fileunix.txt filedos.txt: convertir un formato de fichero de texto desde UNIX a MSDOS. 
- recode ..HTML < page.txt > page.html: convertir un fichero de texto en html. 4.recode -l | more: mostrar todas las conversiones de formato disponibles.

# Análisis del sistema de ficheros

- badblocks -v /dev/hda1: Chequear los bloques defectuosos en el disco hda1. 
- fsck /dev/hda1: reparar / chequear la integridad del fichero del sistema Linux en el disco hda1.
- fsck.ext2 /dev/hda1: reparar / chequear la integridad del fichero del sistema ext 2 en el disco hda1. 
- e2fsck /dev/hda1: reparar / chequear la integridad del fichero del sistema ext 2 en el disco hda1. 
- e2fsck -j /dev/hda1: reparar / chequear la integridad del fichero del sistema ext 3 en el disco hda1. 
- fsck.ext3 /dev/hda1: reparar / chequear la integridad del fichero del sistema ext 3 en el disco hda1. 
- fsck.vfat /dev/hda1: reparar / chequear la integridad del fichero sistema fat en el disco hda1. 
- fsck.msdos /dev/hda1: reparar / chequear la integridad de un fichero del sistema dos en el disco hda1.dosfsck /dev/hda1: reparar / chequear la integridad de un fichero del sistema dos en el disco hda1.

# Formatear un sistema de ficheros

- mkfs /dev/hda1: crear un fichero de sistema tipo Linux en la partición hda1.
- mke2fs /dev/hda1: crear un fichero de sistema tipo Linux ext 2 en hda1.
- mke2fs -j /dev/hda1: crear un fichero de sistema tipo Linux ext3 (periódico) en la partición hda1.
- mkfs -t vfat 32 -F /dev/hda1: crear un fichero de sistema FAT32 en hda1.
- fdformat -n /dev/fd0: formatear un disco flooply.
- mkswap /dev/hda3: crear un fichero de sistema swap.

# Trabajo con la SWAP

- mkswap /dev/hda3: crear fichero de sistema swap.
- swapon /dev/hda3: activando una nueva partición swap.
- swapon /dev/hda2 /dev/hdb3: activar dos particiones swap.

# Salvas (Backup)

- dump -0aj -f /tmp/home0.bak /home: hacer una salva completa del directorio ‘/home’. 
- dump -1aj -f /tmp/home0.bak /home: hacer una salva incremental del directorio ‘/home’. 
- restore -if /tmp/home0.bak: restaurando una salva interactivamente. 
- rsync -rogpav –delete /home /tmp: sincronización entre directorios. 
- rsync -rogpav -e ssh –delete /home ip_address:/tmp: rsync a través del túnel SSH. 
- rsync -az -e ssh –delete ip_addr:/home/public /home/local: sincronizar un directorio local con un directorio remoto a través de ssh y de compresión. 
- rsync -az -e ssh –delete /home/local ip_addr:/home/public: sincronizar un directorio remoto con un directorio local a través de ssh y de compresión. 
- dd bs=1M if=/dev/hda | gzip | ssh user@ip_addr ‘dd of=hda.gz’: hacer una salva de un disco duro en un host remoto a través de ssh. 
- dd if=/dev/sda of=/tmp/file1: salvar el contenido de un disco duro a un fichero. (En este caso el disco duro es “sda” y el fichero “file1”). 
- tar -Puf backup.tar /home/user: hacer una salva incremental del directorio ‘/home/user’.
- ( cd /tmp/local/ && tar c . ) | ssh -C user@ip_addr ‘cd /home/share/ && tar x -p’: copiar el contenido de un directorio en un directorio remoto a través de ssh. 
- ( tar c /home ) | ssh -C user@ip_addr ‘cd /home/backup-home && tar x -p’: copiar un directorio local en un directorio remoto a través de ssh. 
- tar cf – . | (cd /tmp/backup ; tar xf – ): copia local conservando las licencias y enlaces desde un directorio a otro. 
- find /home/user1 -name ‘\*.txt’ | xargs cp -av –target-directory=/home/backup/ –parents: encontrar y copiar todos los ficheros con extensión ‘.txt’ de un directorio a otro. 
- find /var/log -name ‘\*.log’ | tar cv –files-from=- | bzip2 > log.tar.bz2: encontrar todos los ficheros con extensión ‘.log’ y hacer un archivo bzip. 
- dd if=/dev/hda of=/dev/fd0 bs=512 count=1: hacer una copia del MRB (Master Boot Record) a un disco floppy. 17.dd if=/dev/fd0 of=/dev/hda bs=512 count=1: restaurar la copia del MBR (Master Boot Record) salvada en un floppy.

# CD-ROM

- cdrecord -v gracetime=2 dev=/dev/cdrom -eject blank=fast -force: limpiar o borrar un cd regrabable. 
- mkisofs /dev/cdrom > cd.iso: crear una imagen iso de cdrom en disco. 
- mkisofs /dev/cdrom | gzip > cd_iso.gz: crear una imagen comprimida iso de cdrom en disco. 
- mkisofs -J -allow-leading-dots -R -V “Label CD” -iso-level 4 -o ./cd.iso data_cd: crear una imagen iso de un directorio. 
- cdrecord -v dev=/dev/cdrom cd.iso: quemar una imagen iso. 
- gzip -dc cd_iso.gz | cdrecord dev=/dev/cdrom -: quemar una imagen iso comprimida. 
- mount -o loop cd.iso /mnt/iso: montar una imagen iso. 
- cd-paranoia -B: llevar canciones de un cd a ficheros wav. 
- cd-paranoia – ”-3”: llevar las 3 primeras canciones de un cd a ficheros wav. 
- cdrecord –scanbus: escanear bus para identificar el canal scsi. 11.dd if=/dev/hdc | md5sum: hacer funcionar un md5sum en un dispositivo, como un CD.

# Trabajo con la RED ( LAN y Wi-Fi)

- ifconfig eth0: mostrar la configuración de una tarjeta de red Ethernet. 
- ifup eth0: activar una interface ‘eth0′. 
- ifdown eth0: deshabilitar una interface ‘eth0′. 
- ifconfig eth0 192.168.1.1 netmask 255.255.255.0: configurar una dirección IP. 
- ifconfig eth0 promisc: configurar ‘eth0′en modo común para obtener los paquetes (sniffing). 
- dhclient eth0: activar la interface ‘eth0′ en modo dhcp. 
- route -n: mostrar mesa de recorrido. 
- route add -net 0/0 gw IP_Gateway: configurar entrada predeterminada.
- route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.1.1: configurar ruta estática para buscar la red ’192.168.0.0/16′. 
- route del 0/0 gw IP_gateway: eliminar la ruta estática. 
- echo “1” > /proc/sys/net/ipv4/ip_forward: activar el recorrido ip. 
- hostname: mostrar el nombre del host del sistema. 
- host www.example.com: buscar el nombre del host para resolver el nombre a una dirección ip(1). 
- nslookup www.example.com: buscar el nombre del host para resolver el nombre a una direccióm ip y viceversa(2). 
- ip link show: mostar el estado de enlace de todas las interfaces. 
- mii-tool eth0: mostar el estado de enlace de ‘eth0′. 
- ethtool eth0: mostrar las estadísticas de tarjeta de red ‘eth0′. 
- netstat -anpl: Da el estado actual de los puertos y conexiones abiertas.
- netstat -tup: mostrar todas las conexiones de red activas y sus PID. 
- netstat -tupl: mostrar todos los servicios de escucha de red en el sistema y sus PID.
- netstat -punta: mostrar todas las conexiones activas por dirección IP y puerto.
- tcpdump tcp port 80: mostrar todo el tráfico HTTP. 
- iwlist scan: mostrar las redes inalámbricas. 
- iwconfig eth1: mostrar la configuración de una tarjeta de red inalámbrica. 
- whois www.example.com: buscar en base de datos Whois.
- iftop -nNP -i eth0 → mostrar en tiempo real las conexiones abiertas en eth0 y su tasa de transferencia.
- sockstat → mostrar información sobre las conexiones abiertas.
- arp-scan -l → descubrir en la red las direcciones IP y MAC.
- nm-tool → muestra configuración de red (en caso de usar Network Manager obtiene los DNS).

# Redes de Microsoft Windows (SAMBA)

- nbtscan ip_addr: resolución de nombre de red bios. 
- nmblookup -A ip_addr: resolución de nombre de red bios. 
- smbclient -L ip_addr/hostname: mostrar acciones remotas de un host en windows.

# Tablas IP (CORTAFUEGOS)

- iptables -t filter -L: mostrar todas las cadenas de la tabla de filtro. 
- iptables -t nat -L: mostrar todas las cadenas de la tabla nat. 
- iptables -t filter -F: limpiar todas las reglas de la tabla de filtro. 
- iptables -t nat -F: limpiar todas las reglas de la tabla nat. 
- iptables -t filter -X: borrar cualquier cadena creada por el usuario. 
- iptables -t filter -A INPUT -p tcp –dport telnet -j ACCEPT: permitir las conexiones telnet para entar.iptables -t filter -A OUTPUT -p tcp –dport http -j DROP: bloquear las conexiones HTTP para salir. 
- iptables -t filter -A FORWARD -p tcp –dport pop3 -j ACCEPT: permitir las conexiones POP a una cadena delantera. 
- iptables -t filter -A INPUT -j LOG –log-prefix “DROP INPUT”: registrando una cadena de entrada. 
- iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE: configurar un PAT (Puerto de traducción de dirección) en eth0, ocultando los paquetes de salida forzada. 
- iptables -t nat -A PREROUTING -d 192.168.0.1 -p tcp -m tcp –dport 22 -j DNAT –to-destination 10.0.0.2:22: redireccionar los paquetes diriguidos de un host a otro.

# Monitoreando y depurando

- top: mostrar las tareas de linux usando la mayoría cpu. 
- ps -eafw: muestra las tareas Linux. 
- ps -e -o pid,args –forest: muestra las tareas Linux en un modo jerárquico. 
- pstree: mostrar un árbol sistema de procesos. 
- kill -9 ID_Processo: forzar el cierre de un proceso y terminarlo. 
- kill -1 ID_Processo: forzar un proceso para recargar la configuración.
- killall nameProcess: Mata un proceso por su nombre. E.j.: killall google-chrome. 
- lsof -p $$: mostrar una lista de ficheros abiertos por procesos.
- lsof /home/user1: muestra una lista de ficheros abiertos en un camino dado del sistema. 
- strace -c ls >/dev/null: mostrar las llamadas del sistema hechas y recibidas por un proceso. 
- strace -f -e open ls >/dev/null: mostrar las llamadas a la biblioteca. 11.watch -n1 ‘cat /proc/interrupts’: mostrar interrupciones en tiempo real. 
- last reboot: mostrar historial de reinicio. 
- lsmod: mostrar el kernel cargado. 
- free -m: muestra el estado de la RAM en megabytes. 
- smartctl -A /dev/hda: monitorear la fiabilidad de un disco duro a través de SMART. 
- smartctl -i /dev/hda: chequear si SMART está activado en un disco duro. 
- tail /var/log/dmesg: mostrar eventos inherentes al proceso de carga del kernel. 
- tail /var/log/messages: mostrar los eventos del sistema.

# Otros comandos útiles

- apropos ...keyword: mostrar una lista de comandos que pertenecen a las palabras claves de un programa; son útiles cuando tú sabes qué hace tu programa, pero de sconoces el nombre del comando. 
- man ping: mostrar las páginas del manual on-line; por ejemplo, en un comando ping, usar la opción ‘-k’ para encontrar cualquier comando relacionado. 
- whatis ...keyword: muestra la descripción de lo que hace el programa. 
- mkbootdisk –device /dev/fd0 `uname -r`: crear un floppy boteable. 
- gpg -c file1: codificar un fichero con guardia de seguridad GNU. 
- gpg file1.gpg: decodificar un fichero con Guardia de seguridad GNU. 7.wget -r www.example.com: descargar un sitio web completo. 
- wget -c www.example.com/file.iso: descargar un fichero con la posibilidad de parar la descargar y reanudar más tarde. 
- echo ‘wget -c www.example.com/files.iso‘ | at 09:00: Comenzar una descarga a cualquier hora. En este caso empezaría a las 9 horas. 
- ldd /usr/bin/ssh: mostrar las bibliotecas compartidas requeridas por el programa ssh. 
- alias hh=’history’: colocar un alias para un commando –hh= Historial. 
- chsh: cambiar el comando Shell. 
- chsh –list-shells: es un comando adecuado para saber si tienes que hacer remoto en otra terminal. 
- who -a: mostrar quien está registrado, e imprimir hora del último sistema de importación, procesos muertos, procesos de registro de sistema, procesos activos producidos por init, funcionamiento actual y últimos cambios del reloj del sistema.
- crontab -e: Edita o muestra el crontab del sistema crontab -e

# Conexión remota host

- ssh: invoca el protocolo ssh para conectarse remotamente a un host: ssh usuario@ip/hostname
- scp: copia remota de archivos; establecida la conexión ssh previamente se hace lo siguiente: scp [[user1@]hostname1:]file1 ... [[user2@]hostname2:]file2
- scp -r: como el anterior, pero hace una copia recursiva de todo un directorio: scp [-r] [[user1@]hostname1:]file1 ... [[user2@]hostname2:]file2
 
# History

- history : Despliega el contenido de la lista del historial de comandos.
- !number : Expande el contenido del número en el historial (!88).
- CTRL-R : Buscar inversa e incrementalmente en el historial, se busca a medida que se escribe. Al presionar nuevamente se busca la siguiente coincidencia.
- CTRL-J: Copia la línea del historia.
- CTRL- G ó CTRL-C : Quita la búsqueda.
- CTRL-P : Mover a la entrada previa del historial de comandos. La misma acción que flecha arriba.
- CTRL-N : Mover a la siguiente entrada del historial de comandos. La misma acción que flecha abajo.
- ALT-< : Mover hacia el inicio (arriba) de la lista del historial.
- ALT-> : Mover al final (abajo) de la lista del historial.
- ALT-P : Búsqueda inversa, no incremental. Primero se teclea el comando a buscar, después, al presionar ENTER, la búsqueda se realiza.
- ALT-N : Búsqueda hacia delante, no incremental.
- ALT-O : Ejecuta el elemento actual en el historial de búsqueda y avanza al siguiente. Esto es útil si están intentando ejecutar una secuencia de comandos en el historial.
- !! : Repetir el último comando.
- !number : Repetir el elemento de la lista del historial con el número indicado.
- !string : Repetir el último elemento de la lista del historial que comienza por el string indicado.
- !?string : Repetir el último elemento de la lista que concuerda con el string indicado.
- script [file] : Muchas de las distribuciones de Linux incluyen este programa, el cual puede ser usado para grabar una sesión entera de shell y guardarla en un archivo.

# Operadores de control de flujo

- > : Direcciona un flujo hacia un archivo/dispositivo.
- >>: Agregar el texto al final del archivo/dispositivo.
- <: Redireccionamiento hacia atrás; envía el contenido de un archivo hacia el proceso anterior o hacia un comando.
- ; : Encadena múltiples comandos por línea, ejecutándolos uno tras otro.
- | : Envía la salida de un proceso o comando hacia otro; es útil para hacer filtrados o para evitar el uso de archivos temporales. Por ejemplo: cat /var/log/messages | egrep -i “Oct 10”
- $(comando): Evalúa un comando al momento e inserta el resultado en la línea en que fue invocado. También puede utilizarse con comillas simples. Por ejemplo: apt-get install-headers-$(uname -r)
- &: Ejecuta un comando y lo envía a segundo plano, permite recuperar control del prompt.
- &&: como el ;el comando que siga se ejecutará si y sólo sí el comando anterior terminó de manera exitosa.

# Caracteres de escape

- \ : Se usa para escapar un solo carácter de su significado especial. A menudo se hace dentro de dobles comillas (“”) para evitar alguna expansión. También se puede usar para escapar un carácter especial de un nombre de archivo como mv bad\&filename good_filename. Para escapar el carácter de escape se hace así \\.

# Control codes | código de control

- \a : Campana (“alert” - causa un beep de la computadora).
- \b : Retroceso.
- \n : Nueva línea (en sistemas tipo Unix, esto produce un linefeed).
- \r : Regreso de “carro”.
- \t : Tab.
- echo -e  ó $’ ’ : permite interpretar a shell las secuencias de escape.

# Movimiento de cursor

- ctrl-A: Mueve el cursor al inicio de la línea.
- ctrl-E: Mueve el cursor al final de la línea.
- ctrl-F: Mueve el cursor al siguiente carácter hacia la derecha, como la flecha derecha.
- ctrl-B: Mueve el cursor al siguiente carácter hacia la izquierda, como la flecha izquierda.
- alt-F: Mueve el cursor una palabra adelante.
- alt-B: Mueve el cursor una palabra atrás.
- ctrl-L: similar a clear, limpia la pantalla y mueve el cursor hacia la esquina superior izquierda.

# Modificando el texto

- ctrl-D: Elimina el carácter en la posición del cursor.
- ctrl-T:Cambia o transpone el carácter en la posición del cursor con el que lo precede.
- alt-T: Transpone la palabra en la localización del cursor con la precedente.
- alt-L: Convierte los caracteres desde la posición del cursor hasta el final de la palabra en minúsculas.
- alt-U: Convierte los caracteres desde la posición del cursor hasta el final en mayúsculas.

# Killing and Yanking (cortar y pegar)

- ctrl-K: Kill el texto desde la posición del cursor hasta el final de la línea.
- ctrl-U: Kill el texto desde la posición del cursor hasta el inicio de la línea.
- ctrl-D: Kill el texto desde la posición del cursor hasta el final de la palabra actual.
- alt-backspace: Kill el texto desde la posición actual hasta el inicio de la actual palabra. Si el cursor está al inicio de una palabra, kill la palabra previa.
- ctrl-Y: Yank el texto desde la posición del kill-ring y lo inserta en la posición del cursor. 

# Permisos

- Id: obtiene el ID del usuario (uid) y del grupo (gid), así como de los dispositivos. 

# Autocompletar comando

- TAB : Completa del comando, si no resulta ambiguo.
- ALT-? : Muestra todas las posibilidades de completado.
- ALT-\* : Inserta todas las posibilidades de completado.

# Miscelánea

- clear : Limpia la pantalla.
- Inicio de sentencias:
    - $ : variable
    - ~ : usernames
    - @ : hostnames
    - word : comando
- READLINE : mucha documentación de terminal.
- wc: cuenta la cantidad de líneas.

# Conceptos

- Librería: Una colección de rutinas que diferentes programas pueden usar.
- Killing and yanking: La documentación de Readline usa los términos killing y yanking para referirse a lo que comúnmente llamamos copiar y pegar. Los elementos cortados se guardan en el buffer llamado kill-ring.
- meta key: es la tecla alt, avece ESC también funciona de ese modo.

#  Storage Media

- /etc/fstab: lista los dispositivos que son montados al momento del inicio.

# Desmontar

- umount /dev/deviceName

# Manipulando particiones

- sudo fdisk /dev/deviseName #Siguiendo las instrucciones se pueden eliminar y crear particiones.
- sudo mkfs -t typeFileSistem /dev/deviseName #Permite formatear particiones
- sudo fsck /dev/deviseName #Repara archivos corruptos, fuck.

# Mover datos directamente de un dispositivo a otro

dd: (data definition) este comando es muy poderoso, permite copiar los datos en su forma “raw” hacia otro dispositivo de la misma capacidad o bien hacia una imagen.

Sintaxis:
dd if=input_file of=output_file [bs=block_size [count=blocks]]

Dispositivos de la misma capacidad:
dd if=/dev/sdb of=/dev/sdc

Dispositivo a imagen
dd if=/dev/sdb of=flash_drive.img

¡Advertencia! No intercambiar el orden de if y of, y revisar bien los parámetros, o los datos del dispositivo pueden quedar inutilizables.

Crear ISO de CD o DVD de datos
dd if=/dev/cdrom of=ubuntu.iso #para CD de música usar cdrdao

Herramientas para quemar y crear CD: wodim y genisoimage.

# Imágen desde una colección de archivos

Para crear un archivo de imagen ISO que contenga los contenidos de un directorio, usamos el programa enisoimage. Para hacer esto, primero creamos un directorio que contiene todo los archivos que deseamos incluir en la imagen y luego ejecutamos el comando  genisoimage para crear el archivo de imagen. Por ejemplo, si hubiéramos creado un directorio llamado ~/cd-rom-files y se lo llenó con archivos para nuestro CD-ROM o DVD, podemos crear
un archivo de imagen llamado cd-rom.iso con el siguiente comando:

genisoimage -o cd-rom.iso -R -J ~/cd-rom-files

La opción -R agrega metadatos para las extensiones de Rock Ridge, que permiten el uso de nombres de archivo largos y permisos de archivos estilo POSIX. Del mismo modo, el -J opción habilita las extensiones de Joliet, que permiten nombres de archivo largos en Windows.

# Networking
Examinar y monitorear la red
ping: El comando ping envía un paquete especial de red llamado IMCP ECHO_REQUEST para un host especificado. La mayoría de los dispositivos de red que reciben este paquete responderán a él, permitiendo que la conexión de red de trabajo pueda ser verificada.

traceroute: El programa Traceroute (algunos sistemas usan el programa similar de tracepath) muestra una lista de todos los "saltos" que el tráfico de red requiere para llegar al host especificado.

ip: El programa ip es una herramienta de configuración de red multipropósito que hace uso completo de las funciones de red de rango disponibles en los núcleos Linux modernos. Con ip, podemos examinar las interfaces de red de un sistema de red y la tabla de enrutamiento.

netstat: El programa netstat se utiliza para examinar diversos ajustes de red y estadísticas.Utilizando la opción de "-ie" podemos examinar las interfaces de red en nuestro sistema. 

