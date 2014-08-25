.. _reference-programacion-csharp-entityframework-recuperar_datos_de_otras_tablas_basico:

############################################
Recuperar datos de otras tablas relacionales
############################################

Fuentes
*******

* Libro: Getting Started with Entity Framework 6 Code First using MVC 5: Pag 161

-----------------

Aunque esta bastante incompleto, pero me dejo una pequeña referencia para saber
como se llaman las formas de hacer las cosas y la pagina donde lo leí.

Imaginando que tenemos 2 modelos

.. code-block:: c#

    class Usuario
    {
        public int UsuarioID { get; set; }

        public string Nombre { get; set; }

        public virtual ICollection<Post> Posts { get; set; }
    }

    class Post
    {
        public int PostID { get; set; }

        public string Titulo { get; set; }

        public virtual ICollection<Usuario> Usuarios { get; set; }
    }

    // El Contexto
    class PracticasContext : DbContext
    {
        public DbSet<Usuario> Usuarios { get; set; }

        public DbSet<Post> Posts { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Entity<Usuario>().HasMany(u => u.Posts).WithMany(p => p.Usuarios);
        }
    }

La base de datos, son 3 tablas Usuarios, Posts y UsuarioPosts.

Con postgres la tabla ``UsuarioPosts`` hay que crearla a mano
y aun no se como hacer las relación en EF.

Lazy loading (Carga diferida)
*****************************

.. code-block:: c#

    // Mostrara todos los titulos de Posts, ya que no hay filtros en Usuario
    List<Usuario> usuarios = db.Usuarios.ToList();

    foreach (Usuario usuario in usuarios)
    {
        foreach (Post post in usuario.Posts)
        {
            Console.WriteLine(post.Titulo);
        }
    }

Eager loading (Carga diligente/Carga rapida)
********************************************

.. code-block:: c#

    // Mostrara todos los titulos de Posts, ya que no hay filtros en Usuario
    // IEnumerable<Usuario> usuarios = db.Usuarios.Include(x => x.Post);

    // Usando filtro, para ver los posts de un usuario con x ID
    IEnumerable<Usuario> usuarios = db.Usuarios.Where(u => u.UsuarioID == 1).Include(x => x.Post);

    foreach (Usuario usuario in usuarios)
    {
        foreach (Post post in usuario.Posts)
        {
            Console.WriteLine(post.Titulo);
        }
    }

Explicit loading (Carga explicita)
**********************************

.. code-block:: c#

    // Mostrara todos los titulos de Posts, ya que no hay filtros en Usuario
    List<Usuario> usuarios = db.Usuarios.ToList();

    foreach (Usuario usuario in usuarios)
    {
        db.Entry(usuario).Collection(x => x.Posts).Load();
        foreach (Post post in usuario.Posts)
        {
            Console.WriteLine(post.Titulo);
        }
    }

Nota del libro
**************

Si usted sabe que necesita los datos relacionados para cada entidad
recuperada, eager loading a menudo ofrece el mejor rendimiento, ya
que una sola consulta enviada a la base de datos suele ser más
eficiente que las consultas separadas para cada entidad recuperada.
Por ejemplo, en los ejemplos anteriores, suponer que cada departamento
tiene diez cursos relacionados. En el ejemplo de eager loading se
traduciría en una sola (unión) de consulta y un solo de ida y vuelta
a la base de datos. La lazy loading y ejemplos de Explicit loading
haría tanto resultado en once consultas y once de ida y vuelta a la
base de datos. Las idas y vueltas adicionales a la base de datos son
especialmente perjudiciales para el rendimiento cuando la latencia es alta.

Por otra parte, en algunos escenarios de lazy loading es más eficiente.
Eager loading podría causar una muy compleja unen a generarse, que
SQL Server no puede procesar de manera eficiente. O si usted necesita
para acceder a las propiedades de navegación de una entidad sólo para
un subconjunto de un conjunto de las entidades que estés procesamiento,
lazy loading podría funcionar mejor, porque eager loading podría recuperar
más datos de los que necesita. Si el rendimiento es crítico, lo mejor es
probar el rendimiento en ambos sentidos con el fin de tomar la mejor decisión
