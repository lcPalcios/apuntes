.. _reference-editors-sublime_text-sublime_repl:

###########
SublimeREPL
###########

Por defecto ejecuta Python 2 **en linux**, para cambiar de ejecutable, hay que modificar un
archivo.

Crear una copia ``Python/Main.sublime-menu``

.. code-block:: bash

    cp .config/sublime-text-3/Packages/SublimeREPL/config/Python/Main.sublime-menu .config/sublime-text-3/Packages/SublimeREPL/config/Python/Main.sublime-menu.orig

Abrir el archivo

.. code-block:: bash

    vim .config/sublime-text-3/Packages/SublimeREPL/config/Python/Main.sublime-menu

    # Ejecutar en busqueda y remplazo con vim
    :%s/\"cmd\"\: \[\"python\"\,/\"cmd\"\: \[\"python3\"\,/g

Para mostrar la consola ``Tools -> SublimeREPL -> Python -> Elegir uno``

