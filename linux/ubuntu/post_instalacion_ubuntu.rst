.. _reference-linux-ubuntu-post_instalacion_ubuntu:

#######################
Post instalacion Ubuntu
#######################

Si se usa calligra, eliminar libreoffice antes de actualizar.

.. code-block:: bash

    sudo apt-get remove --purge libreoffice*

Actualizar

.. code-block:: bash

    sudo apt-get update && apt-get dist-upgrade

Si es Virtualbox

.. code-block:: bash

    sudo apt-get install virtualbox-guest-dkms

Instalar Vim

.. code-block:: bash

    sudo apt-get -y install vim

Cambiar editor

.. code-block:: bash

    sudo update-alternatives --config editor

Programas basicos

.. code-block:: bash

    sudo apt-get install -y \
        build-essential \
        git-core \
        gitk \
        exuberant-ctags \
        curl \
        wget \
        ssh \
        unrar \
        htop \
        nmap \
        tree \
        python-pygments

    sudo apt-get install -y \
        openjdk-7-jre \
        openjdk-7-jdk

Diccionario español

.. code-block:: bash

    sudo apt-get install aspell-es -y

KDE
===

Si se configura Akonadi con SQLite

Cambiar en Menu y buscar Akonadi Server Configuraction

.. code-block:: bash

    sudo apt-get install akonadi-backend-sqlite

Gui SQLite

.. code-block:: bash

    sudo apt-get install sqliteman

Muon

.. code-block:: bash

    sudo apt-get install muon

Calligra

.. code-block:: bash

    sudo apt-get install calligra -y

kdiff3

.. code-block:: bash

    sudo apt-get install kdiff3-qt -y

Utilidades KDE

.. code-block:: bash

    sudo apt-get install kgpg kleopatra umbrello kcolorchooser -y

Para visualizar las miniaturas en Dolphin de los .pdf

.. code-block:: bash

    sudo apt-get install kdegraphics-thumbnailers -y

Transmision

.. code-block:: bash

    sudo apt-get install transmission-qt -y

Eliminar

.. code-block:: bash

    sudo apt-get remove --purge kget ktorrent amarok -y

Opcionales

.. code-block:: bash

    sudo apt-get install kdeplasma-addons -y

qBittorent

.. code-block:: bash

    sudo apt-get install qbittorrent -y

-----------------------

GNOME
=====

.. code-block:: bash

    sudo apt-get remove --purge unity-webapps-common

Synaptic

.. code-block:: bash

    sudo apt-get install synaptic

Open terminal here

.. code-block:: bash

    sudo apt-get install nautilus-open-terminal

Meld

.. code-block:: bash

    sudo apt-get install meld -y

libreoffice

.. code-block:: bash

    sudo apt-get install libreoffice

-------------------

KDE/GNOME
=========

Thunderbird

.. code-block:: bash

    sudo apt-get install thunderbird

Chromium

.. code-block:: bash

    sudo apt-get install chromium-browser -y

Vlc

.. code-block:: bash

    sudo apt-get install vlc

Inskape y gimp

.. code-block:: bash

    sudo apt-get install gimp inkscape

Filezilla

.. code-block:: bash

    sudo apt-get install filezilla

Kdevelop

.. code-block:: bash

    sudo apt-get install kdevelop cmake

kdevelop python

.. code-block:: bash

    sudo apt-get install kdev-python pep8

qtcreator

.. code-block:: bash

    sudo apt-get -y install qtcreator

No mostrar la opcion de cuenta de envitado al hacer login con kde

.. code-block:: bash

    sudo sh -c 'printf "[SeatDefaults]\nallow-guest=false\n" >/usr/share/lightdm/lightdm.conf.d/50-no-guest.conf'
