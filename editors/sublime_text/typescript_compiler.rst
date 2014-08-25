.. _reference-editors-sublime_text-typescript_compiler:

###################
Typescript compiler
###################

Comprobar donde esta el binario de ``tsc``

.. code-block:: bash

    which tsc

Añadirlo a ``Preferences > Package Settings > Better Typescript > Settigs User``

.. code-block:: javascript

    {
        "binDir": "/usr/local/bin",
        "compileOnSave": true
    }
