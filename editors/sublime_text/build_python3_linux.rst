.. _reference-editors-sublime_text-build_python3_linux:

#######################
Build Python 3 en Linux
#######################

En Linux, tanto en Fedora como en Ubuntu se tiene instalado Python 2.x y 3.x,
por fefecto al pulsar ``Ctrl+B`` ejecuta Python 2.x.

Para cambiar este comportamiento, en el editor:

``Tools -> Build System -> new Build System``

.. code-block:: javascript

    {
        "cmd": ["python3", "-u", "$file"],
        "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
        "selector": "source.python"
    }

Lo guardo como ``Python3.sublime-build`` en ``.config/sublime-text-3/Packages/User``

Ahora en ``Tools > Build System`` seleccionar ``Python3``

Virtualenv
**********

Ejemplo de como ejecutarlo para un entorno virtual de python **virtualenv**

.. code-block:: javascript

    {
        "cmd": ["/home/snicoper/.virtualenvs/py3venv/bin/python3", "-u", "$file"],
        "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
        "selector": "source.python"
    }
