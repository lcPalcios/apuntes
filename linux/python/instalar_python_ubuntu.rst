.. _reference-linux-python-instalar_python:

############################
Instalacion Python en Ubuntu
############################

Python2
=======

.. code-block:: bash

    sudo apt install -y python-dev python-setuptools
    sudo apt install -y python-pip

Python3
=======

.. code-block:: bash

    sudo apt install -y python3 python3-dev python3-setuptools
    sudo apt install -y python3-pip


Use Pip

.. code-block:: bash

    # en python 2
    pip install nombre_paquete

    # en python 3
    pip3 install nombre_paquete

Virtualenv y Virtualenvwrapper en Fedora/Ubuntu
***********************************************

Instalación

.. code-block:: bash

    sudo pip3 install virtualenv
    mkdir ~/.virtualenvs

Virtualenv y Virtualenvwrapper
******************************

.. code-block:: bash

    su
    pip3 install virtualenv virtualenvwrapper
    exit

    mkdir ~/.virtualenvs

Editar .bashrc

.. code-block:: bash

    vim ~/.bashrc

Añadir

.. code-block:: bash

    export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
    export WORKON_HOME=$HOME/.virtualenvs
    source /usr/local/bin/virtualenvwrapper.sh

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
