.. _reference-programacion-javascript-tostring_and_valueof_js:

##################
toString y valueOf
##################

Tanto toString como valueOf se puede usar para otener datos rapidamente de un
objeto.

valueOf tiene precedencia sobre toString.

Cuando se quiere convertir un objeto en un dato primitivo, javascript intenta
por medio de valueOf obtener un datos primitivo.
En caso de no existir, comprobara si toString existe y en caso de que tampoco
exista, devolvera [object object]

Por ejemplo

.. code-block:: javascript

    var o = {
        titulo: 'Libro de javascript',
        paginas: 656,

        valueOf: function() {
            return this.paginas;
        },

        toString: function() {
            return this.paginas + 100;
        }
    };

    var num = 700;
    num < o; // false: num no es menor a o.valueOf() que devuelve 656

    num < o.toString(); // true, 700 es menor que (656 + 100)

De manera implicita si solo se llama al objeto "o", usara para la conversion
valueOf.

.. code-block:: javascript

    var o = {
        titulo: 'Libro de javascript',
        paginas: 656,

        //valueOf: function() {
        //    return this.paginas;
        //},

        toString: function() {
            return this.paginas + 100;
        }
    };

    var num = 700;
    num < o; // true: ahora de manera implicita ha llamado a toString al no estar
            // defina valueOf

    var o = {
        titulo: 'Libro de javascript',
        paginas: 656,

        //valueOf: function() {
        //    return this.paginas;
        //},

        //toString: function() {
        //    return this.paginas + 100;
        //}
    };

    var num = 700;
    num < o; // false: o devuelve [object object]
