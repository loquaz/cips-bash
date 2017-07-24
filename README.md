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

After that, there should be a running site using an dedicated php-fpm pool owned by the site owner. This user has the same name provided as site name. The pool configuration file will be in:  `path /etc/<php version>/fpm/pool.d/<nome do site>.conf`.

Example: if the site's name provided as argument to the script is  `api_v2` in an environment with php5` and `php5-fpm` enabled, then, a pool configuration file will be created under the path:

```bash
/etc/php5/fpm/pool.d/api_v2.conf
```

You can open this file and made your own changes to configure the pool. You must to restart the `php-fpm` service. In Debian based distros (Ubuntu is a Debian based distro) you can list these services by typing the following command: `ls /etc/init.d/`. To list only the php-fpm related services type:


```bash
ls /etc/init.d/ | egrep '^php.+-fpm$'
```
This command lists only services related to `php-fpm`. The regular expression provided as argument to the egrep command `'^php.+-fpm$'`, matches all services that begins with `php` and ends with `-fpm`.

If the outut result is `php5-fpm`, so you must to type: 

```bash
sudo service php5-fpm restart
```

In case of failure, check the fpm log file under `/var/log/<service name>.log`. In our case, the complete path to this file is: `/var/log/php5-fpm.log`. 

You can use an text editor to browse the file contents or you can type: 

```bash
cat /var/log/php5-fpm.log
```

To see the file contents in the default stdout, in this case, the terminal.

# !Important!

The followed approach to do this tool was based in this tutorial [How To Host Multiple Websites Securely With Nginx And Php-fpm On Ubuntu 14.04 ](https://www.digitalocean.com/community/tutorials/how-to-host-multiple-websites-securely-with-nginx-and-php-fpm-on-ubuntu-14-04).

This is a alpha version tested only in docker containers. The development is in this initial phase and there are a lot of work to be done until a stable version be releasead. You can contribute to this project if you want by doing one of these thigs: finding bugs, correcting the code, translating, pointing possibles use cases. Feel free to do what you want.
You can contact me at: sereno.desenvolvimento@gmail.com

TODO

- [ ] Fix a lot of bugs
- [ ] Add messages in other languages than portuguese
- [ ] Allow more flexibility by adding options
- [ ] Write documentation
- [ ] Build a docker image that will contain this tool as a default system tool

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

Depois disso, deverá existir um site em funcionamento, usando um php-fpm pool próprio, controlado pelo usuário de mesmo nome do site. O arquivo de configuração do pool será: `path /etc/<versao php>/fpm/pool.d/<nome do site>.conf`.

Exemplo: caso o nome do site passado como argumento para o script seja `api_v2` em um ambiente com `php5` e `php5-fpm` habilitado, Será criado então um arquivo de configuração do pool no caminho:
```bash
/etc/php5/fpm/pool.d/api_v2.conf
```

Você pode abrir este arquivo e configura-lo do jeito que quiser. Mas não esqueça de reiniciar o serviço php-fpm rodando na sua máquina. Em ambientes baseados em Debian (Ubuntu é baseado no Debian) você pode listar estes serviços digitando o seguinte comando `ls /etc/init.d/`. Para listar apenas os serviços instalados pelo php-fpm digite:

```bash
ls /etc/init.d/ | egrep '^php.+-fpm$'
```

Este comando irá listar apenas os serviços relativos a `php-fpm`. E expressão regular fornecida como parametro pro comando egrep `'^php.+-fpm$'`,  vai encontrar todos os serviços começando em `php` e que terminam com `-fpm`.

Caso o resultado seja `php5-fpm`, digite então: 

```bash
sudo service php5-fpm restart
```

Em caso de falha, confira o log do fpm que geralmente encontra-se em `/var/log/<nome do serviço>.log`. No nosso caso, o caminho completo para este arquivo é: `/var/log/php5-fpm.log`.

Você pode usar um editor de texto para ver as mensgens dentro deste arquivo ou pode simplestemente digitar: 

```bash
cat /var/log/php5-fpm.log
```

para ver o conteúdo do arquivo na saída padrão, neste caso o próprio terminal.

# !Importante!

O aproach seguido, foi baseado neste tutorial [How To Host Multiple Websites Securely With Nginx And Php-fpm On Ubuntu 14.04 ](https://www.digitalocean.com/community/tutorials/how-to-host-multiple-websites-securely-with-nginx-and-php-fpm-on-ubuntu-14-04) Esta é uma versão alpha que está sendo testada em container docker. Está em fase inicial de desenvolvimento e ainda há muito trabalho a ser feito até atingir o estágio de versão estágio. Quem quiser, pode se envolver no projeto, corrigingo bugs, traduzindo, apontando possíveis usos. Sinta-se a vontade.
Para entrar em contato mande-me um email para: sereno.desenvolvimento@gmail.com

TODO

- [ ] Resolver um monte de bugs
- [ ] Dar suporte a outras linguas (as mensagens estão direto nas functions, retirar isso pra um arquivo separado)
- [ ] Dar a possibilidade do usuário informar opções ao executar o script
- [ ] Escrever documentação
- [ ] Construir uma imagem docker que usará o script como ferramenta default





