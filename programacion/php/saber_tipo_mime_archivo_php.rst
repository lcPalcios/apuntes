.. _reference-programacion-php-saber_tipo_mime_archivo_php:

#############################
Saber tipo mime de un archivo
#############################

mirar por ``fopen_file()``

.. code-block:: php

    <?php

    shell_exec('file -i'.escapeshellcmd($nombreArchivoSubido));
