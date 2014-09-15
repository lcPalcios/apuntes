.. _reference-linux-python-compilar_python_34_centos:

#################################
Compilar Python 3.4.1 en Centos 7
#################################

Compilación
***********

.. code-block:: bash

    sudo yum install -y zlib-devel openssl-devel sqlite-devel bzip2-devel
    wget https://www.python.org/ftp/python/3.4.1/Python-3.4.1.tgz
    tar -zxvf Python-3.4.1.tgz
    cd Python-3.4.1

    ./configure
    make
    sudo make altinstall

Usar pip con ``pip3.4``

Virtualenv y Virtualenvwrapper
******************************

.. code-block:: bash

    su
    pip3.4 install virtualenv virtualenvwrapper
    exit

Como usuario:

.. code-block:: bash

    mkdir ~/.virtualenvs

Añadir a ``~/.bashrc``

.. code-block:: bash

    vim ~/.bashrc

    export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3.4
    export WORKON_HOME=$HOME/.virtualenvs
    source /usr/local/bin/virtualenvwrapper.sh

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
