.. _reference-editors-sublime_text-error_lang_en_us_utf-8-sublime_text:

###################################
Error LANG=en_US.UTF-8 sublime_text
###################################

Me paso en Ubuntu

Editar

.. code-block:: bash

    sudo vim /usr/share/applications/sublime_text.desktop

Buscar y remplazar:

.. code-block:: bash

    # buscar
    Exec=/opt/sublime_text/sublime_text %F

    # remplazar
    Exec=bash -c "LANG=en_US.UTF-8 /opt/sublime_text/sublime_text %F"
