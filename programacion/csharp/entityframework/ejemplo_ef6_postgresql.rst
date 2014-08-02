.. _reference-programacion-csharp-entityframework-ejemplo_ef6_postgresql:

########################################
Ejemplo EntityFramework 6 PostgreSQL 9.3
########################################

Herramientas
************

* PostgreSQL 9.3
* PgAdmin3
* VS 2013
* EntityFramework 6.1.0
* Npgsql 2.1.3
* ASP.NET MVC 5.2

------------

Estos son los pasos que hice para crear un proyecto ASP.NET MVC con PostgreSQL.

Primero creo el proyecto ASP.NET MVC empty, para el ejemplo use el nombre de Blog.

Una vez abierto, desde Package Manager Console, instalo EntityFramework y Npgsql

.. code-block:: none

    Install-Package EntityFramework
    Install-Package Npgsql
    Install-Package Npgsql.EntityFramework

    # Actualizar todos los paquetes del proyecto, MVC a 5.2, etc
    Update-Package

En la base de datos, cree una database 'practicas' para el usuario
'snicoper' y password '123456'

.. code-block:: sql

    CREATE TABLE categorias (
        id serial NOT NULL ,
        titulo character varying(255) NOT NULL
    );

    CREATE TABLE noticias (
        id serial NOT NULL ,
        categoria_id integer NOT NULL ,
        usuario_id integer NOT NULL ,
        titulo character varying(255) NOT NULL ,
        contenido text NOT NULL
    );

    CREATE TABLE usuarios (
        id serial NOT NULL ,
        nombre character varying(50) NOT NULL ,
        email character varying(50) NOT NULL
    );

    ALTER TABLE usuarios ADD CONSTRAINT pk_usuarios_id PRIMARY KEY (id);
    ALTER TABLE categorias ADD CONSTRAINT pk_categorias_id PRIMARY KEY (id);
    ALTER TABLE noticias ADD CONSTRAINT pk_noticias_id PRIMARY KEY (id);
    ALTER TABLE noticias ADD CONSTRAINT fk_noticias_categoria_id FOREIGN KEY (categoria_id) REFERENCES categorias(id) ON UPDATE CASCADE ON DELETE CASCADE;
    ALTER TABLE noticias ADD CONSTRAINT fk_noticias_usuario_id FOREIGN KEY (usuario_id) REFERENCES usuarios(id) ON UPDATE CASCADE ON DELETE CASCADE;

En VS, en la carpeta Models, creo 3 clases 'Usuario.cs', 'Categoria.cs' y 'Noticia.cs'.

**Usuario.cs**

.. code-block:: c#

    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    namespace Blog.Models
    {
        [Table("usuarios", Schema = "public")]
        public class Usuario
        {
            [Key]
            [Column("id")]
            public int UsuarioId { get; set; }

            [Column("nombre")]
            public string Nombre { get; set; }

            [Column("email")]
            public string Email { get; set; }

            public virtual ICollection<Noticia> Noticias { get; set; }
        }
    }

En todas las clases y propiedades (tablas, columnas en la db), les pongo de explicitamente los
nombres de la base de datos.

| ``[Table("xxx")]``
| ``[Column["xxx"]]``
|

EntityFramework tiene una convencion para las PK **ID** o **NombreColID**,
siempre ha de acabar en **xxxID**. El problema es que manejar en postgres
mayusculas es un verdadero lio, nesesita de comillas todos los nombres de
tablas y columnas, asi que opto por ser explicito y listo.

Ademas, en ``[Table("xxx")]`` le digo el schema, en PostgreSQL, usa public por defecto
``[Table("usuarios", Schema = "public")]``

A las claves primarias les pongo el decorador ``[Key]``

Luego ``public virtual ICollection<Noticia> Noticias { get; set; }``,
aqui es donde relaciona con otras tablas (Clases), en este caso, un
usuario puede tener muchas noticias y por eso lo pongo en un
``ICollection<Noticia>``, relacion uno a muchos.

