# Create Isolated PHP Sites - cips-bash

This Project aim is to create a isolated processes for `php enabled sites` using PHP-FPM. This process will be owned by a specific linux user. To ensure this, this script creates a new `user`, `group` and a `php-fpm pool` owned by the user.

# Usage

Just download or clone the project and assign execute permission to the `create_site` file. 
```shell
sudo chmod +x create_site
```
Then type
```shell
sudo ./create_site <site name>
```

# How It Works?

In order

* Check if `php` is installed and his version is greater than or equals to 5.x
* Check if `nginx` webserver is installed
* Check if `php-fpm` is installed and his version is greater than or equals to 5.x
* Creates a new linux `user` and `group` with the same name of the site
* Creates the following directories:
  * `/var/www/<site name>` (to hold site files)
  * `/var/log/nginx/<site name>`  (to hold site log files)
  * `/var/lib/mysql/<site name>` (if you plan to use mysql as database)

After the directory and user creation phases, the script will create a new `php-fpm` pool configuration under `/etc/<php path>/fpm/pool.d/<site name>.conf` using `templates/php_fpm_pool.template` as template. Feel free to modify this file to match your own needs.   
Português

O objetivo deste projeto é criar processos isolados para `sites php` usando o PHP-FPM. Este processo será de propriedade de um usuário linux. Para garantir isso, esse script cria um novo `usuário`,` grupo` e um `pool php-fpm`de propriedade do usuário.





