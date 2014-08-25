.. _reference--windows-odbc_postgres_windows:

##########################
ODBC PostgreSQL en Windows
##########################

Desde el instalador de Postgres
*******************************

Una vez instalado Postgresql, ir a inicio y buscar "Application Stack Builder".
Después de elegir el PostgreSQL instalado, sale un menú, buscar en "Database Driver" y
seleccionar pgsqlODBC, elegir la de 32.

El primer path es para decirle donde lo descarga, se puede dejar que nos propone que
es la carpeta de usuario. Después pregunta por la carpeta de instalación
de postgresql, pongo en C:\Postgresql (donde instalo postgres)

Siguiente, Siguiente, Siguiente

Descargándolo a parte
*********************

* http://www.postgresql.org/ftp/odbc/versions/msi/

Descargar la versión de x86 e instalar.

Instalarla en C:\Postgresql\psqlODBCx86\

Independientemente del tipo de instalación
******************************************

Ir a Control Panel\System and Security\Administrative Tools.

Abrir ODBC Data Sources (32-bit).

En **User DNS** Add y elegir Postgresql Unicode.

Rellenar los campos con los datos del usuario postgres.

Supongo que para la versión de x64, se deberá hacer lo mismo pero con un binario de x64.
