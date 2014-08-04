.. _reference--windows-instalacion_python_windows:

#############################
Instalacion Python en Windows
#############################

Fuentes
*******
* https://www.python.org/
* http://www.lfd.uci.edu/~gohlke/pythonlibs/
* http://www.stickpeople.com/projects/python/win-psycopg/

------------

..note::
    Python 3.4+ ya viene por defecto pip y setuptools

Variables de entorno
********************

.. code-block:: bash

    C:\Python34\;C:\Python34\Scripts\;

Virtualenv
**********

.. code-block:: bash

    pip install virtualenv

    # Con la bandera --no-site-packages, no instala los packetes del Python original.
    # virtualenv --system-site-packages py3venv
    virtualenv venv

    cd venv
    Scripts\activate

    # Para salir de virtualenv
    deactivate

Pysopg2
=======

``version 2.5.3``

.. code-block:: bash

    (py3venv) easy_install http://www.stickpeople.com/projects/python/win-psycopg/2.5.3/psycopg2-2.5.3.win-amd64-py3.4-pg9.3.4-release.exe

PYTHONPATH
**********

Crear variable de entorno PYTHONPATH y añadir la carpeta site-packages de un entorno virtual

.. code-block:: bash

    C:\virtualenvs\py3venv\Lib\site-packages
