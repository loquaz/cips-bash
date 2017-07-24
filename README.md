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
Português

O objetivo deste projeto é criar processos isolados para `sites php` usando o PHP-FPM. Este processo será de propriedade de um usuário linux. Para garantir isso, esse script cria um novo `usuário`,` grupo` e um `pool php-fpm`de propriedade do usuário.





