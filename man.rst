cdist-type__ungleich_nginx_app_proxy(7)
=======================================
Application proxy via nginx

ungleich GmbH <cdist--@--ungleich.ch>


DESCRIPTION
-----------
Provides an application proxy for various applications.
Supported applications / frameworks: 

- Jetty
- PHP
- RubyOnrails, 
- Opennebula Sunstone (without VNC Proxy)

Planned: 

- django / uwsgi.

This type was developed and sponsored by Panter AG (www.panter.ch).


REQUIRED PARAMETERS
-------------------
config
    Which application proxy to provide


OPTIONAL PARAMETERS
-------------------
ssl-name
    Select the ssl certificate

ssl-custom-redirect
    Define where to redirect for ssl instead of $host

domain
    Define the domain for Let's Encrypt

BOOLEAN PARAMETERS
------------------
ssl
    Enable SSL

ssl-no-redirect
    Disable http -> https redirect (both http and https are accessable)

letsencrypt
    Enable Let's Encrypt for SSL

custom-config-from-stdin
    Insert this configuration from stdin after the generic part


EXAMPLES
--------

.. code-block:: sh

    __ungleich_nginx_app_proxy --config rails

    __ungleich_nginx_app_proxy --config jetty --ssl

    # Select certificate below /etc/ssl/certs/${ssl_name}.crt
    # Select key below /etc/ssl/private/${ssl_name}.key
    __ungleich_nginx_app_proxy --config jetty --ssl \
        --ssl-name test.example.org

    __ungleich_nginx_app_proxy --config rails --letsencrypt --domain test.example.org
    
    __ungleich_nginx_app_proxy --config rails --custom-config-from-stdin << eof

        # some aditional nginx config

    eof


SEE ALSO
--------
- `cdist-type(7) <cdist-type.html>`_


COPYING
-------
Copyright \(C) 2013-2015 ungleich GmbH (www.ungleich.ch). 
Free use of this software is granted under the terms 
of the GNU General Public License version 3 (GPLv3).
