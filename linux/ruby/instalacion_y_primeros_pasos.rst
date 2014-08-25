.. _reference-linux-ruby-instalacion_y_primeros_pasos:

############################
Instalación y Primeros Pasos
############################

Instalación
***********

Ubuntu
======

Dependencias para Ruby, si se omiten, cuando se instale Ruby desde
rvm, pedirá instalarlas.

Prerrequisitos
^^^^^^^^^^^^^^

.. code-block:: bash

    sudo apt-get install gawk libreadline6-dev libyaml-dev libsqlite3-dev sqlite3 \
        autoconf libgdbm-dev libncurses5-dev automake libtool bison libffi-dev

    sudo apt-get install nodejs

rvm
^^^^

Es algo así, como Virtualenv?

.. code-block:: bash

    \curl -sSL https://get.rvm.io | bash -s stable

.. warning::
    Esta parte, no se si lo hago bien del todo, buscar mas info de instalación.

Editar .vimrc

.. code-block:: bash

    vim ~/.bashrc

Añadir al final

.. code-block:: bash

    # Load RVM into a shell session *as a function*
    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"
    export PATH="$PATH:$HOME/.rvm/gems/ruby-2.1.1/bin"

    # Add RVM to PATH for scripting
    export PATH="$PATH:$HOME/.rvm/bin"

Releer ~/.bashrc

.. code-block:: bash

    source ~/.bashrc

Instalar Ruby **Tarda su tiempo!!**

.. code-block:: bash

    rvm install ruby-2.1.2
    rvm use ruby-2.1.2 --default

Instalar Rails

.. code-block:: bash

    gem install rails
    rails -v

Fedora
======

.. hint::
    Supongo que sera igual que en **Ubuntu**, lo único son los
    Prerrequisitos, ponerlos si alguna vez lo hago.
