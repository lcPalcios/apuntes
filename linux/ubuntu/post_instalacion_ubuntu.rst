.. _reference-linux-ubuntu-post_instalacion_ubuntu:

#######################
Post instalacion Ubuntu
#######################

Tengo el SO en ingles, pero país, moneda, etc en español. Si da el error de
``locale: Cannot set LC_ALL to default locale: No such file or directory``,
editar ``/etc/environment`` y añadir:

.. code-block:: bash

    LC_ALL="en_US.UTF-8"

    # reiniciar

Si se usa calligra, eliminar libreoffice antes de actualizar.

.. code-block:: bash

    sudo apt-get remove --purge libreoffice*

Actualizar.

.. code-block:: bash

    sudo apt-get update && apt-get dist-upgrade

Si es Virtualbox.

.. code-block:: bash

    sudo apt-get install virtualbox-guest-dkms

Instalar Vim.

.. code-block:: bash

    sudo apt-get -y install vim

Cambiar editor.

.. code-block:: bash

    sudo update-alternatives --config editor

Programas basicos.

.. code-block:: bash

    sudo apt-get install -y \
        build-essential \
        git \
        gitk \
        git-cola \
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

Diccionario español.

.. code-block:: bash

    sudo apt-get install aspell-es myspell-es -y

KDE
===

Si se configura Akonadi con SQLite o PostgreSQL.

Cambiar en Menú y buscar Akonadi Server Configuration.

.. code-block:: bash

    sudo apt-get install akonadi-backend-sqlite
    sudo apt-get install akonadi-backend-postgresql

Muon.

.. code-block:: bash

    sudo apt-get -y install muon

Calligra.

.. code-block:: bash

    sudo apt-get install calligra -y

kdiff3.

.. code-block:: bash

    sudo apt-get install kdiff3-qt -y

Utilidades KDE.

.. code-block:: bash

    sudo apt-get install kgpg kleopatra kcolorchooser -y

Para visualizar las miniaturas en Dolphin de los .pdf.

.. code-block:: bash

    sudo apt-get install kdegraphics-thumbnailers -y

Eliminar.

.. code-block:: bash

    sudo apt-get remove --purge kget amarok -y

Opcionales.

.. code-block:: bash

    sudo apt-get install kdeplasma-addons -y

Transmision.

.. code-block:: bash

    sudo apt-get install transmission-qt -y

qBittorent.

.. code-block:: bash

    sudo apt-get install qbittorrent -y

-----------------------

GNOME
=====

gnome 3.12 en ubuntu-gnome 14.04.

* https://kerneleros.com/instalar-gnome-3-12-en-ubuntu-14-04/

Eliminar en Ubuntu Unity Amazon.

.. code-block:: bash

    sudo apt-get remove --purge unity-webapps-common

Synaptic.

.. code-block:: bash

    sudo apt-get install synaptic

Open terminal here.

.. code-block:: bash

    sudo apt-get install nautilus-open-terminal

Meld.

.. code-block:: bash

    sudo apt-get install meld -y

Gpick.

.. code-block:: bash

    sudo apt-get install gpick -y

libreoffice.

.. code-block:: bash

    sudo apt-get install libreoffice

RabbitVCS.

.. code-block:: bash

    sudo add-apt-repository ppa:rabbitvcs/ppa
    sudo apt-get update
    sudo apt-get install rabbitvcs-nautilus3 rabbitvcs-cli

-------------------

KDE/GNOME/Varios
================

Umbrello.

    sudo apt-get install -y  umbrello

Gui SQLite.

.. code-block:: bash

    sudo apt-get install -y sqliteman

Thunderbird.

.. code-block:: bash

    sudo apt-get install thunderbird

Chromium.

.. code-block:: bash

    sudo apt-get install chromium-browser -y

Vlc.

.. code-block:: bash

    sudo apt-get install vlc

Inskape y gimp.

.. code-block:: bash

    sudo apt-get install gimp inkscape

Filezilla.

.. code-block:: bash

    sudo apt-get install filezilla

Kdevelop.

.. code-block:: bash

    sudo apt-get install kdevelop cmake

kdevelop python.

.. code-block:: bash

    sudo apt-get install kdev-python pep8

qtcreator.

.. code-block:: bash

    sudo apt-get -y install qtcreator

No mostrar la opción de cuenta de invitado al hacer login.

.. code-block:: bash

    sudo sh -c 'printf "[SeatDefaults]\nallow-guest=false\n" >/usr/share/lightdm/lightdm.conf.d/50-no-guest.conf'
