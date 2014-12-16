# Nginx ('nginx')

**Part of the BAS Ansible Role Collection (BARC)**

Installs Nginx web-sever using default virtual host

## Overview

* Installs Nginx server.
* Configures default virtual host for HTTP connections, if a non-default document root is used the virtual server will be configured to point to this location.
* Optionally configures virtual host for HTTPS connections, if a non-default document root is used the virtual host will be configured to point to this location.
* The app user is made a member of the `www-data` group and ownership of the default document root is set to the 'app' user.

## Availability

This role is designed for internal use but if useful can be shared publicly.

## Usage

### Requirements

#### BAS Ansible Role Collection (BARC)

* `core`

#### Other

If using SSL the certificate and private key used must be accessible on the server, then use the `nginx_default_var_www_ssl_cert` and `nginx_default_var_www_ssl_key` variables to point to this location. It is out of scope to do this in this role (as the certificate may be used in multiple web-servers).

### Variables

Variables used in default virtual host `/etc/nginx/sites-available/default`:

* `nginx_app_user_username`
    * The username of the app user, used for day to day tasks, if enabled
    * This variable **must** be a valid unix username
    * Default: "app"
* `nginx_default_var_www_document_root`
	* Location on server containing site files. 
	* If a non-default root is used ensure the `www-data` group has access.
    * Default: "/var/www/"
* `nginx_default_var_www_ssl_enabled`
    * Boolean value for enabling SSL support 
    * Default: "false"
* `nginx_default_var_www_ssl_cert_path`
    * Path, without a trailing slash, to the directory holding the SSL certificate 
    * Default: "/vagrant/data/certificates"
* `nginx_default_var_www_ssl_key_path`
    * Path, without a trailing slash, to the directory holding the SSL private key 
    * Default: "{{ nginx_default_var_www_ssl_cert_path }}" (i.e. same directory as `nginx_default_var_www_ssl_cert_path`)
* `nginx_default_var_www_ssl_cert_file`
    * File name (including extension) of SSL certificate in `nginx_default_var_www_ssl_cert_path`
    * Default: "cert.cer"
* `nginx_default_var_www_ssl_key_file`
    * File name (including extension) of SSL private key in `nginx_default_var_www_ssl_key_path`
    * Default: "cert.key"

## Contributing

This project welcomes contributions, see `CONTRIBUTING` for our general policy.

## Developing

### Committing changes

The [Git flow](https://github.com/fzaninotto/Faker#formatters) workflow is used to manage development of this package.

Discrete changes should be made within *feature* branches, created from and merged back into *develop* (where small one-line changes may be made directly).

When ready to release a set of features/changes create a *release* branch from *develop*, update documentation as required and merge into *master* with a tagged, [semantic version](http://semver.org/) (e.g. `v1.2.3`).

After releases the *master* branch should be merged with *develop* to restart the process. High impact bugs can be addressed in *hotfix* branches, created from and merged into *master* directly (and then into *develop*).

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the BAS Web & Applications Team Jira project ([BASWEB](https://jira.ceh.ac.uk/browse/BASWEB)).

## License

Copyright 2014 NERC BAS. Licensed under the MIT license, see `LICENSE` for details.
