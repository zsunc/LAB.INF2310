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
Finalmente nos deja un archivo *data8*, que si lo abrimos con `cat` encontramos la contraseña para el siguiente nivel.  
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

Para este nivel, tendremos que entrar como el usuario bandit14 para poder encontrar la contraseña, para eso usaremos la *sshkey.private* en un localhost con `-i` para poder usar la *sshkey.private*, una vez dentro revisamos */etc/bandit_pass/bandit14*, para la contraseña del siguiente nivel.
```
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p2220
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
###  • Nivel 14 → Nivel 15  
> user: bandit14  
password: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS  
ssh: bandit14@bandit.labs.overthewire.org -p 2220  

Para este nivel tendremos que enviar la contraseña del nivel actual a un puerto *30000* en un *localhost* con `nc` para poder escuchar al servidor, donde escribiremos la contraseña y si es correcta deberia devolvernos la contraseña para el siguiente nivel.
```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```
###  • Nivel 15 → Nivel 16
> user: bandit15  
password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo  
ssh: bandit15@bandit.labs.overthewire.org -p 2220  

Para este nivel se debe recuperar la contraseñapara el siguiente nivel mediante un cifrado SSL, para lo cual nos conectaremos al servidor local con `openssl s_client`, le enviamos la contraseña, y me devuelve la contraseña para el siguiente nivel.
```
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
```
###  • Nivel 16 → Nivel 17  
> user: bandit16  
password: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx  
ssh: bandit16@bandit.labs.overthewire.org -p 2220  

Para este nivel tenemos 
que enviar la contrasena del nivel actual a un puerto del host local en el rango de 31000 - 32000, para eso tenemos que encontrar los puertos abiertos en un host, para eso usaremos `nmap` que nos ayudara en el descubrimiento de host, y con `-sT` intentamos hacer una conexion con cada puerto.  
```
bandit16@bandit:~$ nmap -sT localhost -p 31000-32000
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-04-17 19:15 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00023s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds
```
Con esto, `nmap` nos indica que hay 5 puertos abiertos, hacemos `echo` de la contrasena del nivel actual y con el `openssl`nos conectamos a un puerto y vemos cual nos da respuesta, con el `-quiet` evitamos que `openssl` muestre informacion adicional.
```
 echo kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx | openssl s_client -quiet -connect localhost:31790
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```
En nuestro caso el puerto 31790 nos da una llave como en el nivel 13, para eso nos crearemos un directorio para guardar la llave con `nano` bajo el nombre de *sshkey*.
```
bandit16@bandit:~$ mkdir /tmp/zsc-16
bandit16@bandit:~$ cd /tmp/zsc-16
bandit16@bandit:/tmp/zsc-16$  nano sshkey
bandit16@bandit:/tmp/zsc-16$ ls
sshkey
```
para poder conectarnos tenemos que darle permisos de lectura y escritura al propietario para lo cual usaremos `chmod 600` en el *sshkey*, luego para conectarnos usaremos `-oHosKeyAlgorithms=+ssh-dss` para usar el algoritmo `ssh-dss`, que por defecto esta deshabilitado, y ponemos como identificador el *sshkey*.
```
bandit16@bandit:/tmp/zsc-16$ chmod 600 sshkey
bandit16@bandit:/tmp/zsc-16$ ssh -oHostKeyAlgorithms=+ssh-dss -i sshkey bandit17@localhost -p 2220
```
Una vez dentro nos iremos al directorio */etc/bandit_pass/*, y veremos con `cat` *bandit17*, en la cual se encuentra la contrasena para el siguiente nivel.  
```
bandit17@bandit:~$ cd /etc/bandit_pass/
bandit17@bandit:/etc/bandit_pass$ ls
bandit0   bandit13  bandit18  bandit22  bandit27  bandit31  bandit6
bandit1   bandit14  bandit19  bandit23  bandit28  bandit32  bandit7
bandit10  bandit15  bandit2   bandit24  bandit29  bandit33  bandit8
bandit11  bandit16  bandit20  bandit25  bandit3   bandit4   bandit9
bandit12  bandit17  bandit21  bandit26  bandit30  bandit5
bandit17@bandit:/etc/bandit_pass$ cat bandit17
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
```
###  • Nivel 17 → Nivel 18
> user: bandit17  
password: EReVavePLFHtFlFsjn3hyzMlvSuSAcRD  
ssh: bandit17@bandit.labs.overthewire.org -p 2220

En este nivel hay 2 archivos en el directorio de inicio *passwords.old* y *passwords.new*, la contraseña para el siguiente nivel se encuentra en *passwords.new* y es la única línea que se ha modificado entre *passwords.old* y *passwords.new*, para eso usaremos `diff` para ver la diferencia entre los dos archivos.
```
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< C6XNBdYOkgt5ARXESMKWWOUwBeaIQZ0Y
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```
Como escribí *passwords.new* en segundo lugar, la contraseña también se imprime en la segunda parte.  
###  • Nivel 18 → Nivel 19
> user: bandit18  
password: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO  
ssh: bandit@bandit.labs.overthewire.org -p 2220  

En este nivel al iniciar normalmente nos cierra la sesion, pero si al final de toda la linea del ssh ponemos un comando pj. `cat`, podremos ver el readme que contiene la contraseña del siguiente nivel.
```
$ ssh bandit18@bandit.labs.overthewire.org -p 2220 ls
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames
bandit18@bandit.labs.overthewire.org's password:
readme

$ ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
bandit18@bandit.labs.overthewire.org's password:
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```
###  • Nivel 19 → Nivel 20
> user: bandit19  
password: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8  
ssh: bandit19@bandit.labs.overthewire.org -p 2220  

Para acceder al siguiente nivel, debemos utilizar el binario `setuid` en el directorio de inicio, asi despues entramos a la carpeta */etc/bandi_pass/* y encontramos la contraseña.
```
bandit19@bandit:~$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Apr 10 14:23 .
drwxr-xr-x 70 root     root      4096 Apr 10 14:24 ..
-rwsr-x---  1 bandit20 bandit19 14884 Apr 10 14:23 bandit20-do
-rw-r--r--  1 root     root       220 Mar 31  2024 .bash_logout
bandit19@bandit:~$ ./bandit20-do ls /etc/bandit_pass
bandit0   bandit13  bandit18  bandit22  bandit27  bandit31  bandit6
bandit1   bandit14  bandit19  bandit23  bandit28  bandit32  bandit7
bandit10  bandit15  bandit2   bandit24  bandit29  bandit33  bandit8
bandit11  bandit16  bandit20  bandit25  bandit3   bandit4   bandit9
bandit12  bandit17  bandit21  bandit26  bandit30  bandit5
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```
###  • Nivel 20 → Nivel 21
> user: bandit20  
password: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO  
ssh: bandit20@bandit.labs.overthewire.org -p 2220  

En este nivel usaremos `netcat` creamos una conexión en modo servidor, que escucha las conexiones entrantes, para que netcat mande la contraseña usamos `echo` y con `-n` nos evitamos caracteres de nueva línea en la entrada y dejamos que el proceso se ejecute en segundo plano con `&`, despues ejecutamos el binario con el puerto *1234* asi entonces recibira la contraseña enviada con `echo` y nos devolveria la pass para el siguiente nivel.
```
bandit20@bandit:~$ echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234 &
[1] 474002
bandit20@bandit:~$ ./suconnect 1234
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234
```
###  • Nivel 21 → Nivel 22
> user: bandit21  
password: EeoULMCra2q0dSkYj561DX7s1CpBuOBt  
ssh: bandit21@bandit.labs.overthewire.org -p 2220  

En este nivel tenemos que buscar el programa se ejecuta automáticamente a intervalos regulares desde cron, para eso accederemos al directorio */etc/crond.d/*, y miraremos el archivo *cronjob_bandit22*, en el cual nos muestra un directorio con un *.sh* que si lo ponemos en la consola nos mostrara otro directorio, al cual si hacemos `cat` podremos ver la contraseña para el siguiente nivel.
```
bandit21@bandit:~$ cd /etc/cron.d
bandit21@bandit:/etc/cron.d$ ls
clean_tmp         cronjob_bandit23  e2scrub_all  sysstat
cronjob_bandit22  cronjob_bandit24  otw-tmp-dir
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:/etc/cron.d$ /usr/bin/cronjob_bandit22.sh
chmod: changing permissions of '/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv': Operation not permitted
/usr/bin/cronjob_bandit22.sh: line 3: /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv: Permission denied
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```
###  • Nivel 22 → Nivel 23
> user: bandit22  
password: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q  
ssh: bandit22@bandit.labs.overthewire.org -p 2220  

Para este nivel debemos ejecutar el script que se encuentra en */etc/cron.d/cronjob_bandit23*, en el cual en el script nos pedira una entrada que debemos identificarnos con el usuario *bandit23* el cual nos dara un directorio en el que se encuentra la contraseña para el siguiente nivel.
```
bandit22@bandit:~$ cd /etc/
bandit22@bandit:/etc$ ls
credstore               ld.so.conf.d                screenrc
credstore.encrypted     legal                       security
cron.d                  libaudit.conf               selinux
bandit22@bandit:/etc$ cd cron.d
bandit22@bandit:/etc/cron.d$ ls
clean_tmp         cronjob_bandit23  e2scrub_all  sysstat
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```
###  • Nivel 23 → Nivel 24
> user: bandit23  
password: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga  
ssh: bandit23@bandit.labs.overthewire.org -p 2220

Para este nivel antes crearemos una carpeta en */tmp/* para poder pasar la contraseña ya que el *cronjob* se ejecuta y elimina todos los archivos de la carpeta */var/spool/bandit24*, para eso crearemos un script para poder encontrar la contraseña para bandit24, que copiara desde la carpeta de las contraseñas y pasarlo al directorio que creamos, para eso le otorgaremos los permisos al archivo y al directorio.
```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/testzs/pass
```
Una vez copiado tendremos que esperar un momento para obtener la contraseña viendo el archivo simple que creamos *pass*.
```
bandit23@bandit:~$ cd /etc/cron.d/
bandit23@bandit:/etc/cron.d$ ls -l
total 28
-rw-r--r-- 1 root root 123 Apr 10 14:16 clean_tmp
-rw-r--r-- 1 root root 120 Apr 10 14:23 cronjob_bandit22
-rw-r--r-- 1 root root 122 Apr 10 14:23 cronjob_bandit23
-rw-r--r-- 1 root root 120 Apr 10 14:23 cronjob_bandit24
-rw-r--r-- 1 root root 201 Apr  8  2024 e2scrub_all
-rwx------ 1 root root  52 Apr 10 14:24 otw-tmp-dir
-rw-r--r-- 1 root root 396 Jan  9  2024 sysstat
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

