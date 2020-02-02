# Commands

# Services

- service --status-all

# Environment Variables

- export VAR=valor: con export se hace accesible a la variable para toda la sesi�n.
- export PATH=$PATH:/nuevo/directorio 


## ssh

- ssh user@host
- .ssh/config: en este archivo se encuentran las configuraciones. P.j.:

    Host name
        HostName XXX.XXX.XXX.XXX
        IdentifyFile path/file
        User user
        Port ###
    ...

Puede tener configurados cuantos host se quieren. Las opciones obigatorias son **HostName** y **User**.

## System characteristics

- neofetch
- cat /etc/\*-release
- lsb_release -a
- cat /etc/issue
- uname -a

## Exec commans in background

- _command_ &
- [ctrl] + z: send current command to background, to restore:
- fg: is used to restore the execution of comman to foreground.

## Process in execution

- ps ax: all process running.
- top: show in real time al process.

## Stop process

- kill -9 [PID]: stops immediately the process
- killall [executable file name]: stops the process

## Permissions and owners

- chmod: it change file mode, it change individuali persmissions.
    
    - u: owner user
    - g: group
    - o: others
    - a: all
    - examples: add read permissions: o+r, remove that permissions: o-r
    
    - - = 0
    - x = 1
    - w = 2
    - r = 4
    - Permisos del usuario propietario: r (4) + w (2) + x (1) = 7.
    - Permisos del grupo al que pertenece el archivo: r (4) + x (1) = 5.
    - Permisos del grupo al que pertenece el archivo: r (4) = 4.


- chown: it change file owner.
    - sudo chown _user_ file
    - sudo chown _user_:_group_ file
    
- chgrp: it change file group wner.

## Downloads

- curl url -o filename: descargar un archivo, se usa para realizar pedidos crudos, se recibe la respuesta http, y es lo que se muestra en pantalla.
- curl -v url: muestra tambi�n toda la comunicaci�n htt.

- wget url: Se utiliza m�s para descargar alg�n archivo.

## Compress uncompress

- zip _nombre.zip_ _archivosAcomprimir_: comprimir archivos en zip.

- unzip -vl _archivo.zip_: muestrar los archivos del zip.
- unzip _archivo.zip_: descomprimir archivo

- tar cfz _nombre.tgz_ _archivosAcomprimir_: comprimir archivos en tar.
- tar xfz _nombre.tgz_: extraer.
- tar tf file: ver el contenido del comprimido.

- gzip _file_: comprime archivo, elimina el original.
- gzip -d _file.gz_: escomprimer archivo, elimina el original.

## Redirect string

- 0<: stdin standart in
- 1>: stdout standart out
- 2>: stderr standar error
- 1>&2: redirigir ambas salidas al mismo lugar

# Operators

## operador | (pipe):

- command_1 | command_2: Manda el STDOUT de command_1 al STDIN de command_2

## operador >

- command_1 > FILE: Manda el STDOUT de command_1 al inicio de FILE. Si FILE no existe lo crea, si existe losobreescribe.

## operador >>

- command_1 >> FILE: Manda el STDOUT de command_1 al inicio de FILE. Si FILE no existe lo crea, si existe lo concatena al final(tras un _newline_).

## operador <

command_1 < FILE: Manda al STDIN de command_1 el contenido de FILE.

## redirecci�n de salida

- command > FILE - manda el STDOUT a FILE
- command 1> FILE 2>FILE_ERROR - manda el STDOUT a FILE y el STDERR a
FILE_ERROR
- command > FILE 2>&1 - manda, tanto el STDOUT como el STDERR a FILE
- command >> FILE 2>&1 - manda a concatenar las salidas de STDOUT y STDERR a FILE

# Combinaci�n de teclas como comando

- [ctrl]-C - este comando termina el proceso que se est� ejecutando en la terminal, haya o noacabado de ejecutarse.
- [ctrl]-D - el sistema lo interpreta como _EOF_ (End Of File) y cierra el _stream_ de entrada(STDIN) para un archivo en donde se est� escribiendo desde la termina.

