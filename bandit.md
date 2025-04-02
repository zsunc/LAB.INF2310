## Bandit
### ¬ Nivel 0 -> Nivel 1  
> User: bandit0  
Password: bandit0  
SSH: bandit0@bandit.labs.overthewire.org -p 2220  

Para ingresar nos conectaremos al servidor a través de una terminal de Linux (o de Powershell en Windows), en este caso, voy a utilizar un sistema operativo Linux con su interfaz de línea de comandos (shell).  
Luego, usaremos el comando `ssh` para conectarnos al servidor con el usuario **bandit0** en el puerto 2220, con esto establecemos una conexión remota segura con el servidor:
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
una vez dentro nos pedira la contraseña que es *bandit0*, si la contraseña es correcta ya deberiamos estar como usuarios y en la terminal estaremos como:  
```
bandit0@bandit:~$
```
Con esto empezamos usando un comando `ls` con el cual vemos que hay un archivo "readme", en el cual se encuentra la contraseña para el siguiente nivel, la cual preferentemente guardaremos en un archivo de texto.  
```
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
"The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If"
```
### ¬ Nivel 1 -> Nivel 2  
> User: bandit1  
Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If  
SSH: bandit1@bandit.labs.overthewire.org -p 2220  

Ahora cambiaremos usuario al "bandit1" para iniciar sesion, y pondremos la contraseña que ya obtenimos.  
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
### ¬ Nivel 2 -> Nivel 3
> User: bandit2  
Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx  
SSH: bandit2@bandit.labs.overthewire.org -p 2220  

Para este nivel ingresamos con el usuario "bandit2", al ingresar y hacer `ls` vemos un archivo "spaces in this filename", en Linux si un archivo tiene espacios en su nombre, necesitamos escapar estos espacios o usar comillas.  
Con eso obtendriamos la contraseña para el siguiente nivel.  
```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
### Nivel 3 -> Nivel 4
> User: bandit3  
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx  
SSH: bandit3@bandit.labs.overthewire.org -p 2220  

...





[//]: # (
> User: bandit  
Password: M  
SSH: bandit@bandit.labs.overthewire.org -p 2220  
)

#### Lista de codigos Nivel 0-33 
```
level 0 --> bandit0
level 1 --> ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
level 2 --> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
level 3 --> MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
level 4 --> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
level 5 --> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
level 6 --> HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
level 7 --> morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
level 8 --> dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
level 9 --> 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
level 10 --> FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
level 11 --> dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
level 12 --> 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
level 13 --> FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
level 14 --> MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
level 15 --> 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
level 16 --> kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
level 17 --> EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
level 18 --> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
level 19 --> cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
level 20 --> 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
level 21 --> EeoULMCra2q0dSkYj561DX7s1CpBuOBt
level 22 --> tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
level 23 --> 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
level 24 --> gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
level 25 --> iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
level 26 --> s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
level 27 --> upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
level 28 --> Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
level 29 --> 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
level 30 --> qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
level 31 --> fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
level 32 --> 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
level 33 --> tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
level 34 --> no hay hasta el momento :))
```