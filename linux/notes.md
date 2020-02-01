# Commands

- curl url -o filename: descargar un archivo

- zip nombre.zip archivos_a_comprimir: comprimir archivos en zip.

- unzip -vl archivo.zip: muestrar los archivos del zip.
- unzip archivo.zip: descomprimir archivo

- tar cfz nombre.tar.gz archivos_a_comprimir: comprimir archivos en tar
- tar xfz nombre.tar.gz

- 1>: stdout standart out
- 2>: stderr standar error
- 1>&2: redirigir ambas salidas al mismo lugar

## Show files in directory

- ls: list files in a directory.
- ls -l: lista los archivos con datos de cada nodo, ordenados alfabéticament. Muestra toda la información: usuario, grupo, permisos, tamaño, fecha y hora de creación.
- ls -lS: lista los contenidos ordenados por tamaño.
- ls -lh: lista los contenidos mostrando los datos legibles fácilmente (tamaño).
- ls -r: lista los archivos ordenados de forma inversa (sirve con las banderas S y `t`).
- ls -a: lista los contenidos de un directorio incluyendo los archivos oculto.
- ls -t: Ordena los archivos por fecha de modificación.
- ls -x: Ordena los archivos por extensión.
- ls -R: Muestra el contenido de todos los subdirectorios de forma recursiva.
- ls -S: Ordena los resultados por tamaño de archivo.

