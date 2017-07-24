# Create Isolated PHP Sites | cips-bash

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

After the directory and user creation phases, the script will create a new `php-fpm` pool configuration under `/etc/<php path>/fpm/pool.d/<site name>.conf` using `templates/<php version folder>/php_fpm_pool.template` as template. Feel free to modify this file to match your own needs.

TODO

 * Fix a lot of bugs
 * Add messages in other languages than portuguese
 * Allow more flexibility by adding options

# Português

O objetivo deste projeto é criar processos isolados para `sites php` usando o PHP-FPM. Este processo será de propriedade de um usuário linux. Para garantir isso, esse script cria um novo `usuário`,` grupo` e um `pool php-fpm`de propriedade do usuário.

# Uso

Faça download ou clone o projeto e dê permissão de execução ao arquivo `create_site`. 
```shell
sudo chmod +x create_site
```
Então digite
```shell
sudo ./create_site <nome do site>
```

# Como funciona?

Na ordem

* Checa se o `php` está instalado e sua versão é igual ou maior que 5.x
* Checa se o `nginx` webserver está instalado
* Checa se o `php-fpm` está instalado e sua versão é igual ou maior que 5.x
* Cria um novo `usuário` e `grupo` com o mesmo nome do site
* Cria os seguintes diretórios:
  * `/var/www/<nome do site>` (aqui ficaram os arquivos do site)
  * `/var/log/nginx/<nome do site>`  (arquivos de log)
  * `/var/lib/mysql/<nome do site>` (para armazenar arquivos do mysql caso você pretenda usar)

Depois da fase de criação de diretórios, o script cria uma nova configuração para o pool `php-fpm` no caminho `/etc/<php path>/fpm/pool.d/<site name>.conf` usando `templates/<pasta com a versão do php>/php_fpm_pool.template` como template. Sinta-se livre para modificar este arquivo com suas próprias configurações.

# !Importante!

O aproach seguido, foi baseado neste tutorial [How To Host Multiple Websites Securely With Nginx And Php-fpm On Ubuntu 14.04 ] (https://www.digitalocean.com/community/tutorials/how-to-host-multiple-websites-securely-with-nginx-and-php-fpm-on-ubuntu-14-04) Esta é uma versão alpha que está sendo testada em container docker. Está em fase inicial de desenvolvimento e ainda há muito trabalho a ser feito até atingir o estágio de versão estágio. Quem quiser, pode se envolver no projeto, corrigingo bugs, traduzindo, apontando possíveis usos. Sinta-se a vontade.
Para entrar em contato mande-me um email para: sereno.desenvolvimento@gmail.com

TODO

 * Resolver um monte de bugs
 * Dar suporte a outras linguas (as mensagens estão direto nas functions, retirar isso pra um arquivo separado)
 * Dar a possibilidade do usuário informar opções ao executar o script





