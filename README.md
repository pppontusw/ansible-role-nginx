# Ansible Role Nginx

## What does it do?

1. Installs Nginx
2. Creates an SSL certificate and DH parameter store location as defined in {{nginx_proxy_ssl_store_path}}
3. Generates secure DHparams (2048)
4. Copies all the SSL certificates and keys defined in ssl sites to your SSL store
5. Copies the custom Nginx configuration with only secure ciphers
6. Copies all of your virtual site configurations defined in defaults/main or {group,host}_vars to sites-available
7. Symlinks all of the above virtual sites to sites-enabled