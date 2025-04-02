## Bandit
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




###  • Nivel  → Nivel  
###  • Nivel  → Nivel  
###  • Nivel  → Nivel  
###  • Nivel  → Nivel  




[//]: # ( > user: bandit  
password: -  
ssh: bandit@bandit.labs.overthewire.org -p 2220  
)


<br>`02/04 | v.1.0`