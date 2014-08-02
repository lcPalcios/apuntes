.. _reference--windows-odbc_postgres_windows:

##########################
ODBC PostgreSQL en Windows
##########################

Desde el instalador de Postgres
*******************************

Una vez instalado Postgresql, ir a inicio y buscar "Application Stack Builder".
Despues de elegir el PostgreSQL instalado, sale un menu, buscar en "Database Driver" y
seleccionar pgsqlODBC, elegir la de 32.

El primer path es para decirle donde lo descarga, se puede dejar que nos propone que
es la carpeta de usuario. Despues pregunta por la carpeta de instalacion
de postgresql, pongo en C:\Postgresql (donde instalo postgres)

Siguiente, Siguiente, Siguiente

Descargandolo a parte
*********************

* http://www.postgresql.org/ftp/odbc/versions/msi/

Descarlar la version de x86 e instalar.

Instalarla en C:\Postgresql\psqlODBCx86\

Independientemente del tipo de instalacion
******************************************

Ir a Control Panel\System and Security\Administrative Tools.

Abrir ODBC Data Sources (32-bit).

En **User DNS** Add y elegir Postgresql Unicode.

Rellenar los campos con los datos del usuario postgres.

Supongo que para la version de x64, se debera hacer lo mismo pero con un binario de x64.
