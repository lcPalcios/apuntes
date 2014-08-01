.. _reference-programacion-javascript-atributos_etiqueta_script:

#################################
Atributos de la etiqueta <script>
#################################

La etiqueta <script> tiene seis atributos:

- async:

    Opcional. Indica que el script debe descargarse solo cuando el contenido
    esta ya descargado.
    Solo es valido para si tiene el atributo src (es decir, para js externo)

    El problema es que no se garantiza el orden en que los scripts se ejecutan.

- charset:

    Opcional.  El juego de caracteres del código especificado mediante el
    atributo src.

- defer:

    Opcional. Es parecido a async, lo que hace que aunque este en la cabecera
    del html lo trata como si estubiera al final del documento.
    En caso de necesitarlo, usar async.

- languaje:

    Opcional. Desaprobado, para el indicar el tipo de lenguaje/script
    Javascript, Javascript1.2 o SBScript por ejemplo.

- src:

    Opcional. La ruta del arhico .js

- type:

    Opcional. Para indicarle al navegador el tipo mime de script
    Normalmente se ha usado text/javascript, el tipo mime seria
    application/x-javascript.
    Actualmente no es necesario, ya que por defecto, el navagador lee
    text/javascript


Para evitar problemas, siempre que sea posible, añadir las etiquetas <script>
antes del </body>

Un articulo interesante sobre defer y async
http://www.marketingprofesional.net/ejecucion-asincronica-de-scripts-con-el-atributo-async-y-defer-para-mejorar-la-carga-de-una-web/
