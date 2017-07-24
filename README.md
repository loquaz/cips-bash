# Create Isolated PHP Sites - cips-bash

This Project aim is to create a isolated environment owned by a specific linux user. To ensure this, this script creates a new `user`, `group` and a `php-fpm pool` owned by the user.

# Usage

Just download or clone the project and assign execute permission to the `create_site` file. 
```shell
sudo chmod +x create_site
```
Then type
```shell
sudo ./create_site <site name>
```
Português:
O objetivo deste projeto é criar um ambiente isolado controlado por um usuário linux específico. Para garantir isto, este script cria um novo `usuário`, `grupo` e um `pool php-fpm` controlado por este usuário.






