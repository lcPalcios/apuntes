.. _reference-linux-fedora-centos-post_instalacion_fedora:

#######################
Post instalacion Fedora
#######################

.. note::
    Actualmente Fedora 20

Todo se hace como usuario ``root`` a no ser que se diga lo contrario.

Si se elimina Calligra, eliminarlo antes de actualizar.

.. code-block:: bash

    yum remove calligra*

Actualizar
**********

.. code-block:: bash

    yum update

Instalar Vim
************

.. code-block:: bash

    yum install -y vim

Editar el hosts
***************

.. code-block:: bash

    vim /etc/hosts
    127.0.0.1   lxmaq1.workspace.local lxmaq1

Establecer hostname
*******************

.. code-block:: bash

    hostnamectl set-hostname lxmaq1.workspace.local

RPMFusion and Remi
******************

+ Fedora 20 RPMFusion http://rpmfusion.org/Configuration
+ Con wget

.. code-block:: bash

    cd Downloads/
    yum install -y wget
    wget http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-20.noarch.rpm
    wget http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-20.noarch.rpm

    rpm -U rpmfusion-*
    yum update -y

    # Eliminar
    rm -f rpmfusion-*

Install Remi Repository in Fedora 20
************************************

.. code-block:: bash

    wget http://rpms.famillecollet.com/remi-release-20.rpm
    rpm -Uvh remi-release-20.rpm

Codecs
******

.. code-block:: bash

    yum -y install gstreamer-ffmpeg \
        gstreamer-ffmpeg \
        gstreamer-plugins-ugly \
        gstreamer1-libav \
        gstreamer1-plugins-bad-freeworld \
        gstreamer1-plugins-ugly

Flash-Player x64
****************

.. code-block:: bash

    rpm -ivh http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm
    rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
    yum install -y flash-plugin nspluginwrapper alsa-plugins-pulseaudio libcurl

Programas basicos
*****************

.. code-block:: bash

    # yum -y groupinstall "Development-Tools"
    # O bien
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

Muestra alertas de selinux, no viene por defecto en KDE

.. code-block:: bash

    yum -y install setroubleshoot

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
        kdenetwork-kget \
        kdenetwork-kget-libs \
        amarok \
        bluedevil \
        libbluedevil

Otros
*****

KDE
===

.. code-block:: bash

    yum install -y kde-partitionmanager
    yum install -y sqliteman # Gui Sqlite, en qt
    yum install -y transmission-qt

GTK
===

.. code-block:: bash

    yum install -y qbittorrent
    yum -y install gimp
    yum -y install gparted
    yum -y install filezilla
    yum -y install inkscape
    yum -y install icedtea-web

Chromium estable
================

* http://copr.fedoraproject.org/coprs/churchyard/chromium-russianfedora-tested/

.. code-block:: bash

    /etc/yum.repos.d
    wget https://copr.fedoraproject.org/coprs/churchyard/chromium-russianfedora-tested/repo/fedora-20/churchyard-chromium-russianfedora-tested-fedora-20.repo

    yum install chromium -y
