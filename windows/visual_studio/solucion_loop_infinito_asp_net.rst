.. _reference--windows-visual_studio-solucion_loop_infinito_asp_net:

#####################################
Solucion Loop infinito en ASP.NET IIS
#####################################

**Fuentes**

* http://stackoverflow.com/questions/19601412/new-asp-net-mvc5-project-produces-an-infinite-loop-to-login-page

-------

Cree un proyecto en asp.net con un nombre que ya habia usado en otro proyecto,
el que biene por defecto.

Al cargar la pagina para probarla, me hacia un loop infinito en la barra de
direcciones en el navegador y salia el error:

.. code-block:: bash

    "HTTP Error 404.15 - Not Found The request filtering module is configured to deny a request where the query string is too long."

Para solucionarlo, abri el archivo:

.. code-block:: bash

    C:\Users\snicoper\Documents\IISExpress\config\applicationhost.config

Una vez dentro, elimine toda referencia con el nombre del proyecto (pero no
eliminar el archivo)
