## Natas
###  • Nivel 0  → Nivel 1  
>user: natas0  
password: natas0  
url: http://natas0.natas.labs.overthewire.org  

En este nivel usamos el modo inspeccion del navegador de preferencia,y en el codigo de la pagina se encontrara la contraseña para el siguiente nivel.
![natas0](/images/natas/n0.png)

###  • Nivel 1 → Nivel 2
> user: natas1  
password: 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq  
url: http://natas1.natas.labs.overthewire.org  

Este nivel es similar al anterior ya que igualmente la contraseña esta en el codigo de la pagina.
![natas1](/images/natas/n1.png)

###  • Nivel 2 → Nivel 3
> user: natas2  
password: TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI  
url: http://natas2.natas.labs.overthewire.org  

Para este nivel solo encontramos una imagen el el codigo de la pagina, pero si vamos a los */files/* de la pagina nos encontramos un *.txt* que tiene la contraseña para el siguiente nivel.
![natas2](/images/natas/n2.1.png)

![natas2](/images/natas/n2.2.png)

###  • Nivel 3 → Nivel 4
> user: natas3  
password: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH  
url: http://natas3.natas.labs.overthewire.org  

En este nivel veremos los archivos *robots.txt*, estos indican si ciertos agentes de usuario pueden o no rastrear partes de un sitio web. Actualmente, existe en la mayoría de los sitios web.
![natas3](/images/natas/n3.1.png)

![natas3](/images/natas/n3.2.png)

![natas3](/images/natas/n3.3.png)

###  • Nivel 4 → Nivel 5
> user: natas4  
password: QryZXc2e0zahULdHrtHxzyYkj59kUxLQ  
url: http://natas4.natas.labs.overthewire.org  

Para este nivel debemos entrar como un referrer entrando desde *natas5*, para eso realizamos un script en phyton, ya que si lo hacemos desde el navegador necesitariamos algunas extensiones extras.
![natass4](/images/natas/n4.1.png)

este seria el script para poder entrar.
```
import requests
url = "http://natas4.natas.labs.overthewire.org/"
referer = "http://natas5.natas.labs.overthewire.org/"
s = requests.Session()
s.auth = ('natas4', 'QryZXc2e0zahULdHrtHxzyYkj59kUxLQ')
s.headers.update({'referer': referer})
r = s.get(url)

print(r.text)
```
Una vez ejecutado podemos encontrar la contraseña para el siguiente nivel. 
```
┌──(coria㉿zsun)-[~/Documentos/INF2310/script]
└─$ python3 natas5.py 
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
Access granted. The password for natas5 is 0n35PkggAPm2zbEpOU802c0x0Msn1ToK
```
###  • Nivel 5 → Nivel 6  
> user: natas5  
password: 0n35PkggAPm2zbEpOU802c0x0Msn1ToK  
url: http://natas5.natas.labs.overthewire.org  

Al entrar al sitio del nivel, veremos que nos da la contraseña para el siguiente nivel.
![natas5](/images/natas/n5.png)

###  • Nivel 6 → Nivel 7
> user: natas6  
password: 0RoJwHdSKWFTYR5WuiAewauSuNaBXned  
url: http://natas6.natas.labs.overthewire.org  

En este nivel debemos introducir un secreto, si revisamos el codigo fuente de la pagina, veremos esto:
```
<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>
```
Lo que llama la atencion es el directorio *includes/secret.inc*, si accedemos a el y vemos el codigo fuente encontraremos el secreto y si lo introducimos, obtendremos la contraseña para el siguiente nivel.
![natas6](/images/natas/n6.1.png)

![natas6](/images/natas/n6.2.png)

![natas6](/images/natas/n6.3.png)

###  • Nivel 7 → Nivel 8
> user: natas7  
password: bmg8SvU1LizuWjx3y7xkNERkHxGre0GS  
url: http://natas7.natas.labs.overthewire.org  

Para este nivel la pagina no valida la entrada page, y por lo tanto es vulnerable a ataques de cruce de ruta.
Recordamos que la introducción de Natas Wargame dice: All passwords are also stored in */etc/natas_webpass/natas#*, por lo tanto, podemos intentar establecer el parámetro page como /etc/natas_webpass/natas8 y encontrar la contraseña.
Para eso en la pagehome, iremos añadiendo *../* hasta encontrar el directorio donde se encuentra la contraseña.

![natas7](/images/natas/n7.1.png)

```
http://natas7.natas.labs.overthewire.org/index.php?page=home../../../../../../../../../../etc/natas_webpass/natas8
```

con eso encontrariamos la contraseña.

![natas7](/images/natas/n7.2.png)

###  • Nivel 8 → Nivel 9
> user: natas8  
password: xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q   
url: http://natas8.natas.labs.overthewire.org  

En este nivel veremos el siguiente codigo PHP.
vemos una funcion que compara el codigo con el codigo secreto porlo cual debemos hacer una serie de conversiones.
Primero convertir de hexadecimal a ascii.
luego invertir el texto, finalmente decodificarlo del base64.
```
<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>
```
![natas8](/images/natas/n8.1.png)

Este seria el texto a invertir, si lo invertimos tenemos:
`b3ViV1lmMmtCcQ==`
Como este texto esta en base64 procedemos a decodificarlo.

![natas8](/images/natas/n8.2.png)

Ahora ponemos el codigo descifrado en la pagina y obtenemos la contraseña para el siguiente nivel.

![natas8](/images/natas/n8.3.png)

###  • Nivel 9 → Nivel 10
> user: natas9  
password: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t  
url: http://natas.natas.labs.overthewire.org  

Para este nivel vemos el siguiente codigo:
```
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
```
Al ver el codigo y viendo la pagina vemos que podemos ingresar algun tipo de comando, si intentamos entrar a la carpeta de contraseñas obtendremos la contraseña para el siguiente nivel
Pero debemos poner un `; ` en el campo de busqueda para poder separar el comando de un shell.

![natas](/images/natas/n9.1.png)

###  • Nivel 10 → Nivel 11
> user: natas10  
password: t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu  
url: http://natas.natas.labs.overthewire.org  

Este nivel es similar al anterio solo que tiene algunas restricciones en los caracteres, pero podemos leer todoslos archivosde un directorio con `.*`, de igual manera buscamos en el directorio donde se encuentran las contraseñas.

![natas10](/images/natas/n10.png)

###  • Nivel 11 → Nivel 12
> user: natas11  
password: UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk  
url: http://natas.natas.labs.overthewire.org  

En el codigo veremos que podemos cambiar el campo de `showpassword` a yes y obtendremos el valor de la contraseña pero no la calver para la funcion `xor_encrypt()`, vemos que este nivel se usa el algoritmo XOR, por lo cual conocemos los valores del texto, para eso haremos un script para cambiar los valores, una vez con el valor tendremos que cambiar el valor de la cookie en el navegador y nos daria la contraseña para el siguiente nivel.

![natas11](/images/natas/n11.png)

###  • Nivel 12 → Nivel 13
> user: natas12  
password: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB  
url: http://natas.natas.labs.overthewire.org  



###  • Nivel 13 → Nivel 14
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 14 → Nivel 15 
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 15 → Nivel 16
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 16 → Nivel 17 
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 17 → Nivel 18
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 18 → Nivel 19
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 19 → Nivel 20 
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 20 → Nivel 21
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 21 → Nivel 22
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 22 → Nivel 23
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 23 → Nivel 24
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 24 → Nivel 25
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 25 → Nivel 26 
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 26 → Nivel 27
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 27 → Nivel 28
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 28 → Nivel 29
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 29 → Nivel 30
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 30 → Nivel 31
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 31 → Nivel 32
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 32 → Nivel 33
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  

###  • Nivel 33 → Nivel 34
> user: natas  
password: -  
url: http://natas.natas.labs.overthewire.org  


<br>`lx 22.05`