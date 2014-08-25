.. _reference-linux-fedora-centos-postfix:

#######
Postfix
#######

.. note::
    Todo se hace con root excepto si se dice lo contrario.

-------------------

Servidor postfix
****************

Instalación de postfix.

.. code-block:: bash

    yum install -y postfix

Editar archivo de configuración.

.. code-block:: bash

    vim /etc/postfix/main.cf

.. code-block:: bash

    # line 75: uncomment and specify hostname
    myhostname = mail.workspace.local

    # line 83: uncomment and specify domain name
    mydomain = workspace.local

    # line 99: uncomment
    myorigin = $mydomain

    # line 113: uncomment
    inet_interfaces = all

    # line 116: comment
    # inet_interfaces = localhost

    # line 164: comentar
    #mydestination = $myhostname, localhost.$mydomain, localhost

    # line 165: descomentar
    mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

    # line 264: uncomment and specify your LAN
    mynetworks = 192.168.0.0/24, 127.0.0.0/8

    # line 419: uncomment (use Maildir)
    home_mailbox = Maildir/

    # line 548: uncomment
    header_checks = regexp:/etc/postfix/header_checks

    # line 549: añadir
    body_checks = regexp:/etc/postfix/body_checks

    # line 574: add
    smtpd_banner = $myhostname ESMTP

    # add at the last line

    # limit an email size 10M
    message_size_limit = 10485760

    # limit mailbox 1G
    mailbox_size_limit = 1073741824

    # for SMTP-Auth settings
    smtpd_sasl_type = dovecot
    smtpd_sasl_path = private/auth
    smtpd_sasl_auth_enable = yes
    smtpd_sasl_security_options = noanonymous
    smtpd_sasl_local_domain = $myhostname
    smtpd_client_restrictions = permit_mynetworks,reject_unknown_client,permit
    smtpd_recipient_restrictions = permit_mynetworks,permit_auth_destination,permit_sasl_authenticated,reject

.. code-block:: bash

    vim /etc/postfix/header_checks

.. code-block:: bash

    # add at the head
    # reject if email address is empty
    /^From:.*<#.*@.*>/ REJECT
    /^Return-Path:.*<#.*@.*>/ REJECT

.. code-block:: bash

    vim /etc/postfix/body_checks

.. code-block:: bash

    # reject if includes 'example.com' in mail body
    /^(|[^>].*)example.com/ REJECT

Dovecot
*******

.. code-block:: bash

    yum install -y dovecot

.. code-block:: bash

    vim /etc/dovecot/dovecot.conf

.. code-block:: bash

    # line 24: uncomment
    protocols = imap pop3 lmtp

.. code-block:: bash

    vim /etc/dovecot/conf.d/10-auth.conf

.. code-block:: bash

    # line 10: uncomment and change ( allow plain text auth )
    disable_plaintext_auth = no

.. code-block:: bash

    auth_mechanisms = plain login

.. code-block:: bash

    vim /etc/dovecot/conf.d/10-mail.conf

.. code-block:: bash

    # line 30: uncomment and add
    mail_location = maildir:~/Maildir

.. code-block:: bash

    vim /etc/dovecot/conf.d/10-master.conf

.. code-block:: bash

    # line 96: uncomment and add

    # Postfix smtp-auth
    unix_listener /var/spool/postfix/private/auth {
        mode = 0666
        user = postfix # add
        group = postfix # add
    }

.. code-block:: bash

    vim /etc/aliases

.. code-block:: bash

    # En la ultima linea agregar
    root: snicoper

.. important::
    | Ver :ref:`reference-linux-fedora-centos-reglas_selinux`
    | Para crear el certificado SSL, :ref:`reference-linux-fedora-centos-crear_ssl`

.. code-block:: bash

    vim /etc/postfix/main.cf

.. code-block:: bash

    # add at the last line
    # SSL
    smtpd_use_tls = yes
    smtpd_tls_cert_file = /etc/pki/tls/certs/workspace.crt
    smtpd_tls_key_file = /etc/pki/tls/certs/workspace.key
    smtpd_tls_session_cache_database = btree:/etc/postfix/smtpd_scache

.. code-block:: bash

    vim /etc/postfix/master.cf

.. code-block:: bash

    # Descomentar linea 16
    smtps       inet   n       -       n       -       -       smtpd

    # Descomentar lineas 27 y 28
    -o syslog_name=postfix/smtps
    -o smtpd_tls_wrappermode=yes

.. code-block:: bash

    vim /etc/dovecot/conf.d/10-ssl.conf

.. code-block:: bash

    # line 6: uncomment
    ssl = yes

    # line 14,15: comentar
    # line 16: añadir and specify certificate
    ssl_cert = </etc/pki/tls/certs/workspace.crt
    ssl_key = </etc/pki/tls/certs/workspace.key

    systemctl start postfix.service
    systemctl enable postfix.service
    systemctl start dovecot.service
    systemctl enable dovecot.service

Firewall
********

.. code-block:: bash

    firewall-cmd --permanent --zone=public --add-service=smtp
    systemctl restart firewalld.service

Lista de puertos por defecto
============================

.. code-block:: bash

    POP3 - port 110
    IMAP - port 143
    SMTP - port 25
    HTTP - port 80
    Secure SMTP (SSMTP) - port 465
    Secure IMAP (IMAP4-SSL) - port 585
    IMAP4 over SSL (IMAPS) - port 993
    Secure POP3 (SSL-POP) - port 995
