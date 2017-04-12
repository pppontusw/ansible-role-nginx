# Ansible Role Nginx

## What does it do?

1. Installs Nginx
2. Creates an SSL certificate and DH parameter store location as defined in {{nginx_ssl_store_path}}
3. Generates secure DHparams (2048)
4. Copies all the SSL certificates and keys defined in ssl sites to your SSL store
5. Copies the custom Nginx configuration with only secure ciphers
6. Copies all of your virtual site configurations defined in defaults/main or {group,host}_vars to sites-available
7. Symlinks all of the above virtual sites to sites-enabled


## Variables

```
# This is quite an extensive list of variables you can set in order to create all the virtual sites, copy certificates etc.
# You probably do not want to manage this in the defaults/main file but rather copy this into your group_vars or host_vars
# and then comment out everything here or remove the defaults file altogether as it is really only here to show all the options

# some defaults
nginx_path: /etc/nginx
nginx_process_name: nginx
nginx_pkg_name: nginx
nginx_user: www-data
nginx_group: www-data

dh_size: 2048

# define path to store certificates
nginx_ssl_store_path: '/ssl'
#

firewalld_open_ports:
  - 80
  - 443

nginx_copy_ssl:
  - name: fullchain.pem
    content: "certhere"
  - name: priv.key
    content: "keyhere"

nginx_fail2ban: yes

nginx_vhosts:
  - name: test
    content: |
     nginx_full_vhost
```