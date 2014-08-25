.. _reference-mono-monodevelop-creacion_proyecto_asp_net_mvc5:

#####################################
Creacion de un proyecto ASP.NET MVC 5
#####################################

Fuentes
*******

* http://curtis.schlak.com/2014/02/04/setup-asp-net-mvc-4-on-monodevelop-4.2.html
* http://joelennon.com/asp-net-mvc-on-mac-os-x/

.. note::
    A partir de Monodevelop 5.2 o 5.3 este problema ya no lo da.

Crear un proyecto MVC con Razor

Editar opciones del proyecto.

``Options > Build > General > Target Framework: Mono/.NET 4.5``

Pinchar encima del nombre del proyecto: ``Add -> Add Packages``.
instlar Microsoft ASP.NET MVC

Editar Web.config

Sustituir:

.. code-block:: xml

    <add key="webpages:Version" value="1.0.0.0" />

    # Por
    <add key="webpages:Version" value="3.0.0.0" />

Editar Views/Web.config

.. code-block:: none

    # Sustituir
    System.Web.WebPages.Razor, Version=1.0.0.0

    # Por
    System.Web.WebPages.Razor, Version=3.0.0.0

    # Sustituir
    System.Web.Mvc, Version=3.0.0.0

    # Por
    System.Web.Mvc, Version=5.1.0.0

En linux, editar permisos. Las rutas varian segun como se ha instalado ``mono``,
pero lo que se ha de tener en cuenta es que en el directorio ``mono`` ha de tener
un directorio ``registry`` y dentro de este, otro llamado ``LocalMachine``

.. code-block:: bash

    sudo mkdir /opt/mono/etc/mono/registry
    sudo mkdir /opt/mono/etc/mono/registry/LocalMachine
    sudo chmod g+rwx /opt/mono/etc/mono/registry
    sudo chmod g+rwx /opt/mono/etc/mono/registry/LocalMachine