**Categoria.cs**

.. code-block:: c#

    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    namespace Blog.Models
    {
        [Table("categorias", Schema = "public")]
        public class Categoria
        {
            [Column("id")]
            [Key]
            public int CategoriaId { get; set; }

            [Column("titulo")]
            public string Titulo { get; set; }

            public virtual ICollection<Noticia> Noticias { get; set; }
        }
    }

**Noticia.cs**

.. code-block:: c#

    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    namespace Blog.Models
    {
        [Table("noticias", Schema = "public")]
        public class Noticia
        {
            [Column("id")]
            [Key]
            public int NoticiaId { get; set; }

            [Column("categoria_id")]
            [ForeignKey("Categoria")]
            public int CategoriaId { get; set; }

            [Column("usuario_id")]
            [ForeignKey("Usuario")]
            public int UsuarioId { get; set; }

            [Column("titulo")]
            public string Titulo { get; set; }

            [Column("contenido")]
            public string Contenido { get; set; }

            public virtual Usuario Usuario { get; set; }

            public virtual Categoria Categoria { get; set; }
        }
    }

Esta tabla/clase, tiene un par de diferencias, en primer lugar
``[ForeignKey("Usuario")]``, las claves foraneas, tambien existe
una convencion para las claves foraneas, pero otra vez lo mismo
como los nombres de postgres es diferente a la convencion, lo hago
de manera explicita. Lo que le dice es la (¿Clase/Propiedad? aun
no lo tengo muy claro), cual es la referencia.

Por ultimo, en este caso, las propiedades de referencias, como son
uno a uno no usan ``ICollection``.

Las convenciones serian algo asi:

Nombre de la clave foranea. (La tabla debera ser con el mismo nombre)
``public int DepartmentID { get; set; }``

La propiedad de "navegacion", seria el nombre de la clave foranea sin el ID
``public virtual Department Department { get; set; }``

**BlogContext**

.. code-block:: c#

    using System.Data.Entity;

    namespace Blog.Models
    {
        public class BlogContext : DbContext
        {
            public DbSet<Categoria> Categorias { get; set; }

            public DbSet<Noticia> Noticias { get; set; }

            public DbSet<Usuario> Usuarios { get; set; }
        }
    }

Aqui con ``DbSet<Clase>`` le decimos a Entity cuales seran las clases a mapear.
En esta clase se puede hacer muchisimo mas, pero de momento, para un ejemplo rapido, con esto
es suficiante

Configuracion Web.config
************************

Ver :ref:`reference-programacion-csharp-entityframework-connectionstring`

En la configuracion, en ``<add name="BlogContext" ... />``
poner el mismo que la clase Context, en este caso BlogContext

HomeController.cs e Index.cshtml
********************************

**HomeController.cs**

.. code-block:: c#

    using System.Linq;
    using System.Web.Mvc;
    using Blog.Models;

    namespace Blog.Controllers
    {
        public class HomeController : Controller
        {
            BlogContext db = new BlogContext();

            public ActionResult Index(int? id)
            {
                id = id ?? 1;
                var noticias = db.Noticias.Where(n => n.CategoriaId == id).ToList();

                return View(noticias);
            }
        }
    }

**Index.cshtml**

.. code-block:: html

    @using Blog.Models;
    @model List<Noticia>

    @{
        ViewBag.Title = "Index";
    }

    <h2>Index</h2>

    <h3>Lista de noticias</h3>

    <table class="table table-striped">
        <thead>
            <tr>
                <th>Titulo</th>
                <th>Categoria</th>
                <th>Autor</th>
            </tr>
        </thead>
        <tbody>
            @foreach (Noticia noticia in Model)
            {
                <tr>
                    <td>@noticia.Titulo</td>
                    <td>@noticia.Categoria.Titulo</td>
                    <td>@noticia.Usuario.Nombre</td>
                </tr>
            }
        </tbody>
    </table>
