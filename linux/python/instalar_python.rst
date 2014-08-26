.. _reference-linux-python-instalar_python:

#####################
Instalación de Python
#####################

Fedora
******

Python2
=======

.. code-block:: bash

    yum install -y python-setuptools python-devel
    yum install -y python-pip

Python3
=======

.. code-block:: bash

    yum install -y python3 python3-setuptools python3-devel
    yum install -y python3-pip

Ubuntu
******

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

Virtualenv con python 3
=======================

Si se va a usar Virtualenvwrapper omitir esta parte

.. code-block:: bash

    virtualenv -p /usr/bin/python3 ~/.virtualenvs/py3venv --no-site-packages
    source py3venv/bin/activate

Para desactivar

.. code-block:: bash

    deactivate

Instalar Virtualenvwrapper
==========================

.. code-block:: bash

    sudo pip3 install virtualenvwrapper

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

    mkvirtualenv nombre_site

Para usarlo

.. code-block:: bash

    workon nombre_site