## Show files in directory

- ls: list files in a directory.
- ls -l: lista los archivos con datos de cada nodo, ordenados alfab�ticament. Muestra toda la informaci�n: usuario, grupo, permisos, tama�o, fecha y hora de creaci�n.
- ls -lS: lista los contenidos ordenados por tama�o.
- ls -lh: lista los contenidos mostrando los datos legibles f�cilmente (tama�o).
- ls -r: lista los archivos ordenados de forma inversa (sirve con las banderas S y `t`).
- ls -a: lista los contenidos de un directorio incluyendo los archivos oculto.
- ls -t: Ordena los archivos por fecha de modificaci�n.
- ls -x: Ordena los archivos por extensi�n.
- ls -R: Muestra el contenido de todos los subdirectorios de forma recursiva.
- ls -S: Ordena los resultados por tama�o de archivo.

- tree lista recursivamente la estructura de �rbol de un directorio incluyendo tanto archivoscomo directorios (**NOTA:** No viene pre-instalado as� que hay que instalarlo primero con suadministrador de paquetes preferido: para RHEL/CentOS/Fedora yum install tree paraDebian/Mint/Ubuntu apt-get install tree, para OS X `brew install tree`
- tree -L 1: muestra recursivamente la estructura de árbol de un directorio pero sólo hasta elprimer subnivel de directorios
- tree -a: muestra recursivamente la estructura de árbol de un directorio incluyendo tantoarchivos como directorio ocultos
- tree -d: muestra recursivamente la estructura de árbol de un directorio tomando en cuentasólo los directorios
- tree -dL 1: muestra recursivamente la estructura de árbol de un directorio tomando en cuentasólo los directorios y hasta el primer subnivel

# Remove files and directories

- rm [FILE]: elimina un archivo
- rm -rf [DIRECTORY]: elimina un directorio recursivamente sin preguntar

# Move files

- mv [FILE] [DIRECTORY]: mueve FILE a DIRECTORY
- mv [FILE] [NAME]: renombra FILE a NAME

# Change directory

- cd [DIRECTORY]: lleva el PROMPT a DIRECTORY

# Create file

- touch [FILE]: si FILE existe, modifica la hora de �ltima modificaci�n al momento de  ejecuci�n del comando, si FILE no existe, lo crea.

# Link

- ln -s [DIRECTORY] [NAME]: crea un _link_ simb�lico llamado NAME hacia DIRECTORY NAME se comporatarácomo DIRECTORY

# Clear screen

- clear:limpia la terminal

# Show path

- pwd: imprime o muestra la ruta actual donde nos encontramos ubicados

# Manual

- man [COMANDO]: muestra la documentacion de todos los comandos

# Make dir

- mkdir [DIRECTORY]: crea un directorio en la ubicación actual
- mkdir -p [RUTA]: crea un árbol de directorios completo que no existe

# Copy files and directories

- cp [archivo/directorio origen] [archivo/directorio destino]: copia un archivo o directorio desdeun origen a un destino
- cp -r [directorio origen] [directorio destino]: copia un directorio y todos sus directorios hijos deforma recursiva

# Open files

- open [-a APP] [ FILE | DIRECTORY ]: abre el (archivo o directorio) con la aplicación pordefecto en elsistema operativo, si se manda la bandera -a usará la APP para abrirl

# Crontab

- crontab -l: enlista las tarea programadas.
- crontab -e: editar el archivo de crontab.
- sudo service cron start

# at

- at now +2 minutes: ejecutar algo en dos minutos.
- sudo service atd start

# du

- du: desk usage, cu�nto ocupa cada uno de los nodos que se est�n utilizando
- du -h deepth: du -h 1, la profundidad es 1. tambi�n se puede presentar cómo: du -h --maxdepth=, du -h d 1

# Text files

# head

- head [FILE]: show first 10 lines of a text file.
- head -n5 [FILE]: show first 5 lines of a text file.

# tail

- tail [FILE]: show last 10 lines of a text file.
- tail -f [FILE]: tail forever, show 10 last lines, but not close de file, so show the last changes in that file. 
- tail -n5: show las 5 lines of a text file.

# more

- more [FILE]: more is a filter for paging through text one screenful at a time.  This version is especially primitive.  Users  should  realize  that  less(1) provides more(1) emulation plus extensive enhancements.

# less

- less [FILE]: Less is a program similar to more (1), but it has many  more  features. Less  does  not  have to read the entire input file before starting, so with large input files it starts up faster than text  editors  like  vi(1).  Less uses termcap (or terminfo on some systems), so it can run on a variety of terminals.  There is even  limited  support  for  hardcopy terminals.   (On  a hardcopy terminal, lines which should be printed at the top of the screen are prefixed with a caret.)

# cat

- cat [FILE]: Concatenate FILE(s) to standard output.

# sed (string editor)

**Modifica el flujo de datos no el contenido de su fuente.**

- sed -n 5p <file>:  You can get one specific line during any procedure. Very interesting to be used when you know what line you want.
- sed -n '3,6p' /path/to/file: Print all lines between two line numbers This command uses sed(1) to print all lines between two known line numbers in a file. Useful for seeing output in a log file, where the line numbers are known. The above command will print all lines between, and including, lines 3 and 6.
- sed '10,20!d': Print all the lines between 10 and 20 of a file.
- sed -n '5{p;q}' file: for lines 5 to 10.
- sed -n '10,$p' file: for lines 10 to last line.
- sed 's/expresion/expresion/g' [FILE]: sustituye una expresi�n por otra en un flujo de datos, quiere decir que no modifica el contenido del cual proviene el flujo. s indica la sustituci�n. g que se realice la acci�n a lo largo del texto.
sed '$d' [file]: delete last line. 

# grep

Find expressions in files or stdout.

- grep -rni [directory] -e "expresion": buscar en un directorio, recursivamente, una expresión en los archivos
- grep -rni "expresion" [directory/file]: search a expresi�n in file or directory. -i is for case insentisive. -r for recursive. -n show lines numbers. 
- grep -v expresion: excluir expresi�n buscada.

# awk

- awk -F ';' '{ print $1 }' [FILE.scv]: ';' indica un delimitador, '{ pirnt $1 }' selecciona la primera columna. El comando imprimer la primera columa de un archivo delimitado por ;
- awk -F ';' 'NR > 1 && $3 >0 { print $1, $3 * $4 }' [FILE.scv]: imprime despu�s de la l�nea 1, la columna 1 y en una segunda columna pone el producto de la dolumna 3 por la 4.
- awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -nr: ips que ingresan al sitio en nginx, organizadas y elimina las repetidas. 

# Find files

## find

### Syntax

- find <startingdirectory> <options> <search term>
    - <startingdirectory>: es el punto de origen de donde deseas iniciar la b�squeda.
    - <options>: filtro que deseas usar para buscar tu archivo.
    - <search term>: este tercer argumento es una continuaci�n del segundo, donde se especificar� el t�rmino de b�squeda relevante. 

### By Name

- find directorio -name "expresion+wildcard" typo typoDeArchivo/f: buscar en un directorio, por el nombre de una expresi�n, en un archivo.
- fin [directorio] -type f : en el directorio seleccionado busca elementos tipo archivo.
- fin /var/log -name "\*.log" -type f: busca en la ruta todos los archivos que en su nombre tenga .log
- find /var/log -iname "\*.LOG" -type f: busca en la ruta todos los archivos que en su nombre tenga .log sin importar las may�sculas o min�sculas.
- find /var/log ! -iname "\*.LOG" -type f: todos los archivos que no tengan extensi�n .log.
- find _dir_ -not -iname "\*.LOG" -type f: como el anterior.
- fin _dir_ -name "_expression_" -delete: elimina el archivo encontrado.

### By Date Time

- find _dir_ -mtime 10: Encuentra archivos con cambios en los �ltimos 10 minutos.

- -atime: Tiempo de acceso. Fecha m�s reciente en que el archivo fue le�do o escrito, en d�as.
- -mtime: Tiempo de modificaci�n. Fecha m�s reciente en que se modific� el archivo.
- -ctime: Hora de cambio. Fecha m�s reciente en que se actualizaron los metadatos del archivo.

- find _dir_ -atime 1: encontrar� todos los archivos a los que se accedi� hace un d�a desde el momento actual. Esto significa que se listar�n todos los archivos que fueron le�dos y/o escritos desde el d�a anterior.
- find _dir_ -mtime +2: Podemos hacer que nuestras consultas sean m�s precisas con los signos m�s (+) y menos (�) precediendo al n�mero de d�as. Esto listar� todos los archivos que tienen un tiempo de modificaci�n de m�s de dos d�as.

- <time-descriptor>min: busca cu�ntos minutos han pasado
- find _dir_ -mmin -1: Esto buscar� archivos que se modificaron hace menos de un minuto. 

- -newer: se puede usar para comparar la antig�edad de dos archivos y encontrar el m�s reciente.

### By User and Permissions

- find _dir_ -user _user_ -perm _644_: busca archivos de un usuario con determinados permisos.
- find _dir_ -group _group_
- find _dir_ -perm -644: Esto mostrar� todos los archivos que tengan al menos el permiso 644.

### By Type

- find _dir_ -type [TYPE]: Busca por tipo de archivo:
    - f: archivo normal
    - d: directorio o carpeta
    - l: enlace simb�lico
    - c: dispositivos de caracteres
    - b: dispositivos de bloque
- find _dir_ -type f -mtime +7: busca elementos tipo file modificados hace m�s de 7 d�as.
- find _dir_ -type f -mtime +7 -exec cp {} _dirTarget_ \;
- find _dir_ -type f -name "_expresion_"
- find _dir_ -size [type]: buscar por tama�o
    - c: bytes
    - k: kilobytes
    - M: meabytes
    - b:trozos de 512 bytes
    - find ./ -size 200M: encuentra archivos de 200M
    - find ./ -size +200M: encuentra archivos de m�s de 200M
    - find ./ -size -200M:
    - find ./ -size200M -type f

### Exec

- find _dir_ -exec: buscar todos los ejecutables guardados en tu disco, utiliza la opci�n -exec.

### Read

- find _dir_ -read: buscar archivos legibles.

## Utils

- find _dir_ -empty: Buscar archivos y carpetas vac�os.

## Locate

- locate _file_: busca un archivo en el sistema de archivos, y funciona mediante una base de datos que debe ser actualizada.
    - sudo updatedb: actualiza la base de datos de archivos.
- locate -b _file_: Puedes usar el argumento -b para una b�squeda m�s espec�fica. Solo buscar� el �nombre base� del archivo, enumerando efectivamente solo los archivos que tienen el t�rmino de b�squeda en lugar de devolver los directorios que conducen a los archivos.
    - -e muestra entradas de archivos existentes en el momento en que se ejecuta el comando locate.
    - -q inhabilita la visualizaci�n de errores encontrados en el proceso de b�squeda.
    - -c muestra la cantidad de archivos que coinciden, en lugar de los nombres de los archivos.
- sudo updatedb: actualizar base de datos de archivos.

# whereis

- whereis: busca binaros, es decir, comandos.

# Sort files

- Write sorted concatenation of all FILE(s) to standard output.
- With no FILE, or when FILE is -, read standard input.
- sort [OPTION]... [FILE]...
- sort [OPTION]... --files0-from=F

# Uniques

- Filter  adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output). 
- With no options, matching lines are merged to the first occurrence.
- uniq [OPTION]... [INPUT [OUTPUT]]

# Send files

## rsync

- rsync -avz $(pwd) $user@$host:/home/quattroc/Descargas/transf

# Email

- echo "Mensaje" | mail -s "Asunto" email@email.com
