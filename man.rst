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
dh
    Keysize for Diffie-Hellman. A size of 2048 bit is recommended.


OPTIONAL PARAMETERS
-------------------

ssl-custom-redirect
    Define where to redirect for ssl instead of $host

ssl-cert
    Define the path where the ssl-cert is on the $host

ssl-key
    Define the path where the ssl-key is on the $host
   


BOOLEAN PARAMETERS
------------------
ssl
    Enable SSL 

ssl-no-redirect
    Disable http -> https redirect (both http and https are accessable)

custom-config-from-stdin
    Insert this configuration from stdin after the generic part


EXAMPLES
--------

.. code-block:: sh

    __ungleich_nginx_app_proxy --config rails --dh 2048

    # Select a certificate on your machine
    __ungleich_nginx_app_proxy --config rails --dh 2048 \
    --ssl --ssl-cert "/etc/ssl/certs/ssl-cert-snakeoil.pem" \
    --ssl-key "/etc/ssl/private/ssl-cert-snakeoil.key"

    # Example when you want to use Let's Encrypt
    __ungleich_nginx_app_proxy  --config rails --dh 2048 \
    --ssl --ssl-cert "/etc/letsencrypt/live/test.example.org/fullchain.pem" \
    --ssl-key  "/etc/letsencrypt/live/test.example.org/privkey.pem"

    __ungleich_nginx_app_proxy --config rails --dh 2048 --custom-config-from-stdin << eof

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
