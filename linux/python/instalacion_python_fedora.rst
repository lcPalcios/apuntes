.. _reference-linux-python-instalacion_python_fedora:

############################
Instalacion Python en Fedora
############################

Python2
=======

.. code-block:: bash

    sudo yum install -y python-setuptools python-devel
    sudo yum install -y python-pip

Python3
=======

.. code-block:: bash

    sudo yum install -y python3 python3-setuptools python3-devel
    sudo yum install -y python3-pip

Use Pip

.. code-block:: bash

    # en python 2
    pip install nombre_paquete

    # en python 3
    pip-python3 install nombre_paquete

Virtualenv y Virtualenvwrapper
******************************

.. code-block:: bash

    su
    pip-python3 install virtualenv virtualenvwrapper
    exit

    mkdir ~/.virtualenvs

Editar .bashrc

.. code-block:: bash

    vim ~/.bashrc

    # Añadir
    export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
    export WORKON_HOME=$HOME/.virtualenvs
    source /usr/bin/virtualenvwrapper.sh

    # Guardar y salir
    source ~/.bashrc

Comandos

* mkvirtualenv // Crea un nuevo virtualenv
* rmvirtualenv // Elimina un virtualenv existente
* workon // Cambia el actual virtualenv
* deactivate // Desactivar virtualenv
* lsvirtualenv // Listar virtualenvs

Para crear un nuevo virtualenv, ejecutar

.. code-block:: bash

    mkvirtualenv nombre_venv

Para usarlo

.. code-block:: bash

    workon nombre_venv
