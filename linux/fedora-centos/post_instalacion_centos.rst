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

EPEL RHEL/CentOS 7
*************************

.. code-block:: bash

    wget http://dl.fedoraproject.org/pub/epel/beta/7/x86_64/epel-release-7-2.noarch.rpm
    rpm -ivh epel-release-7-2.noarch.rpm
    rm epel-release-7-2.noarch.rpm

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

    yum install -y kernel-devel kernel-headers gcc cpp make
    yum -y install p7zip \
        p7zip-plugins \
        unrar \
        wget \
        git \
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
        gnome-tweak-tool \
        meld

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
        calligra-l10n-es

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
        kdenetwork-kget \
        kdenetwork-kget-libs \
        amarok \
        bluedevil \
        libbluedevil

PackageKit
**********

.. code-block:: bash

    yum install gnome-packagekit
