.. _reference-editors-sublime_text-key_bindings:

############
Key Bindings
############

Algunas combinaciones de teclas no me funciona por defecto, por lo que
tengo configuradas una pocas.

Algunas sin modificar si funcionan el Windows, pero para no tener 2
diferentes, uso esta configuracion en ambos sistemas.

.. code-block:: javascript

    [
        // Indetntar codigo
        { "keys": ["ctrl+shift+."], "command": "indent" },

        // DesIndentar codigo
        { "keys": ["ctrl+shift+,"], "command": "unindent" },

        // Comentar linea
        { "keys": ["ctrl+shift+c"], "command": "toggle_comment", "args": { "block": false } },

        // Comentar bloque
        { "keys": ["ctrl+shift+b"], "command": "toggle_comment", "args": { "block": true } },

        // Join lines
        { "keys": ["ctrl+j"], "command": "join_lines" },

        // Alignment (No lo instalo)
        // { "keys": ["ctrl+shift+a"], "command": "alignment" },
    ]
