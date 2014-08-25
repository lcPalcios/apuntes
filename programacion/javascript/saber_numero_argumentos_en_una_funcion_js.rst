.. _reference-programacion-javascript-saber_numero_argumentos_en_una_funcion_js:

###########################################################
Saber el números de argumentos se han pasado en una función
###########################################################

Fuentes

* https://developer.mozilla.org/es/docs/Referencia_de_JavaScript_1.5/Funciones/arguments

-------------

Para saber cuantos argumentos se han pasado en una función, se ha de usar el
objeto arguments.

Arguments, aunque es un objeto, se trata como si fuera un array.

.. code-block:: javascript

    function pruebaArguments() {
        arguments.length; // 3
        arguments[1]; // 'dos'
    }

    pruebaArguments(1, 'dos', false);
