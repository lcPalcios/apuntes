.. _reference-programacion-csharp-aspnet-mvc-cerrar_DbContext_en_los_controllers:


###################################
Cerrar DbContext en los Controllers
###################################

Cuando se usa en los controladores una propiedad tipo:

.. code-block:: c#

    public class StudentController : Controller
    {
        private SchoolContext db = new SchoolContext();

        [...]

Hay que asegurarse de que quedan cerradas al finalizar las tareas.

Para asegurarse de que se cierra, en el controllador se escribe un metodo
override Dispose, para asegurarnos de que siempre quedara cerrala la conexion
de la base de datos.

.. code-block:: c#

    protected override void Dispose(bool disposing)
    {
        if (disposing)
        {
            db.Dispose();
        }

        base.Dispose(disposing);
    }
