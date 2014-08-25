.. _reference-linux-source_code_pro:

###############
Source Code Pro
###############

**Fuentes**

* http://sourceforge.net/projects/sourcecodepro.adobe/files/
* https://github.com/adobe-fonts/source-code-pro

----

Descargar de sourceforge ``SourceCodePro_WebFontsOnly-(version)``.

Después de descomprimir crear carpeta ~/.fonts

.. code-block:: bash

    mkdir ~/.fonts

Dentro, hay una carpeta ``WOFF`` que contiene dos carpetas ``OTF`` y ``TTF``

.. code-block:: bash

    cd carpeta_descomprimida
    cp -r WOFF/OTF/* ~/.fonts
    cp -r WOFF/TTF/* ~/.fonts

    sudo fc-cache
