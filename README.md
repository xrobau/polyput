# Polyput

Simple script that handles PUT and HEAD requests from Polycom phones, so
you can finally disable your TFTP server.

This requires a new httpd configuration:

    <Directory /tftpboot>
      AddHandler php5-script .poly
      AddType text/html .poly
      RewriteEngine On
      RewriteCond %{REQUEST_METHOD} =PUT [OR]
      RewriteCond %{REQUEST_METHOD} =HEAD
      RewriteRule ^(.*)$ put.poly?url=$1
    </Directory>


