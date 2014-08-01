.. _reference-programacion-pcre-detalles_basicos_pcre:

########################
Detalles basicos en PCRE
########################

Fuentes
*******

* http://es.php.net/manual/es/book.pcre.php
* http://www.php.net/manual/es/regexp.reference.meta.php
* http://www.php.net/manual/es/regexp.reference.escape.php#regexp.reference.escape

---------------

Meta-caracteres
***************

* (*) 0 o mas instancias de dicha expresion regular
* (|) Expresion regular compuesta por la expresion regular izquierda o derecha
* (^) Para identificar el inicio de una cadena
* ([^a-z]) Sirve para decir que no puede contener la expresion, en este caso cualquier letra en minusculas.
* ($) Para identificar el final de una cadena
* (.) Para identificar la expresion "cualquier caracter"
* (+) Expresion regular compuesta por una o mas instancias de dicha expresion regular
* (?) Espresion regular compuesta por 0 o 1 instancia de dicha expresion regular
* ({max,min}) Expresion regular compuesta por un numero de variable de instancias de dicha Expresion Regular. El parametro min indica el minimo de numero de instancias aceptables, mientras que el parametro max, si lo ubiera, indica el maximo numero de instancias aceptables. Si solo se encuentra min y la coma disponible, no existe ningun limite superior en cuanto al numero de instancias que podemos encontrar en la cadena. Por ultimo si solo definimos min sin la coma significara el unico numero de instancias aceptable.
* ([]) Sirve para identificar grupos de caracteres aceptables para una determinada posicion.

Secuencias de escape
********************

* (\w) Representa un caracter de "palabra" y es equivalente a la expresion [A-Za-z0-9]
* (\W) Representa lo opuesto a \w y es equivalente a [^A-Za-z0-9]
* (\s) Representa un caracter de espacio en blaco
* (\S) Representa un caracter que no es un espacio en blanco
* (\d) Representa un digito, equivalente a [0-9]
* (\D) Representa un caracter que no es un digito, equivalente a [^0-9]
* (\n) Representa un caracter de nueva linea
* (\r) Representa un caracter de retorno de carro
* (\t) Representa un caracter de tablulacion
