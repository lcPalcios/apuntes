.. _reference-editors-sublime_text-codeintel:

#########
Codeintel
#########

.. attention::
    Para recordar, me dejo aquí algunos ejemplos, hay que cambiar las rutas.

Configuracion Linux
*******************

.. code-block:: bash

    vim ~/.codeintel/config

.. code-block:: javascript

    {
        "PHP": {
            "php": '/usr/bin/php',
            "phpExtraPaths": [],
            "phpConfigFile": '/etc/php.ini'
        },
        "JavaScript": {
            "javascriptExtraPaths": []
        },
        "Perl": {
            "perl": "/usr/bin/perl",
            "perlExtraPaths": []
        }
        "Python": {
            "python": '/usr/bin/python',
            "pythonExtraPaths": []
        },
        "Python3": {
            "python": '/usr/bin/python3',
            "pythonExtraPaths": []
        },
        "virtualenv_de_muestra": {
            "python": '/home/snicoper/venvs/py3venv/bin/python3',
            "pythonExtraPaths": [
                '/home/snicoper/venvs/py3venv/lib/python3.3/site-packages'
            ]
        },
    }
