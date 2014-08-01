.. _reference-programacion-html_css-medidas_relativas_tipografia_cajas:

#####################################
Medidas relativas tipografias y cajas
#####################################

Para hacer paginas Web Responsive Desing solo se ha de tener presente unos
pequeños calculos.

Aqui me anoto algunas reglas basicas a tener en cuenta.

En la regla del body en css, poner el font-size: 16px

La regla #page (El contenedor) en %, por ejemplo 98%, aunque si no
se quiere pasar de una anchura, especificarlo con max-width.

En cuanto tamaño, no ponerlo en el body por si acaso, para mas adelante

Tomar como referencia ``960px`` al hacer la division en contenidos hijos de #page
aunque sea un %, contar siempre como si fueran 960px

Los calculos para los ems:

.. code-block:: none

    fuente_deseada_px / fuente_padre_px = resultado

Para poner un ``h1`` que ahora esta con ``16px`` (con resset de Eric Meyer) en
``24px``, seria:

.. code-block:: none

    24 / 16 = 1.5

Serian 1.5em

Los calculos para los % seria:

.. code-block:: none

    contenedor_deseado / contenedor_padre = resultado

Si #page es de ``960px`` y queremos que el header sea de 940px ``940 / 960 = 0,979166667``

Eliminamos el 0, y pasamos 2 decimales el ``979166667``
quedando en 97.9166667%

Acordarse que los borders, rellenos y margenes van a parte.

Si queremos un contenedor completo de 200px con un border de 1px,
margin de 10px y un padding de 10px sobre un contenedor de 960px
el resultado seria el siguiente:

Omito en la suma el relleno, por eso 178px

``margin 20px + border 2px = 22px - 200px = 178px`` de contenido

.. code-block:: none

    Contenido: 178px / 960px = 18.5416667%
    margen: 10px / 960px = 1.0416667%
    relleno: 10px / 960px = 1.0416667%
    borde: 1px x2
    -----------------------------------
    border: 1px solid red;
    width: 18.5416667%;
    margin: 1.0416667%;
    padding: 1.0416667%;

Para cajas con ems en referencia a la tipografia

Ejemplo:

.. code-block:: none

    Tamaño fuente: 16px;
    Caja de 400px;
    400 / 16 = 25

25ems seria una caja de 400px, pero si se aumenta a 18 en un futuro
la caja pasaria a ser de 448px, tener cuidado con esto.


