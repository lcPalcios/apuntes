.. _reference-programacion-javascript-apply_and_call_js:

#######################
Apply y Call Javascript
#######################

Los metodos apply y call, son metodos que tienen todas las funciones de
javascript.

Estos metodos nos permiten llamar a una function como si fuese el metodo de
otro objeto.

.. code-block:: javascript

    function A(nombre) {
        this.nombre = nombre;
    }

    function B(apellido) {
        return this.nombre + ' ' + apellido;
    }

    var o = new A('Salvador');

    B.apply(o, ['Nicolas']); // Salvador Nicolas

La diferencia de apply y call, es la manera que se le pasan los argumentos

.. code-block:: javascript

    B.call(objeto, param1, param2, param3);
    B.apply(objeto, [param1, param2, param3]);
