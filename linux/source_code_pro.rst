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
    mkdir source-code-pro
    mv OTF/* source-code-pro
    mv TTF/* source-code-pro
    sudo mv source-code-pro /usr/share/fonts/

    sudo fc-cache
