.. _reference-git-crear_repo_centralizado:

##############################
Crear repositorio centralizado
##############################

.. warning::
    Muchos de estos apuntes son viejos y pueden estar des actualizados.

**Fuentes**

* http://www.git-scm.com/book/es/Git-en-un-servidor-Preparando-el-servidor
* http://ymbra.com/es/blog/ramon/gestion-de-repositorios-git-con-gitosis
* http://www.git-scm.com/book/es/Git-en-un-servidor-Gitosis
* https://github.com/sitaramc/gitolite#readme

----

Opcion 1
********

Esta opción es crear un repositorio en ``/opt``, después creamos un usuario
(o varios) y le damos permisos con ``setfacl`` al/los usuarios creados en el repo.

Todos los usuarios asignados tendrán los mismos permisos, útil para poca gente
y de confianza.

Crear en el servidor remoto una carpeta para el proyecto.

.. code-block:: bash

    mkdir -p /opt/git/example.git
    cd /opt/git/example.git
    git init --bare

    # Crear usuario
    adduser user1
    passwd user1

Dar permisos al los usuarios.

.. code-block:: bash

    sudo setfacl -R -m u:user1:rwx -m u:userX:rwx /opt/git/example.git
    sudo setfacl -dR -m u:user1:rwx -m u:userX:rwx /opt/git/example.git

Si el repositorio local ya existe, y/o el remoto esta vacio.

.. code-block:: bash

    git remote add origin user1@ip:/opt/git/example.git
    git push origin master

Si el repositorio tiene contenido, simplemente un clone.

.. code-block:: bash

    git clone user1@ip:/opt/git/example.git

Opcion 2
********

Otra manera es crear un usuario en el sistema, por ejemplo "git" y poner en authorized_keys
los usuarios con acceso al repositorio.

.. code-block:: bash

    useradd -d /home/git -s /bin/bash -c 'git control version' git
    passwd git

Crear en el servidor remoto una carpeta, loguearse como git.

.. code-block:: bash

    mkdir -p /home/git/example.git
    cd /home/git/example.git
    git init --bare

Ahora los clientes remotos que quieran tener acceso de lectura/escritura
deberán proporcionar una clave rsa.

.. code-block:: bash

    ssh-keygen -t rsa

Subirlo de alguna manera al servidor, por ejemplo scp.

.. code-block:: bash

    scp id_rsa.pub git@ip_server:/tmp

Luego como usuario git en el server.

.. code-block:: bash

    echo /tmp/id_rsa >> .ssh/authorized_keys

Eliminar la id_rsa de tmp

.. code-block:: bash

    sudo rm -f /tmp/id_rsa.pub

Opcion 3 Gitosis
****************

.. warning::
    Si algún día lo hago, ordenarlo y presentarlo mejor.

| `Gitosis en git scm book <http://git-scm.com/book/es/Git-en-un-servidor-Gitosis/>`_
| `Gitosis en github <https://github.com/tv42/gitosis/>`_
|

Otra manera también es crear un server donde almacena todos los repositorios
de una manera muy cómoda.
``Probado en Centos 6.x``

**Fedora/Centos**

.. code-block:: bash

    useradd -d /home/git -s /bin/bash -c 'git control version' git

**Ubuntu**

.. code-block:: bash

    sudo adduser --system --shell /bin/sh --gecos 'git version control' --group --disabled-password --home /home/git git

Descargar el paquete gitosis.

.. warning::
    La instalación se ha de hacer clonando repositorio en github, Nota para hacer para
    la próxima vez.

Debemos tener una clave rsa o dsa publica, por ejemplo en /tmp.

.. note::
    No se si tengo que tener al usuario git en visudo.

.. code-block:: bash

    sudo -H -u git gitosis-init < /tmp/id_rsa.pub

Desde el pc local (cliente)

.. code-block:: bash

    git clone git@ip_server:gitosis-admin.git

Crear nuevo repositorio, desde el PC local

