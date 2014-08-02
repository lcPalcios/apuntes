.. _reference--windows-visual_studio-nuget_commands:

##############
NuGet Commands
##############

**Fuentes**

* http://blog.nuget.org/20121231/a-quick-tutorial-on-update-package-command.html

--------

Algunos comandos que encuentro utiles y los apunto aqui

* Get-Package: Muestra la lista de paquetes instalados y sus versiones.
* Install-Package [nombre]: Instala un paquete.
* Update-Package: Actualiza los paquetes.
* Update-Package [nombre]: Actualiza el paquete [nombre].
* Uninstall-Package [nombre]: Elimina un paquete.

Para decir en que proyecto se instala/actualiza/etc.
Valido para cualquier comando.

* Install-Package -ProjectName  nombre_proyecto
* Update-Package -ProjectName  nombre_proyecto
