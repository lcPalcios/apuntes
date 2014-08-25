.. _reference-programacion-javascript-valores_como_constantes_en_funciones_js:

####################################
Valores como constantes en funciones
####################################


Para crear un valor constante en una función, una manera simple seria
crear una variable fuera de la función (una variable global) y después
dentro de la funcionan cambiar el valor de dicha variable global.

.. code-block:: javascript

    /* Opcion 1 */
    var num = 0;

    function aumentar() {
        return ++num;
    }

    aumentar(); // 1
    aumentar(); // 2
    aumentar(); // 3

Una forma mas interesante seria de la siguiente manera.
Como las funciones son un tipo de objeto, crear una propiedad de función
y luego dentro de la función incrementar el valor.

.. code-block:: javascript

    /* Opcion 2 */
    // aumentar.num = 0; // Es posible crearlo antes de la definición de la funcionan
    function aumentar() {
        aumentar.num = (aumentar.num === undefined) ? 1 : ++aumentar.num;

        return aumentar.num;
    }
    aumentar(); // 1
    aumentar(); // 2

    La 3º forma, seria con un cierre (Recomendada)
    var aumentar = (function() {
        var num = 1;

        return function() {
            return num++;
        };
    })();

    aumentar(); // 1
    aumentar(); // 2
