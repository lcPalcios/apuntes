.. _reference-linux-python-pythonpath:

##########
PYTHONPATH
##########

Editar vimrc

.. code-block:: bash

    vim ~/.vimrc

Añadir

.. code-block:: bash

    PYTHONPATH="/home/snicoper/.virtualenvs/py3venv/lib/python3.4/site-packages/":"${PYTHONPATH}"
    export PYTHONPATH

Donde ``/home/snicoper/.virtualenvs/py3venv/lib/python3.4/site-packages/`` sustituirlo
por un directorio.
