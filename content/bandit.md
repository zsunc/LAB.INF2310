## Bandit

![bandit](/images/banditotw.png)  

### • Nivel 0 → Nivel 1  
> user: bandit0  
password: bandit0  
ssh: bandit0@bandit.labs.overthewire.org -p 2220  

Para ingresar nos conectaremos al servidor a través de una terminal de Linux (o de Powershell en Windows), en este caso, voy a utilizar un sistema operativo Linux con su interfaz de línea de comandos (shell).  
Luego, usaremos el comando `ssh` para conectarnos al servidor con el usuario **bandit0** en el puerto 2220, con esto establecemos una conexión remota segura con el servidor:
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
una vez dentro nos pedira la contraseña que es *bandit0*, si la contraseña es correcta ya deberiamos estar como usuarios y en la terminal estaremos como:  
```
bandit0@bandit:~$
```
Con esto empezamos usando un comando `ls` con el cual vemos que hay un archivo *readme*, en el cual se encuentra la contraseña para el siguiente nivel, la cual preferentemente guardaremos en un archivo de texto.  
```
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
"The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If"
```
### • Nivel 1 → Nivel 2  
> user: bandit1  
password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If  
ssh: bandit1@bandit.labs.overthewire.org -p 2220  

Ahora cambiaremos usuario al **bandit1** para iniciar sesion, y pondremos la contraseña que ya obtenimos.  
Al iniciar la sesion primero vemos el directorio */home/* y al hacerle `ls` vemos que hay un directorio *bandit1*
que dentro tiene un texto ASCII, entonces vamos a abrirlo con el comando `cat` y asi obtenemos la contraseña para el siguiente nivel.  
```
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cd /home/
bandit1@bandit:/home$ ls
bandit0   bandit2       bandit29      bandit7    drifter4     krypton1
bandit1   bandit20      bandit29-git  bandit8    drifter5     krypton2
bandit1@bandit:/home$ cat /home/bandit1/-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
### • Nivel 2 → Nivel 3
> user: bandit2  
password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx  
ssh: bandit2@bandit.labs.overthewire.org -p 2220  

Para este nivel ingresamos con el usuario "bandit2", al ingresar y hacer `ls` vemos un archivo *spaces in this filename*, en Linux si un archivo tiene espacios en su nombre, necesitamos escapar estos espacios o usar comillas.  
Con eso obtendriamos la contraseña para el siguiente nivel.  
```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
### • Nivel 3 → Nivel 4
> user: bandit3  
password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx  
ssh: bandit3@bandit.labs.overthewire.org -p 2220  

Al iniciar sesion podremos ver que si hacemos `ls` vemos un directorio *inhere*, en el cual hay archivos ocultos entonces hacemos `ls -la` y nos encontramos con un documento llamado *Hiding-From-You*, entonces accedemos al documento y obtenemos la contraseña para el siguiente nivel.  
```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Sep 19  2024 .
-rw-r----- 1 bandit4 bandit3   33 Sep 19  2024 ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
### • Nivel 4 → Nivel 5
> user: bandit4  
password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ  
ssh: bandit4@bandit.labs.overthewire.org -p 2220  

En este nivel al dinamica es la misma al anterior nivel, pero en esta vez habra que buscar en varios directorios, pero el correcto termina siendo el *file07*.  
Obteniendo asi la contraseña para el siguiente nivel.  
```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ cat /home/bandit4/inhere/-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
### • Nivel 5 → Nivel 6 
> user: bandit5  
password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw  
ssh: bandit5@bandit.labs.overthewire.org -p 2220  

Para este nivel el desafio se mantiene en los directorios variados donde tenemos que encontrar el directorio correcto, por ahora en esta ocacion tambien lo encontramos en un directorio `maybehere07/.file2`.  
Con eso encontramos la contraseña para el proximo nivel  
```
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere05  maybehere10  maybehere15
maybehere01  maybehere06  maybehere11  maybehere16
maybehere02  maybehere07  maybehere12  maybehere17
bandit5@bandit:~/inhere$ cd maybehere07/
bandit5@bandit:~/inhere/maybehere07$ ls -la
total 56
drwxr-x---  2 root bandit5 4096 Sep 19  2024 .
drwxr-x--- 22 root bandit5 4096 Sep 19  2024 ..
-rw-r-----  1 root bandit5 2488 Sep 19  2024 -file2
-rw-r-----  1 root bandit5 1033 Sep 19  2024 .file2
bandit5@bandit:~/inhere/maybehere07$ cat .file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
### • Nivel 6 → Nivel 7
> user: bandit6  
password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG  
ssh: bandit6@bandit.labs.overthewire.org -p 2220  

Para este nivel al iniciar sesion, realizaremos la misma busqueda en */home/*, tambien tendremos que buscar con un `ls` y asi poder buscar un archivo, al ver las pistas que ofrece la pagina para ayudarnos vemos esto:
- *owned by user bandit7*  
- *owned by group bandit6*  
- *33 bytes in size*  

Esta informacion la podemos usar como parametros con `find`y asi encontrar un archivo que llame nuestra atencion.  
Al revisar veremos varios directorios a los cuales tenemos el acceso negado, revisando veremos un directorio con un archivo *bandit7.password*, en el cual si hacemos `cat`, obtendriamos la contraseña para el siguiente nivel.  
```
bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6
find: ‘/drifter/drifter14_src/axTLS’: Permission denied
find: ‘/root’: Permission denied
find: ‘/snap’: Permission denied
find: ‘/var/lib/amazon’: Permission denied
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```   
###  • Nivel 7 → Nivel 8  
 > user: bandit7  
password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj  
ssh: bandit7@bandit.labs.overthewire.org -p 2220  

Para este nivel al iniciar la sesion y hacer `ls` podremos ver un documento *data.txt*.  
En la pagina podremos ver esto:  
- *The password for the next level is stored in the file data.txt next to the word "millionth"*  

En este caso tambien usaremos la palabra millionth como un parametro con el comando `grep`, ya que al ver el *data.txt*, vemos una lista de usuarios con sus contraseñas.

```
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep 'millionth' data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
###  • Nivel 8 → Nivel 9  
> user: bandit8  
password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc  
ssh: bandit8@bandit.labs.overthewire.org -p 2220   

Para este nivel, veremos un texto *data.txt*, como en el anterior nivel pero esta vez son puramente contraseñas y en la pagina se especifica que la contraseña para el siguiente nivel no se repite, con este dato, usaremos un comando `cat`, para abrir el *data.txt*, luego con `sort` ordenamos la lista del documento y poder usar `uniq -u` para encontrar la unica contraseña que no se repite.  
```
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ cat data.txt | sort | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
###  • Nivel 9 → Nivel 10 
> user: bandit9  
password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM  
ssh: bandit9@bandit.labs.overthewire.org -p 2220  

Para este nivel, en las indicaciones de la pagina nos menciona: *"preceded by several ‘=’ characters".*, esto nos da a entender que antes de la contraseña hay varios "=" agrupados, hacer `cat` al *data.txt* veremos que esta cifrado, para eso usamos `strings`, ahora vemos que el texto es mas legible, entonces usamos `grep '='` para buscar lineas de texto con el "=".
```
bandit9@bandit:~$ strings data.txt | grep '='
}========== the
3JprD========== passwordi
qC(=
~fDV3========== is
=tZ~07
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
N=~[!N
```
###  • Nivel 10 → Nivel 11  
> user: bandit10  
password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey  
ssh: bandit10@bandit.labs.overthewire.org -p 2220  

En este nivel vemos que el archivo *data.txt* se encuentra con un codificado base64, para lo cual usaremos el comando `base64 -d` para poder ver el contenido del documento.  
```
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
###  • Nivel 11 → Nivel 12  
> user: bandit11  
password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr  
ssh: bandit11@bandit.labs.overthewire.org -p 2220  

En este nivel nos deja que *s*, esto nos da a entender que esta con un cifrado ROT13, para eso usaremos `tr` con `A-Za-z` que son todas las letras mayusculas y minusaculas, `N-ZA-Mn-za-m` y con esto rotamos los 13 lugares.  
```
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
bandit11@bandit:~$ cat data.txt | tr A-Za-z N-ZA-Mn-za-m
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
###  • Nivel 12 → Nivel 13  
> user: bandit12  
password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4  
ssh: bandit12@bandit.labs.overthewire.org -p 2220  

Para este nivel crearemos un directorio `/tmp/tmp.zsc`, al cual copiaremos el *data.txt*, sabemos que es un volcado hexadecimal asi que primero sera revertirlo, para eso lo renombramos como *hex_data.hex*, seguido podemos usar el comando `xxd` con el `-r` para revertilo cambiandole el nombre a *comp_data*.  
```
bandit12@bandit:~$ mkdir /tmp/tmp.zsc
bandit12@bandit:~$ cp data.txt /tmp/tmp.zsc/data.txt
bandit12@bandit:~$ cd /tmp/tmp.zsc
bandit12@bandit:/tmp/tmp.zsc$ ls
data.txt
bandit12@bandit:/tmp/tmp.zsc$ mv data.txt hex_data
bandit12@bandit:/tmp/tmp.zsc$ xxd -r hex_data comp_data
```
Al ver el tipo de archivo que es vemos un comprimido *gzip*, entonces le cambiaremos el nombre para luego descomprimirlo con `gzip -d`. 
```
bandit12@bandit:/tmp/tmp.zsc$ file comp_data
comp_data: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
bandit12@bandit:/tmp/tmp.zsc$ mv comp_data gz_data.gz
bandit12@bandit:/tmp/tmp.zsc$ ls
gz_data.gz  hex_data
bandit12@bandit:/tmp/tmp.zsc$ gzip -d gz_data.gz
bandit12@bandit:/tmp/tmp.zsc$ ls
gz_data  hex_data
```
Una vez descomprimido podremos ver que nos dejo otro archivo, si vemos us tipo es un comprimido *bzip2*, repetimos los pasos anteriores para este archivo y descomprimimos con `bzip2 -d`.
```
bandit12@bandit:/tmp/tmp.zsc$ file gz_data
gz_data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.zsc$ mv gz_data b2_data.bz2
bandit12@bandit:/tmp/tmp.zsc$ bzip2 -d b2_data.bz2
bandit12@bandit:/tmp/tmp.zsc$ ls
b2_data  hex_data
```
Ahora nos queda un archivo *gzip*, entonces repetimos los anteriores pasos.
```
bandit12@bandit:/tmp/tmp.zsc$ file b2_data
b2_data: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/tmp.zsc$ mv b2_data gz_data.gz
bandit12@bandit:/tmp/tmp.zsc$ gzip -d gz_data.gz
bandit12@bandit:/tmp/tmp.zsc$ ls
gz_data  hex_data
```
Ahora nos queda un archivo tar asi que renombraremos y usaremos `tar -xf` para poder extraer el contenido.  
```
bandit12@bandit:/tmp/tmp.zsc$ file gz_data
gz_data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.zsc$ mv gz_data tar_data.tar
bandit12@bandit:/tmp/tmp.zsc$ tar -xf tar_data.tar
bandit12@bandit:/tmp/tmp.zsc$ ls
data5.bin  hex_data  tar_data.tar
```
Repetimos los pasos anteriores con el archivo *data5.bin*, que se encontraba dentro del *.tar*.
```
bandit12@bandit:/tmp/tmp.zsc$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.zsc$ tar -xf data5.bin
bandit12@bandit:/tmp/tmp.zsc$ ls
data5.bin  data6.bin  hex_data  tar_data.tar
```
Ahora volvemos a un comprimido *bzip2*, pero esta vez lo descomprimimos sin cambiarle la extension.

```
bandit12@bandit:/tmp/tmp.zsc$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.zsc$ ls
data5.bin  data6.bin  hex_data  tar_data.tar
bandit12@bandit:/tmp/tmp.zsc$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
```
Esto nos dejara con un *data6.bin.out*, que si le hacemos `file` veremos que es un archivo *tar*, entonces procedemos a descomprimirlo.

```
bandit12@bandit:/tmp/tmp.zsc$ ls
data5.bin  data6.bin.out  hex_data  tar_data.tar
bandit12@bandit:/tmp/tmp.zsc$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.zsc$ tar -xf data6.bin.out
```
Veremos que nos deja un archivo *data8.bin*, que si vemos el tipo de archivo, es un comprimido *gzip*, entonces procedemos a cambiarle la extension y descomprimirlo.

```
bandit12@bandit:/tmp/tmp.zsc$ ls
data5.bin  data6.bin.out  data8.bin  hex_data  tar_data.tar
bandit12@bandit:/tmp/tmp.zsc$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/tmp.zsc$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.zsc$ gzip -d data8.gz
```
Finalmente nos deja un archivo *data8*, que si lo abrimos con `cat` encontramos la contrasenia para el siguiente nivel.  
```
bandit12@bandit:/tmp/tmp.zsc$ ls
data5.bin  data6.bin.out  data8  hex_data  tar_data.tar
bandit12@bandit:/tmp/tmp.zsc$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```
###  • Nivel 13 → Nivel 14  
> user: bandit13  
password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn  
ssh: bandit13@bandit.labs.overthewire.org -p 2220  

Para....



 
###  • Nivel  → Nivel  
###  • Nivel  → Nivel  


*investigando las respuestas...*  
![espera](/images/sherlock.gif)



[//]: # ( > user: bandit  
password: -  
ssh: bandit@bandit.labs.overthewire.org -p 2220  
)


<br>`03/04 | v.1.0`