.. code-block:: bash

    cd gitosis-admin
    vim gitosis.conf

.. code-block:: bash

    [group project_example]
    memebers = snicoper@workspace.local
    writable = project_example

.. code-block:: bash

    git commit -am 'Dar permisos de escritura en project_example a snicoper'
    git push origin master

Ahora desde otro directorio crear una carpeta e inicializar un proyecto.

.. code-block:: bash

    mkdir project_example
    cd project_example
    git init
    git remote add origin git@ip_server:project_example

    # Crear archivos, etc
    git push origin master

Listo!!!

Añadir nuevos usuarios a proyectos
Para añadir un nuevo usuario con permisos de escritura, no es necesario
hacerlo desde el PC servidor, lo podemos hacer desde el PC de snicoper@workspace.local.

Necesitamos la key rsa publica del otro usuario id_rsa.pub

.. code-block:: bash

    cd gitosis-admin

Copiar y renombrar la clave rsa en gitosis-admin/keydir.

.. code-block:: bash

    cp /tmp/id_rsa.pub keydir/nombre.pub
    git add keydir/nombre.pub

Ahora hay que darle acceso, por ejemplo, al proyecto que hemos creado en el
apartado anterior. Abrimos el archivo gitosis.conf y modificamos la sección
pertinente:

.. code-block:: bash

    [group project_example]
    memebers = snicoper@workspace.local ([otro_nombre@nombre_maquina] | [otro_nombre(el del archivo .pub)])
    writable = project_example

Ahora el otro cliente ya podrá clonar y después pushes.

.. code-block:: bash

    git clone git@ip_server:project_example.git

Opcion 4 Gitolite
*****************

.. warning::
    Escribir documentación la próxima vez que la haga.

`Documentacion Ubuntu <https://help.ubuntu.com/14.04/serverguide/git.html>`_

.. note::
    Dejo en texto plano, los antiguos apuntes, pero son un poco liosos.

.. code-block:: none

    # Usando Gitolite
    # Fedora 20
    $ yum -y install gitolite3 python-setuptools perl-Time-HiRes

    Tener una id_rsa.pub

    Crea un usuario git si no existe

    # Fedora/Centos
    $ useradd -c 'git control version' git
    $ passwd git

    # Ubuntu
    $ sudo adduser --system --shell /bin/sh --gecos 'git version control' --group --disabled-password --home /home/git git

    $ su - git
    $ cd /home/git
    $ cp /tmp/id_rsa.pub ~/snicoper.pub

    ====================================
    Desde gitgub (Recomendado en Ubuntu)
    ====================================
    Añadir path en bashrc
    $ vim ~/.bashrc
    export PATH=~/bin:$PATH

    $ git clone git://github.com/sitaramc/gitolite
    $ mkdir -p $HOME/bin
    $ gitolite/install -to $HOME/bin
    ====================================

    $ gitolite setup -pk snicoper.pub

    Ahora para poder administrar los isuarios, debemos clonar gitolite-admin
    al pc local.
    $ cd Projects
    $ git clone git@ip_server:gitolite-admin

    Dentro de gitolite-admin hay 2 carpetas conf y keydir
    Para añadir usuarios con permisos añadir su id_rsa.pub (renombrado a nombre_usr.pub)
    a la carpeta keydir.
    Para añadir los diferenctes niveles y/o crear nuevos repositoios:
    $ vim conf/gitolite.conf
        repo example.dev
            RW+    = snicoper
            RW     = other_user
            R      = andother_user

    $ git add conf
    $ git add keydir
    $ git commit -m 'added snicoper, se dio acceso a other_user y a andother_user'
    $ git push

    Ahora gitolite en el servidor se encarga de añadir las claves rsa en authorized_keys
    y crea un repositorio vacio llamado example.dev.

    Para usar localmente el repo
    $ cd ~/carpeta
    $ git clone git@ip_server:example.dev

    Para ver una lista completa de los permisos
    https://github.com/sitaramc/gitolite#readme
    ACCESS RULES
