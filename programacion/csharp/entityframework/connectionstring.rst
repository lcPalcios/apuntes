.. _reference-programacion-csharp-entityframework-connectionstring:

################
connectionString
################

Fuentes
*******

* https://www.connectionstrings.com/sql-server-2012/

----------------

PostgreSQL
**********

Desde Package Manager Console, instalar los siguientes:

.. code-block:: none

    Install-Package EntityFramework
    Install-Package Npgsql
    Install-Package Npgsql.EntityFramework

.. note::
    Instalando solo ``Install-Package Npgsql.EntityFramework`` ya se encarga
    de instalar las dependendias ``EntityFramework`` y
    ``Npgsql.EntityFramework``

Editar ``web.config`` de la reaiz del proyecto **ASP.NET MVC**

.. code-block:: xml

    <connectionStrings>
      <add name="BloggingContext"
        connectionString="server=localhost;user id=snicoper;password=123456;database=practicas"
        providerName="Npgsql" />
    </connectionStrings>
    <system.data>
      <DbProviderFactories>
        <add name="Npgsql Data Provider"
          invariant="Npgsql"
          description="Data Provider for PostgreSQL"
          type="Npgsql.NpgsqlFactory, Npgsql" />
      </DbProviderFactories>
    </system.data>
    <entityFramework>
      <defaultConnectionFactory type="System.Data.Entity.Infrastructure.SqlConnectionFactory, EntityFramework" />
      <providers>
        <provider invariantName="Npgsql" type="Npgsql.NpgsqlServices, Npgsql.EntityFramework" />
      </providers>
    </entityFramework>

SQL Server Express
******************

Editar ``web.config`` de la reaiz del proyecto **ASP.NET MVC**

.. code-block:: xml

    <connectionStrings>
        <add name="ConnStringDbContext"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLEXPRESS;
                              Initial Catalog=Practicas;
                              Integrated Security=False;
                              User ID=snicoper;Password=123456;
                              MultipleActiveResultSets=True" />
    </connectionStrings>

    <entityFramework>
        <defaultConnectionFactory type="System.Data.Entity.Infrastructure.SqlConnectionFactory, EntityFramework" />
        <providers>
          <provider invariantName="System.Data.SqlClient" type="System.Data.Entity.SqlServer.SqlProviderServices, EntityFramework.SqlServer" />
        </providers>
    </entityFramework>
