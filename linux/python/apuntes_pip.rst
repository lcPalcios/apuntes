.. _reference-linux-python-apuntes_pip:

###########
Apuntes PIP
###########

Algunos apuntes de paquetes que estan en pip

Usar una version especifica con pip
===================================

.. code-block:: bash

    pip3 install django==1.5.5

Django
======

.. code-block:: bash

    pip3 install django

Flask
=====

.. code-block:: bash

    pip3 install flask

psycopg2
========

.. code-block:: bash

    # Ubuntu
    apt install libpq-dev

    # Fedora
    yum install postgresql-devel

    pip3 insyall psycopg2

sqlalchemy, ORM database para python
====================================

.. code-block:: bash

    pip3 install sqlalchemy

Python y MySQL
==============

.. warning::
    | **Por hacer**
    | Ver `Conector 1 <http://github.com/davispuh/MySQL-for-Python-3/>`_
    | Ver `Conecttor 2 <http://dev.mysql.com/downloads/connector/python/#downloads>`_

lxml, Manejo de archivos XML
============================

.. note::
    Pillow is the ‘friendly’ PIL fork by Alex Clark and Contributors. PIL is the
    Python Imaging Library by Fredrik Lundh and Contributors.

    | **Fuente**
    | http://pillow.readthedocs.org/en/latest/installation.html

Pillow
======

Ubuntu
^^^^^^

.. code-block:: bash

    sudo apt-get install libtiff4-dev libjpeg8-dev zlib1g-dev \
        libfreetype6-dev liblcms2-dev libwebp-dev tcl8.5-dev tk8.5-dev python3-tk \
        libjpeg-dev libpng12-0 libpng12-dev

Fedora
^^^^^^

**Por hacer**

Instalar Pillow
^^^^^^^^^^^^^^^

.. code-block:: bash

    pip install Pillow
