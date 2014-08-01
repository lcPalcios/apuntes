.. _reference-linux-fedora-centos-post_instalacion_centos:

#######################
Post instalacion Centos
#######################

.. note::
    Actualmente Centos 7

Todo se hace como usuario ``root`` a no ser que se diga lo contrario.

Actualizar el sistema
*********************

.. code-block:: bash

    yum update

EPEL RHEL/CentOS 7 64-Bit
*************************

.. code-block:: bash

    wget http://dl.fedoraproject.org/pub/epel/beta/7/x86_64/epel-release-7-0.2.noarch.rpm
    rpm -ivh epel-release-7-0.2.noarch.rpm
    rm epel-release-7-0.2.noarch.rpm

REMI
****

http://rpms.famillecollet.com/

.. code-block:: bash

    wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
    rpm -ivh remi-release-7.rpm
    rm remi-release-7.rpm

Programas basicos
*****************

.. code-block:: bash

    yum install -y kernel-devel kernel-headers gcc cpp
    yum -y install p7zip \
        p7zip-plugins \
        unrar \
        wget \
        git \
        gitk \
        ctags \
        ctags-etags \
        mutt \
        htop \
        nmap \
        python-pygments \
        java-1.7.0-openjdk-devel

KDE
***

.. code-block:: bash

    yum -y install oxygen-cursor-themes firefox kate \
        umbrello git-cola kdiff3

Gnome
*****

.. code-block:: bash

    yum -y install nautilus-open-terminal \
        gnome-tweak-tool

Calligra completo
*****************

.. code-block:: bash

    yum install -y calligra

Diccionario en español
**********************

.. code-block:: bash

    yum install -y hunspell-es

Idioma KDE español
******************

.. code-block:: bash

    yum -y install kde-l10n-es \
        calligra-l10n-es \

Idioma español man
******************

.. code-block:: bash

    yum -y man-pages-es \
        man-pages-es-extra

Eliminar algunos KDE
********************

.. code-block:: bash

    yum remove -y \
        libkdegames \
        kdegames-minimal \
        kwrite \
        ktorrent \
        kdenetwork-kget \
        kdenetwork-kget-libs \
        amarok \
        bluedevil \
        libbluedevil

PackageKit
**********

.. code-block:: bash

    yum install gnome-packagekit

Otros
*****

.. warning::
    Algunos de KDE no los he encontrado en los repos, pero los dejo aqui...

KDE
===

.. code-block:: bash

    yum install -y kde-partitionmanager # (Usar gparted)
    yum install -y sqliteman # Gui Sqlite, en qt
    yum install -y transmission-qt

GNOME
=====

.. code-block:: bash

    yum install -y qbittorrent
    yum -y install gimp
    yum -y install gparted
    yum -y install filezilla
    yum -y install inkscape
    yum -y install icedtea-web
