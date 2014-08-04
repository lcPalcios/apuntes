.. _reference-programacion-csharp-entityframework-ejemplo_mvc5_identity_ef6_pgsql9:

############################
MVC5 EF6 Identity Postgresql
############################

.. warning::
    Es necesario Npgsql 2.2.0+

Npgsql 2.2.0 ya soporta migraciones y supongo que por eso ahora puedo usar
identity con postgres. Supongo que antes deveria crear las tablas en la
base de datos a mano.

De momento, genera las tablas en la db y puedo usarlas.

El proyecto se crea una aplicacion ASP.NET Web Applicacion > MVC

Ahora en Package Console Manager, instalar Npgsql y Npgsql.EntityFramework

.. code-block:: none

    # Ya instalara tambien Npgsql
    Install-Package Npgsql.EntityFramework -Pre

Editar ``Models > EntityModels.cs`` y añadir

.. code-block:: c#

    protected override void OnModelCreating(System.Data.Entity.DbModelBuilder modelBuilder)
    {
        modelBuilder.HasDefaultSchema("public");
        base.OnModelCreating(modelBuilder);
    }

Ahora ver :ref:`reference-programacion-csharp-entityframework-migracion_ef6_basico` para que cree las tablas
