.. _reference-programacion-csharp-aspnet-mvc-descripcion_carpetas:

.. |br| raw:: html

    <br />

###############################
Descrption Arbol en un Proyecto
###############################

=================   ==============================  ==============================
Folder or file      Descripcion                     Notas
=================   ==============================  ==============================
/App_Data           Esta carpeta es donde |br|      IIS no va a servir el contenido |br|
                    pones los datos privados, |br|  de esta carpeta.
                    como los archivos XML o |br|
                    bases de datos si está |br|
                    utilizando SQL Server |br|
                    Express, SQLite u otros |br|
                    repositorios filebased.

/App_Start          Esta carpeta contiene |br|
                    algunas opciones de |br|
                    configuración básicas |br|
                    para su proyecto, |br|
                    incluyendo la definición |br|
                    de las rutas y los |br|
                    filtros y los paquetes |br|
                    de contenido.

/Areas              Áreas son una manera de |br|
                    dividir una aplicación |br|
                    grande en pedazos más pequeños

/bin                El ensamblado compilado |br|    Usted no verá el directorio bin |br|
                    para su aplicación MVC |br|     en la ventana Explorador de |br|
                    se coloca aquí, junto |br|      soluciones a menos que usted |br|
                    con los ensamblados de |br|     haga clic en el botón Mostrar |br|
                    referencia que no están |br|    todos los archivos. Dado que |br|
                    en la GAC.                      estos son archivos binarios |br|
                                                    generados en la compilación, |br|
                                                    que normalmente no debe |br|
                                                    almacenarlos en control de |br|
                                                    código fuente.

/Content            Aquí es donde se pone |br|      Esta es una convención, pero |br|
                    el contenido estático, |br|     no es necesario. Usted puede |br|
                    como archivos CSS e imágenes.   poner su contenido estático |br|
                                                    en cualquier lugar que más le convenga.

/Controllers        Aquí es donde usted pone |br|   Esta es una convención. Usted |br|
                    sus clases de controlador.      puede poner sus clases de |br|
                                                    controlador en cualquier lugar |br|
                                                    que te gusta, porque todos se |br|
                                                    compilan en el mismo ensamblado.

/Models             Aquí es donde usted pone |br|   Esta es una convención. Se |br|
                    su modelo de vista y las |br|   pueden definir las clases del |br|
                    clases del modelo de |br|       modelo en cualquier parte en |br|
                    dominio, a pesar de todo, |br|  el proyecto o en un proyecto |br|
                    pero las aplicaciones más |br|  independiente.
                    sencillas se benefician |br|
                    de la definición del |br|
                    modelo de dominio en un |br|
                    proyecto dedicado, como |br|
                    demostré para SportsStore.

/Scripts            Este directorio está |br|       Esta es una convención. Usted |br|
                    diseñado para mantener |br|     puede poner los archivos de |br|
                    las bibliotecas de |br|         script en cualquier lugar, ya |br|
                    JavaScript para su aplicación.  que son más que otro tipo de |br|
                                                    contenido estático.

/Views              Este directorio contiene |br|   The archivo ``/Views/web.config`` |br|
                    las vistas y las vistas |br|    impide IIS de servir el |br|
                    parciales, generalmente |br|    contenido de estos directorios. |br|
                    agrupadas en carpetas con |br|  Vistas deben ser prestados a |br|
                    el nombre después de que |br|   través de un método de acción.
                    el controlador con el que |br|
                    están asociados.

/Views/Shared       Este directorio contiene |br|
                    presentaciones y vistas |br|
                    que no son específicos de |br|
                    un solo controlador.

/Views/Web.Config   Este no es el archivo de |br|
                    configuración de la |br|
                    aplicación. Contiene la |br|
                    configuración necesaria |br|
                    para realizar visitas de |br|
                    trabajo con ASP.NET y |br|
                    evita que vistas de ser |br|
                    servido por IIS y los |br|
                    espacios de nombres |br|
                    importados en vistas de |br|
                    forma predeterminada.

/Global.asax        Esta es la clase de |br|
                    aplicación ASP.NET |br|
                    global. Su clase de |br|
                    código subyacente |br|
                    (``Global.asax.cs``) es |br|
                    el lugar para registrar |br|
                    la configuración de |br|
                    enrutamiento, así como la |br|
                    creación de cualquier |br|
                    código para ejecutarse en |br|
                    la aplicación de |br|
                    inicialización o apagado, |br|
                    o cuando se producen |br|
                    excepciones no controladas.
=================   ==============================  ==============================
