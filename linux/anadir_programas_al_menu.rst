.. _reference-linux-anadir_programas_al_menu:

########################
Añadir programas al menu
########################

.. note::
    Todos los pongo en ``opt``

Sublime 3
*********

Descomprimir como usuario

.. code-block:: bash

    su
    mv sublime_text_3 /opt/sublime_text_3
    touch /usr/local/bin/sublime
    chmod 755 /usr/local/bin/sublime

.. code-block:: bash

    vim /usr/local/bin/sublime

.. code-block:: bash

    #!/bin/sh
    export SUBLIME_HOME="/opt/sublime_text_3"
    $SUBLIME_HOME/sublime_text $*

.. code-block:: bash

    vim /usr/share/applications/sublime.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=Sublime Text 3
    Comment=Sublime Text Editor
    Exec=sublime %U
    Icon=/opt/sublime_text_3/Icon/48x48/sublime-text.png
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true

Eclipse
*******

.. code-block:: bash

    su
    tar -xvzf nombre_eclipse.tar.gz -C /opt
    chmod -R +r /opt/eclipse
    touch /usr/local/bin/eclipse
    chmod 755 /usr/local/bin/eclipse

.. code-block:: bash

    vim /usr/local/bin/eclipse

.. code-block:: bash

    #!/bin/sh
    export ECLIPSE_HOME="/opt/eclipse"
    $ECLIPSE_HOME/eclipse $*

.. code-block:: bash

    vim /usr/share/applications/eclipse.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=Eclipse
    Comment=Eclipse
    Exec=eclipse
    Icon=/opt/eclipse/icon.xpm
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true

Aptana
******

.. code-block:: bash

    touch /usr/local/bin/aptana
    chmod 755 /usr/local/bin/aptana

.. code-block:: bash

    vim /usr/local/bin/aptana

.. code-block:: bash

    export APTANA_HOME="/opt/aptana"
    $APTANA_HOME/AptanaStudio3 $*

.. code-block:: bash

    vim /usr/share/applications/aptana.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=Aptana Studio 3
    Comment=IDE Web
    Exec=aptana %U
    Icon=/opt/aptana/icon.xpm
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true

DBeaver
*******

.. code-block:: bash

    mv dbeaver /opt/
    touch /usr/local/bin/dbeaver
    chmod 755 /usr/local/bin/dbeaver

.. code-block:: bash

    vim /usr/local/bin/dbeaver

.. code-block:: bash

    #!/bin/sh
    export DBEAVER_HOME="/opt/dbeaver"
    $DBEAVER_HOME/dbeaver $*

.. code-block:: bash

    vim /usr/share/applications/dbeaver.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=DBeaver
    Comment=DB Manager
    Exec=dbeaver
    Icon=/opt/dbeaver/icon.xpm
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true

Netbeans
********

.. code-block:: bash

    unzip netbeans-7.3.1-201306052037-php
    mv netbeans /opt/netbeans
    touch /usr/local/bin/netbeans
    chmod 755 /usr/local/bin/netbeans

.. code-block:: bash

    vim /usr/local/bin/netbeans

.. code-block:: bash

    #!/bin/sh
    export NETBEANS_HOME="/opt/netbeans/bin"
    $NETBEANS_HOME/netbeans $*

.. code-block:: bash

    vim /usr/share/applications/netbeans.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=netbeans
    Comment=IDE PHP
    Exec=netbeans
    Icon=/opt/netbeans/harness/nbi/stub/ext/components/products/helloworld/data/icon48.png
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true

PhpStorm
********

.. note::
    Los productos de Jetbrains los pongo dentro de ``/opt/jetbrains/``,
    si no existe, la creo.

.. code-block:: bash

    # Si no existe
    mkdir /opt/jetbrains
    gzip -d PhpStorm-7.0.tar.gz
    tar -xvf PhpStorm-7.0.tar
    mv PhpStorm-131.374 /opt/jetbrains/PhpStorm
    chmod +x /opt/jetbrains/PhpStorm/bin/phpstorm.sh
    touch /usr/local/bin/pstorm
    chmod 755 /usr/local/bin/pstorm

.. code-block:: bash

    vim /usr/local/bin/pstorm

.. code-block:: bash

    #!/bin/sh
    export PHP_STORM="/opt/jetbrains/PhpStorm/bin"
    $PHP_STORM/phpstorm.sh $*

.. code-block:: bash

    vim /usr/share/applications/phpstorm.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=PhpStorm
    Comment=IDE for PHP
    Exec=pstorm
    Icon=/opt/jetbrains/PhpStorm/bin/webide.png
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true



Intellij idea
*************

.. code-block:: bash

    # Si no existe
    mkdir /opt/jetbrains
    cp -r idea-IU-123.169/ /usr/local/jetbrains/intellij-idea
    chmod +x /opt/jetbrains/intellij-idea/bin/idea.sh
    touch /usr/local/bin/intellij-idea
    chmod 755 /usr/local/bin/intellij-idea

.. code-block:: bash

    vim /usr/local/bin/intellij-idea

.. code-block:: bash

    #!/bin/sh
    export INTELLIJ_IDEA="/opt/jetbrains/intellij-idea/bin"
    $INTELLIJ_IDEA/idea.sh $*

.. code-block:: bash

    vim /usr/share/applications/intellij-idea.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=Intellij Idea
    Comment=IDE for JAVA
    Exec=intellij-idea %U
    Icon=/opt/jetbrains/intellij-idea/bin/idea.png
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;

PyCharm
*******

.. code-block:: bash

    # Si no existe
    mkdir /opt/jetbrains
    gzip -d pycharm-professional-3.1.3.tar.gz
    tar -xvf pycharm-professional-3.1.3.tar
    mv pycharm-3.1.3/ /opt/jetbrains/pycharm
    chmod +x /opt/jetbrains/pycharm/bin/pycharm.sh
    touch /usr/local/bin/pycharm
    chmod 755 /usr/local/bin/pycharm

.. code-block:: bash

    vim /usr/local/bin/pycharm

.. code-block:: bash

    #!/bin/sh
    export PYCHARM="/opt/jetbrains/pycharm/bin"
    $PYCHARM/pycharm.sh $*

.. code-block:: bash

    vim /usr/share/applications/pycharm.desktop

.. code-block:: bash

    [Desktop Entry]
    Encoding=UTF-8
    Name=PyCharm
    Comment=IDE for Python
    Exec=pycharm %U
    Icon=/opt/jetbrains/pycharm/bin/pycharm.png
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Development;
    StartupNotify=true
