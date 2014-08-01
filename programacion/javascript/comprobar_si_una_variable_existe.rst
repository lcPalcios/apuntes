.. _reference-programacion-javascript-comprobar_si_una_variable_existe:

################################
Comprobar si una variable existe
################################

Para comprobar si una variable existe, es decir, si ha sido declarada, aunque
no inicializada, para que no de error en modo strict

.. code-block:: javascript

    if (!variable) {} // Error, si la variable no ha sido declarada

    if (typeof variable !== 'undefined') {} // Correcto

Ten en cuanta que el valor devuleto por typeof es undefined en estos casos
y que 'undefined' es un string. typeof siempre devuelve un string!

.. code-block:: javascript

    var var1;

    typeof var1; // 'undefined'
    typeof var2; // 'undefined'

Pero por lo menos, aunque se aya inicializado pero no asignado un valor,
se puede volver al crear y asignar un valor si es nacesario sabiendo
que no modificaremos un valor existente.

.. code-block:: javascript

    if (typeof var2 === 'undefined') {
        var var2 = 'Creando o asignando un valor en "var2"';
    }

    console.log(var2); // Creando o asignando un valor en "var2"
