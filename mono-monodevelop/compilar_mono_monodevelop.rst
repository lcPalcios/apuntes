.. _reference-mono-monodevelop-compilar_mono_monodevelop:

###########################
Compilar Mono y Monodevelop
###########################

.. warning::
    Falta Monodevelop

.. note::
    En ubuntu tiene un ppa muy actualizado [Poner link cuando lo tenga]

Fuentes
*******

* Fuentes
* http://www.bgsoftfactory.net/run-asp-net-mvc-4-with-mysql-on-linux/
* http://www.lovesmesomecode.com/post/20130719-compiling-mono-3-in-ubuntu/
* https://www.youtube.com/watch?v=5Ag7qTRXSQA

------------------

Herramientas de compilacion

.. code-block:: bash

    # Ubuntu
    sudo apt-get install build-essential git autoconf libtool automake

Crear carpeta para las fuentes.

.. code-block:: bash

    mkdir -p ~/gitrepos/monobuild

    cd ~/gitrepos/monobuild

libgdiplus
**********

.. code-block:: bash

    # Ubuntu
    sudo apt-get install libglib2.0-dev libjpeg-dev libtiff4-dev \
        libpng12-dev libgif-dev libexif-dev libx11-dev \
        libxrender-dev libfreetype6-dev libfontconfig1-dev \
        libcairo2-dev gettext

.. code-block:: bash

    git clone git://github.com/mono/libgdiplus.git
    cd libgdiplus
    ./autogen.sh --prefix=/usr/local
    make
    sudo make install
    cd..

Mono
****

.. code-block:: bash

    git clone https://github.com/mono/mono.git
    cd mono
    ./autogen.sh --prefix=/usr/local

    make get-monolite-latest
    make EXTERNAL_MCS=${PWD}/mcs/class/lib/monolite/gmcs.exe

    # Instalar
    sudo make install

    mono --version
    cd ..

XSP
***

.. code-block:: bash

    git clone https://github.com/mono/xsp.git
    cd xsp
    ./autogen.sh --prefix=/usr/local
    make
    sudo make install

    xsp4 --version
