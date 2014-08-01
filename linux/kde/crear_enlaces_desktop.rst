.. _reference-linux-kde-crear_enlaces_desktop:

########################
Crear enlaces en Desktop
########################

Carpeta Home
************

.. code-block:: bash

    vim ~/Desktop/home.desktop

.. code-block:: bash

    [Desktop Entry]
    Comment=Home
    Comment[es]=Carpeta personal
    Encoding=UTF-8
    Icon=user-home
    Name=Home
    Name[es]=Home
    NoDisplay=false
    OnlyShowIn=KDE
    Type=Link
    URL=/home/snicoper

Carpeta Trash
*************

.. code-block:: bash

    vim ~/Desktop/trash.desktop

.. code-block:: bash

    [Desktop Entry]
    Comment=Home
    Comment[es]=Carpeta personal
    Encoding=UTF-8
    Icon=user-home
    Name=Home
    Name[es]=Home
    NoDisplay=false
    OnlyShowIn=KDE
    Type=Link
    URL=/home/snicoper

Carpeta Data
************

.. code-block:: bash

    vim ~/Desktop/data.desktop

.. code-block:: bash

    [Desktop Entry]
    Comment=Home
    Comment[es]=Carpeta personal
    Encoding=UTF-8
    Icon=user-home
    Name=Home
    Name[es]=Home
    NoDisplay=false
    OnlyShowIn=KDE
    Type=Link

    ## Fedora
    URL=/run/media/snicoper/data

    ## Ubuntu
    URL=/media/snicoper/data/snicoper/
