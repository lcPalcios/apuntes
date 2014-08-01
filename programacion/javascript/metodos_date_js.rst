.. _reference-programacion-javascript-metodos_date_js:

##################
Metodos de Date JS
##################

getTime()
    Devuelve una representacion en milisegundo de la fecha, lo mismo que
    valuesOf(),

setTime(milisegundos)
    Establece una representacion en milisegundos de una fecha, cambiando
    la fecha.

getFullYear()
    Devuelve 4 digitos del año (2013) en vez de 2 (13).

getUTCFullGear()
    Devuelve 4 digitos para el año en UTC.

setFullYear(year)
    Establecer el año de la fecha, el año se a de establecer con 4 digitos.

setUTCFullYear(year)
    Lo mimso que setFullYear() pero el año en UTC

getMonth()
    Obtener el mes de una fecha, donde 0 representa enero y 11 diciembre.

getUTCMonth()
    Lo mimso que getMonth(), pero en UTC

setMonth(month)
    Establecer el mes de una fecha, donde 0 es enero y 11 diciembre.

setUTCMonth(Month)
    Lo mismo que setMonth(month) pero en UTC

getDate()
    Devuelve el dia del mes (1 - 31) de una fecha.

getUTCMonth()
    Igual que getDate() pero en UTC

setDate(date)
    Establecer el dia de una fecha (1 - 31), si el dia es mayor a los dias que
    tiene el mes, el mes tambien sera incrementado.

setUTCDate(date)
    Lo mismo que setDate(date) pero en UTC

getDay()
    Obtener el dia de la semana como un numero, donde 0 es represntado por
    domingo y 6 como sabado

getHours()
    Obtener la hora como un numero entre 0 y 23

getUTCHours()
    Lo mismo que getHours() pero UTC

setHours(hours)
    Establecer la hora de una fecha, hours es un valor numerico entre 0 y 23
    Si el valor es mayor de 23, el dia es incrementado.

setUTCHours(hours)
    Igual que setHours(hours) pero en UTC

getMinutes()
    Obtener el minuto de una hora entre 0 y 59

getUTCMinutes()
    Lo mismo que getMinutes() pero en UTC

setMinutes(minutes)
    Establecer los minutos en una fecha entre 0 y 59, si es mayor de 59, la
    hora sera incrementada.

setUTCMinutes(minutes)
    Lo mismo que setMinutes(minutes) pero en UTC

getSeconds()
    Obtener los segundos de una fecha, numeros entre 0 y 59

getUTCSeconds()
    Lo mismo que getSeconds() pero en UTC

setSeconds(seconds)
    Establecer los segundos en una fecha, si los segundos es mayor a 59
    los minutos se incrementan.

setUTCSeconds(seconds)
    Igual que setSeconds(seconds) pero en UTC

getMilliseconds()
    Obtener la fecha en milisegundos

getUTCMilliseconds()
    Lo mismo que getMilliseconds() pero en UTC

setMilliseconds(milliseconds)
    Establecer una fecha pasando los milisegundos

setUTCMilliseconds(milliseconds)
    Lo mismo que setMilliseconds(milliseconds) pero en UTC

getTimezoneOffset()
    Devuelve la diferencia en minutos de la hora local respecto a UTC
    Por ejemplo, para mi seria -120
