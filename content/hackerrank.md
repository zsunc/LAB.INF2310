## HACKER RANK - LINUX SHELL - BASH
### • EJERCICIO 1
![ej1](/images/hackerrank/hacker1.png)

```
#! /bin/bash
echo "HELLO"
```

![ej1](/images/hackerrank/hacker1r.png)

### • EJERCICIO 2
![ej2](/images/hackerrank/hacker2.png)

```
for((i=1; i<=99; i++)) do
if((i%2 !=0))
then
echo $i
fi
done
```

![ej2](/images/hackerrank/hacker2r.png)

### • EJERCICIO 3
![ej3](/images/hackerrank/hacker3.png)

```
read nombre
echo "Welcome $nombre"
```

![ej3](/images/hackerrank/hacker3r.png)

### • EJERCICIO 4
![ej4](/images/hackerrank/hacker4.png)

```
for((i=1; i<=50; i++)) do
echo $i
done
```

![ej4](/images/hackerrank/hacker4r.png)

### • EJERCICIO 5
![ej5](/images/hackerrank/hacker5.png)

```
read x
read y
echo $[x+y]
echo $[x-y]
echo $[x*y]
echo $[x/y]
```

![ej5](/images/hackerrank/hacker5r.png)

### • EJERCICIO 6
![ej6](/images/hackerrank/hacker6.png)

```
read x
read y
if [[ $x < $y ]]
then
echo "X is less than Y"
elif [[ $x > $y ]]
then 
echo "X is greater than Y"
else
echo "X is equal to Y"
fi
```
![ej6](/images/hackerrank/hacker6r.png)

### • EJERCICIO 7
![ej7](/images/hackerrank/hacker7.png)

```
read letra
if [[ $letra = 'y'  ]]
then
echo "YES"
elif [[ $letra = 'Y' ]]
then
echo "YES"
else
echo "NO"
fi
```
![ej7](/images/hackerrank/hacker7r.png)

### • EJERCICIO 8
![ej8](/images/hackerrank/hacker8.png)

```
read x
read y
read z

if(($x == $y && $y == $z)) 
then
echo "EQUILATERAL"
elif(($x == $y || $x == $z || $z == $y))
then
echo "ISOSCELES"
else
echo "SCALENE"
fi
```
![ej8](/images/hackerrank/hacker8r.png)

### • EJERCICIO 9
