.. _reference-linux-fedora-centos-configurar_ssh:

##############
Configurar SSH
##############

Configuracion basica de ``SSH``

.. code-block:: bash

    yum install ssh

    systemctl start sshd.service
    systemctl enable sshd.service

Editamos el archivo de configuracion de ssh

.. code-block:: bash

    vim /etc/ssh/sshd_config

.. code-block:: bash

    # Linea 17, descomentar y cambiar puerto por defecto
    Port 50022

    # line 48: uncomment and change 'no'
    PermitRootLogin no

    # line 77: uncomment
    PermitEmptyPasswords no # Se tendra que crear un passphare con pass

    # line 78:
    PasswordAuthentication yes

    # Añadir al final
    AllowUsers snicoper

Si se cambia el puerto por defecto y SELinux esta activado

.. code-block:: bash

    semanage port -a -t ssh_port_t -p tcp PUERTO_NUEVO

Crear una clave rsa, desde el cliente/clientes

.. code-block:: bash

    ssh-keygen -t rsa

Subirla al servidor

.. code-block:: bash

    scp .ssh/id_rsa.pub snicoper@ns1.workspace.local:

En el servidor, como **usuario**

.. code-block:: bash

    mkdir .ssh
    chmod 700 .ssh
    touch .ssh/authorized_keys
    chmod 600 .ssh/authorized_keys
    cat id_rsa.pub > .ssh/authorized_keys

Firewalld

.. code-block:: bash

    firewall-cmd --permanent --zone=public --add-service=ssh

    # Si es un puerto distinto al 22
    firewall-cmd --permanent --zone=public --add-port=puerto/tcp
