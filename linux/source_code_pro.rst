.. _reference-linux-source_code_pro:

###############
Source Code Pro
###############

**Fuentes**

* http://sourceforge.net/projects/sourcecodepro.adobe/files/
* https://github.com/adobe-fonts/source-code-pro

----

Descargar de sourceforge ``SourceCodePro_FontsOnly-(version).zip``.

Después de descomprimir, crear un directorio ~/.fonts

.. code-block:: bash

    mkdir ~/.fonts

Dentro, hay dos carpetas ``OTF`` y ``TTF``

.. code-block:: bash

    cd carpeta_descomprimida
    cp -r OTF/* ~/.fonts
    cp -r TTF/* ~/.fonts

    sudo fc-cache
