.. _reference-programacion-csharp-aspnet-mvc-usar_solo_razor_para_las_vistas:

###############################
Usar solo Razor para las Vistas
###############################

Fuentes
*******

* http://geeks.ms/blogs/lruiz/archive/2014/06/20/asp-net-mvc-usa-s-243-lo-el-motor-de-vistas-que-necesites-en-tu-aplicaci-243-n.aspx

----------

Cuando renderizamos de una action a una vista 'return View()', el orden de búsqueda
(o las búsquedas), en un action public ActionResult Prueba() {}:

.. code-block:: none

    The view 'Prueba' or its master was not found or no view engine supports the searched locations. The following locations were searched:
    ~/Views/Home/Prueba.aspx
    ~/Views/Home/Prueba.ascx
    ~/Views/Shared/Prueba.aspx
    ~/Views/Shared/Prueba.ascx
    ~/Views/Home/Prueba.cshtml
    ~/Views/Home/Prueba.vbhtml
    ~/Views/Shared/Prueba.cshtml
    ~/Views/Shared/Prueba.vbhtml

Es decir, busca en~/Views/Home/ y ~/Views/Shared/ un archivo de vista con el mismo
nombre del action con varias extensiones.
.ascx que seria el motor para windows form y vs|cs(html) que seria para el motor de razor.

Para omitir este comportamiento y solo activar el motor de vistas Razor, en el archivo
``~/Global.asax`` se puede añadir lo siguiente:

.. code-block:: c#

    public class MvcApplication : System.Web.HttpApplication
    {
        protected void Application_Start()
        {
            AreaRegistration.RegisterAllAreas();
            RouteConfig.RegisterRoutes(RouteTable.Routes);

            // Limpiar los actuales motores de vista y añadir solo razor
            ViewEngines.Engines.Clear();
            ViewEngines.Engines.Add(new RazorViewEngine());
        }
    }

Ahora el resultado es el siguiente:

.. code-block:: none

    The view 'Prueba' or its master was not found or no view engine supports the searched locations. The following locations were searched:
    ~/Views/Home/Prueba.cshtml
    ~/Views/Home/Prueba.vbhtml
    ~/Views/Shared/Prueba.cshtml
    ~/Views/Shared/Prueba.vbhtml


Otra manera de hacerlo
**********************

Personalizando el motor de razor para las búsquedas de archivo cshtml

Crear carpeta ``Infrastructure`` en la raíz

Crear clae ``CustomLocationViewEngine.cs``

.. code-block:: c#

    using System.Web.Mvc;

    namespace WorkingWithRazor.Infrastructure
    {
        public class CustomLocationViewEngine : RazorViewEngine
        {
            public CustomLocationViewEngine()
            {
                ViewLocationFormats = new string[]
                {
                    "~/Views/{1}/{0}.cshtml",
                    "~/Views/Shared/{0}.cshtml"
                };
            }
        }
    }

Modificar Método Application_Start en ``Global.asax.cs``

.. code-block:: c#

    using System.Web.Mvc;
    using System.Web.Routing;
    using WorkingWithRazor.Infrastructure;

    namespace WorkingWithRazor
    {
        public class MvcApplication : System.Web.HttpApplication
        {
            protected void Application_Start()
            {
                AreaRegistration.RegisterAllAreas();
                RouteConfig.RegisterRoutes(RouteTable.Routes);

                ViewEngines.Engines.Clear();
                ViewEngines.Engines.Add(new CustomLocationViewEngine());
            }
        }
    }

Ahora el resultado es

.. code-block:: none

    ~/Views/Home/Prueba.cshtml
    ~/Views/Shared/Prueba.cshtml
