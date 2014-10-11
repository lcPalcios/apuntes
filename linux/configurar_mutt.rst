.. _reference-linux-configurar_mutt:

###############
Configurar mutt
###############

**Fuentes**

* http://www.elho.net/mutt/maildir/

----

.. code-block:: bash

    # Fedora
    sudo vim /etc/Muttrc

.. code-block:: bash

    # Linea 1066
    set folder="~/Maildir"

    # Linea 1991
    set mask="!^\\.[^.]"

    # Linea 2003
    set mbox="~/Maildir"

    # Linea 2016
    set mbox_type=Maildir

    # Linea 3017
    set postponed="+.Drafts"

    # Linea 3256
    set record="+.Sent"

    # Linea 4176
    set spoolfile="~/Maildir"

Para entrar al correo, simplemente ``mutt``