bandit23@bandit:/etc/cron.d$ mkdir /tmp/testzs
bandit23@bandit:/etc/cron.d$ cd /tmp/testzs
bandit23@bandit:/tmp/testzs$ touch getx.sh
bandit23@bandit:/tmp/testzs$ touch pass
bandit23@bandit:/tmp/testzs$ chmod 777 /tmp/testzs
bandit23@bandit:/tmp/testzs$ chmod 755 getx.sh
bandit23@bandit:/tmp/testzs$ ls -la
total 592
drwxrwxrwx    2 bandit23 bandit23   4096 May  3 04:49 .
drwxrwx-wt 2292 root     root     593920 May  3 05:05 ..
-rwxr-xr-x    1 bandit23 root     61 May  3 04:49 getx.sh
-rwxrwxrwx    1 bandit23 bandit23      0 May  3 04:49 pass
bandit23@bandit:/tmp/testzs$ cp getx.sh /var/spool/bandit24/getx.sh
```
si todo esta correcto viendo el archivo simple encontraremos la contraseña.
```
bandit23@bandit:/tmp/testzs$ cat pass
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```
###  • Nivel 24 → Nivel 25 
> user: bandit24 
password: gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8  
ssh: bandit24@bandit.labs.overthewire.org -p 2220  

Para este nivel creammos un script con un rango especifico, tambien usaremos `netcat`.
```
#!/bin/bash
pass=gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
for i in {0000..9999}
do
echo $pass $i >> zsun25.txt
done
```
una vez configurado el script le damos los permisos de ejecucion y luego verificamos que se crearon los archivos, para luego escuchar el puerto local 30002, en el cual nos dara la contraseña para el siguiente nivel.
```
bandit24@bandit:/tmp$ mkdir zsun25
bandit24@bandit:/tmp$ cd zsun25
bandit24@bandit:/tmp/zsun25$ touch genp.sh
bandit24@bandit:/tmp/zsun25$ nano genp.sh
bandit24@bandit:/tmp/zsun25$ cat zsun25.txt | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct current password and pincode. Try again.
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```
###  • Nivel 25 → Nivel 26
> user: bandit25 
password: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4  
ssh: bandit25@bandit.labs.overthewire.org -p 2220

En este nivel se da un *bandit26.sshkey*, para poder ingresar mediante un localhost, pero con el comando *more* debemos hacer la ventana de la terminal del tamano mas reducido posible, una vez con `--More--` en la terminal, presionamos *h* para la ayuda seguido de *v* para entrar al editor, finalmente presionamos *:* para poder escribir `:set shell=/bin/bash` y aun dentro del editor ponemos `:shell`, con lo cual entramos como *bandit26*.
```
bandit25@bandit:~$ ls
bandit26.sshkey
bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost -p 2220
:shell
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
```
###  • Nivel 26 → Nivel 27  
> user: bandit26  
password: s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ  
ssh: bandit26@bandit.labs.overthewire.org -p 2220  

Para este nivel necesitamos estar logueados desde el nivel anterior, ya que si intentamos entrar normalmente nos cerrara la sesion, cuando vemos los archivos vemos un ejecutable, para lo cual lo usaremos para entrar al direcotrio donde estan las contraseñas y asi obtenemos la pass para el proximo nivel.
```
bandit26@bandit:~$ ls
bandit27-do  text.txt
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```
###  • Nivel 27 → Nivel 28 
> user: bandit27  
password: upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB  
ssh: bandit27@bandit.labs.overthewire.org -p 2220  

Para este nivel debemos copiar el repositorio que se especifica en la pagina, pero debemos especificar el puerto que usaremos, para eso añadiremos depues del localhost `:2220` especificando el puerto a usar.
```
bandit27@bandit:/tmp/zgit$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
Cloning into 'repo'...
bandit27@bandit:/tmp/zgit$ ls
repo
bandit27@bandit:/tmp/zgit$ cd repo
bandit27@bandit:/tmp/zgit/repo$ ls
README
bandit27@bandit:/tmp/zgit/repo$ cat README
The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```
###  • Nivel 28 → Nivel 29
> user: bandit28  
password: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN  
ssh: bandit28@bandit.labs.overthewire.org -p 2220  

Para este nivel igualmente copiaremos el repositorio de la pagina, al momento de tener el repositorio en el archivo markdown vemos que hay un usuario pero no la contraseña, para ver si hubo algun cambio veremos el *git log* y vemos que hay un *fix info leak*, por lo cual vamos por buen camino, copiaremos el codigo del commit para ver el contenido de ese commit, al ver el contenido vemos que ahi esta la contraseña.
```
bandit28@bandit:~$ mkdir /tmp/zgit28
bandit28@bandit:~$ cd /tmp/zgit28
bandit28@bandit:/tmp/zgit28$  git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
bandit28@bandit:/tmp/zgit28$ ls
repo
bandit28@bandit:/tmp/zgit28$ cd repo
bandit28@bandit:/tmp/zgit28/repo$ ls
README.md
bandit28@bandit:/tmp/zgit28/repo$ git log
commit 674690a00a0056ab96048f7317b9ec20c057c06b (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    fix info leak

commit fb0df1358b1ff146f581651a84bae622353a71c0
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    add missing data

commit a5fdc97aae2c6f0e6c1e722877a100f24bcaaa46
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    initial commit of README.md

bandit28@bandit:/tmp/zgit28/repo$ git show 674690a00a0056ab96048f7317b9ec20c057c06b
commit 674690a00a0056ab96048f7317b9ec20c057c06b (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Apr 10 14:23:19 2025 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials

 - username: bandit29
-- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
+- password: xxxxxxxxxx
```


###  • Nivel 29 → Nivel 30
> user: bandit29  
password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7  
ssh: bandit29@bandit.labs.overthewire.org -p 2220  

Para este nivel debemos cambiar de rama en la que estamos en el repositorio, si pasamos a *dev* y vemos el archivo markdown encontramos la contraseña para el siguiente nivel.
```
bandit29@bandit:~$ mkdir /tmp/zgit29
bandit29@bandit:~$ cd /tmp/zgit29
bandit29@bandit:/tmp/zgit29$ ls
bandit29@bandit:/tmp/zgit29$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
Cloning into 'repo'...
bandit29@bandit:/tmp/zgit29$ cd repo
bandit29@bandit:/tmp/zgit29/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/zgit29/repo$ git branch
* master
bandit29@bandit:/tmp/zgit29/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/zgit29/repo$ git checkout origin/dev
Note: switching to 'origin/dev'.
bandit29@bandit:/tmp/zgit29/repo$ ls -la
total 20
drwxrwxr-x 4 bandit29 bandit29 4096 May  3 07:16 .
drwxrwxr-x 3 bandit29 bandit29 4096 May  3 07:14 ..
drwxrwxr-x 2 bandit29 bandit29 4096 May  3 07:16 code
drwxrwxr-x 8 bandit29 bandit29 4096 May  3 07:16 .git
-rw-rw-r-- 1 bandit29 bandit29  134 May  3 07:16 README.md
bandit29@bandit:/tmp/zgit29/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```
###  • Nivel 30 → Nivel 31
> user: bandit30  
password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL  
ssh: bandit30@bandit.labs.overthewire.org -p 2220  

En este nivel de igual manera copiamos el repositorio, pero al ver el archivo markdown, no vemos algo prometedor, pero si vemos la etiqueta veremos un *secret* y lo descubrimos encontraremos la contraseña para el siguiente nivel.
```
bandit30@bandit:~$ mkdir /tmp/zgit30
bandit30@bandit:~$ cd /tmp/zgit30
bandit30@bandit:/tmp/zgit30$ git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
Cloning into 'repo'...
bandit30@bandit:/tmp/zgit30$ cd repo
bandit30@bandit:/tmp/zgit30/repo$ ls
README.md
bandit30@bandit:/tmp/zgit30/repo$ cat README.md
just an epmty file... muahaha
bandit30@bandit:/tmp/zgit30/repo$ git tag
secret
bandit30@bandit:/tmp/zgit30/repo$ git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```
###  • Nivel 31 → Nivel 32
> user: bandit31  
password: fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy  
ssh: bandit31@bandit.labs.overthewire.org -p 2220  

Para este nivel tambien copiamos el repositorio, al ver el markdown nos indica que debemos subir un archivo al repositorio, para eso creamos el archivo, una vez creado si lo intentamos subir el *.gitignore* no los permitira, para eso usaremos `git add` y lo subimos a la rama `origin master`.
```
bandit31@bandit:~$ mkdir /tmp/zgitt
bandit31@bandit:~$ cd /tmp/zgitt
bandit31@bandit:/tmp/zgitt$ git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
Cloning into 'repo'...
bandit31@bandit:/tmp/zgitt$ cd repo
bandit31@bandit:/tmp/zgitt/repo$ ls
README.md
bandit31@bandit:/tmp/zgitt/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/zgitt/repo$ git add -f key.txt
bandit31@bandit:/tmp/zgitt/repo$ git commit -m "a"
[master 8e2e0f4] a
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/zgitt/repo$ git push -u origin master
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost:2220/home/bandit31-git/repo
```
###  • Nivel 32 → Nivel 33 
> user: bandit32  
password: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K  
ssh: bandit32@bandit.labs.overthewire.org -p 2220  

Para este nivel nos encontramos un shell diferente, si usamos comandos normales, parece estar todo en mayuscula, para salir del shell en mayusculas usaremos `$0` y asi usamos comandos normalmente, si buscamos la carpeta de las contraseñas podremos encontrar la pass del siguiente nivel.
```
WELCOME TO THE UPPERCASE SHELL
>> $0
$ ls
uppershell
$ whoami
bandit33
$ cat /etc/bandit_pass/bandit33
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
$
```
###  • Nivel 33
> user: bandit33  
password: tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0  
ssh: bandit33@bandit.labs.overthewire.org -p 2220  

Se termino el juego.
```
bandit33@bandit:~$ ls
README.txt
bandit33@bandit:~$ cat README.txt
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
```

[//]: # ( GG )

<br>`ws 03.05`