- tree lista recursivamente la estructura de árbol de un directorio incluyendo tanto archivoscomo directorios (**NOTA:** No viene pre-instalado así­ que hay que instalarlo primero con suadministrador de paquetes preferido: para RHEL/CentOS/Fedora yum install tree paraDebian/Mint/Ubuntu apt-get install tree, para OS X `brew install tree`
- tree -L 1: muestra recursivamente la estructura de Ã¡rbol de un directorio pero sÃ³lo hasta elprimer subnivel de directorios
- tree -a: muestra recursivamente la estructura de Ã¡rbol de un directorio incluyendo tantoarchivos como directorio ocultos
- tree -d: muestra recursivamente la estructura de Ã¡rbol de un directorio tomando en cuentasÃ³lo los directorios
- tree -dL 1: muestra recursivamente la estructura de Ã¡rbol de un directorio tomando en cuentasÃ³lo los directorios y hasta el primer subnivel

# Remove files and directories

- rm [FILE]: elimina un archivo
- rm -rf [DIRECTORY]: elimina un directorio recursivamente sin preguntar

# Move files

- mv [FILE] [DIRECTORY]: mueve FILE a DIRECTORY
- mv [FILE] [NAME]: renombra FILE a NAME

# Change directory

- cd [DIRECTORY]: lleva el PROMPT a DIRECTORY

# Create file

- touch [FILE]: si FILE existe, modifica la hora de última modificación al momento de  ejecución del comando, si FILE no existe, lo crea.

# Link

- ln -s [DIRECTORY] [NAME]: crea un _link_ simbólico llamado NAME hacia DIRECTORY NAME se comporatarÃ¡como DIRECTORY

# Clear screen

- clear:limpia la terminal

# Show path

- pwd: imprime o muestra la ruta actual donde nos encontramos ubicados

# Manual

- man [COMANDO]: muestra la documentacion de todos los comandos

# Make dir

- mkdir [DIRECTORY]: crea un directorio en la ubicaciÃ³n actual
- mkdir -p [RUTA]: crea un Ã¡rbol de directorios completo que no existe

# Copy files and directories

- cp [archivo/directorio origen] [archivo/directorio destino]: copia un archivo o directorio desdeun origen a un destino
- cp -r [directorio origen] [directorio destino]: copia un directorio y todos sus directorios hijos deforma recursiva

# Open files

- open [-a APP] [ FILE | DIRECTORY ]: abre el (archivo o directorio) con la aplicaciÃ³n pordefecto en elsistema operativo, si se manda la bandera -a usarÃ¡ la APP para abrirl

# Operators

## operador | (pipe):

- command_1 | command_2: Manda el STDOUT de command_1 al STDIN de command_2

## operador >

- command_1 > FILE: Manda el STDOUT de command_1 al inicio de FILE. Si FILE no existe lo crea, si existe losobreescribe.

## operador >>

- command_1 >> FILE: Manda el STDOUT de command_1 al inicio de FILE. Si FILE no existe lo crea, si existe lo concatena al final(tras un _newline_).

## operador <

command_1 < FILE: Manda al STDIN de command_1 el contenido de FILE.

## redirección de salida

- command > FILE - manda el STDOUT a FILE
- command 1> FILE 2>FILE_ERROR - manda el STDOUT a FILE y el STDERR a
FILE_ERROR
- command > FILE 2>&1 - manda, tanto el STDOUT como el STDERR a FILE
- command >> FILE 2>&1 - manda a concatenar las salidas de STDOUT y STDERR a FILE

# Combinación de teclas como comando

- [ctrl]-C - este comando termina el proceso que se está ejecutando en la terminal, haya o noacabado de ejecutarse.
- [ctrl]-D - el sistema lo interpreta como _EOF_ (End Of File) y cierra el _stream_ de entrada(STDIN) para un archivo en donde se está escribiendo desde la termina.

# Crontab

- crontab -l: enlista las tarea programadas.
- crontab -e: editar el archivo de crontab.

# du

- du: desk usage, cuánto ocupa cada uno de los nodos que se están utilizando
- du -h deepth: du -h 1, la profundidad es 1. tambiÃn se puede presentar cÃ³mo: du -h --maxdepth=, du -h d 1

# Text files

## head

- head [FILE]: show first 10 lines of a text file.
- head -n5 [FILE]: show first 5 lines of a text file.

## tail

- tail [FILE]: show last 10 lines of a text file.
- tail -f [FILE]: tail forever, show 10 last lines, but not close de file, so show the last changes in that file. 
- tail -n5: show las 5 lines of a text file.

## more

- more [FILE]: more is a filter for paging through text one screenful at a time.  This version is especially primitive.  Users  should  realize  that  less(1) provides more(1) emulation plus extensive enhancements.

## less

- less [FILE]: Less is a program similar to more (1), but it has many  more  features. Less  does  not  have to read the entire input file before starting, so with large input files it starts up faster than text  editors  like  vi(1).  Less uses termcap (or terminfo on some systems), so it can run on a variety of terminals.  There is even  limited  support  for  hardcopy terminals.   (On  a hardcopy terminal, lines which should be printed at the top of the screen are prefixed with a caret.)

## cat

- cat [FILE]: Concatenate FILE(s) to standard output.

## sed (string editor)

**Modifica el flujo de datos no el contenido de su fuente.**

- sed -n 5p <file>:  You can get one specific line during any procedure. Very interesting to be used when you know what line you want.
- sed -n '3,6p' /path/to/file: Print all lines between two line numbers This command uses sed(1) to print all lines between two known line numbers in a file. Useful for seeing output in a log file, where the line numbers are known. The above command will print all lines between, and including, lines 3 and 6.
- sed '10,20!d': Print all the lines between 10 and 20 of a file.
- sed -n '5{p;q}' file: for lines 5 to 10.
- sed -n '10,$p' file: for lines 10 to last line.
- sed 's/expresion/expresion/g' [FILE]: sustituye una expresión por otra en un flujo de datos, quiere decir que no modifica el contenido del cual proviene el flujo. s indica la sustitución. g que se realice la acción a lo largo del texto.
sed '$d' [file]: delete last line. 

## grep

- grep -rni [directory] -e "expresion": buscar en un directorio, recursivamente, una expresiÃ³n en los archivos
- grep -rni "expresion" [directory/file]: search a expresión in file or directory. -i is for case insentisive. -r for recursive. -n show lines numbers. 
- grep -v expresion: excluir expresión buscada.

## awk

- awk -F ';' '{ print $1 }' [FILE.scv]: ';' indica un delimitador, '{ pirnt $1 }' selecciona la primera columna. El comando imprimer la primera columa de un archivo delimitado por ;
awk -F ';' 'NR > 1 && $3 >0 { print $1, $3 * $4 }' [FILE.scv]: imprime después de la línea 1, la columna 1 y en una segunda columna pone el producto de la dolumna 3 por la 4.

# Find files

## find

- find directorio -name "expresion+wildcard" typo typoDeArchivo/f: buscar en un directorio, por el nombre de una expresión, en un archivo.
- fin [directorio] -type f : en el directorio seleccionado busca elementos tipo archivo.
- fin /var/log -name "*.log" -type f: busca en la ruta todos los archivos que en su nombre tenga .log
- find /var/log -iname "*.LOG" -type f: busca en la ruta todos los archivos que en su nombre tenga .log sin importar las mayúsculas o minúsculas.
- find /var/log ! -iname "*.LOG" -type f: todos los archivos que no tengan extensión .log.

