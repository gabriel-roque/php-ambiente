# Ambiente PHP Linux
![apm](https://img.shields.io/badge/NOTES-update-blue.svg?longCache=true&style=flat-square)

Repositório de anotações de configuração PHP sem uso de Docker

### Sumário

* [Apache](#apache)
* [PHP](#php)
* [Mysql](#mysql)
* [Composer](#composer)
* [Laravel](#laravel)
* [Upgrade bash git](#melhorando-seu-terminal-shell-bash---git)


# Apache

## How to Install PHP 7.2 on Ubuntu 18.04



PHP 7.2 is included by default in Ubuntu’s repositories since version 18.04. So the instructions are pretty similar to PHP 7 for 16.04.

### Update Ubuntu

Again, before doing anything, you should update your server:

```
apt-get update && apt-get upgrade
```

### Install PHP 7.2

Next, to install PHP 7.2 on Ubuntu 18.04, just run the following command:

```
apt-get install php
```

This command will install PHP 7.2, as well as some other dependencies.

To verify if PHP is installed, run the following command:

```
php -v
```

You should get a response similar to this:

```
PHP 7.2.3-1ubuntu1 (cli) (built: Mar 14 2018 22:03:58) ( NTS )
```

And that’s it. PHP 7.2 is installed on your Ubuntu 18.04 server.

### Install PHP 7.2 modules

These are the most common PHP 7.2 modules often used by php applications. You may need more or less, so check the requirements of the software you’re planning to use:

```
apt-get install php-pear php-fpm php-dev php-zip php-curl php-xmlrpc php-gd php-mysql php-mbstring php-xml libapache2-mod-php
```

To check all the PHP modules available in Ubuntu, run:

```
apt-cache search --names-only ^php
```



# PHP

1. Abra o terminal e uso execute o seguintes comandos:

```
apt-get update && apt-get upgrade
```

2. Adicionando php em seus repositorios de att

```
add-apt-repository ppa:ondrej/php
```

3. Update

```
apt-get update
```

4. Install PHP 7.2

```
apt-get install php7.2
```

Ele ira realizar os install dessas dependencias:

- libapache2-mod-php7.2
- libargon2-0
- libsodium23
- libssl1.1
- php7.2-cli
- php7.2-common
- php7.2-json
- php7.2-opcache
- php7.2-readline

5. Verifique a versão do seu php

```
php -v
```

***Obs: porem se faz necessario a instalação da dependêcia do php-cgi***

> retire as " " e coloque as versao ex: 7.2

```
sudo apt-get install php"versao do seu php"-cgi
```

```
sudo apt-get install php7.2-cgi
```

5- Basta Mapearmos nossa php na IDEA que esta rodando 100%



# MySQL

1- Para instalar MySQL, abra o terminal e digite os seguintes comandos:
`sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql`

2- Para fazer a configuração inicial, execute script:
`sudo /usr/bin/mysql_secure_installation`

3- O prompt irá pedir sua senha de root atual.
`Enter current password for root (enter for none):`

OK, successfully used password, moving on…
Em seguida, o prompt irá perguntar se você deseja alterar a senha de root. 

Vá em frente e escolher N e passar para as próximas etapas.

É mais fácil apenas para dizer Sim para todas as opções. No final, o MySQL irá recarregar e implementar as novas alterações.



# Composer

1- Basta executar o comando para instalar

`sudo apt install composer`

2- Execute o comando para verificar 

`composer -v`

3- Finalizado, Bom coder! 



# Laravel

O primeiro requisito é o php, com o terminal aberto digite o seguinte comando.

```
sudo apt-get install php
```

Para verificar a versão do php.

```
php -v
```

Instale também a extensão Mbstring do php.

```
sudo apt-get install php7.2-mbstring
```

A extensão do suporte para o XML.

```
sudo apt-get install php-xml
```

E a extensão do zip do php.

```
sudo apt-get install php7.2-zip
```

Caso não tenha instalado o curl na sua máquina digite:

```
sudo apt-get install curl
```

O Laravel utiliza o composer para cuidar das suas dependências, então o próximo passo é instalar o [Composer](https://getcomposer.org/).

Esse comando faz o download do instalador do composer e realiza a instalação dele no diretório correto, para o composer funcionar de forma global no sistema.

```
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```

Para ver se deu certo, digite composer no terminal.

![img](https://cdn-images-1.medium.com/max/800/1*cjrD7IcQRRWx0KsjxqAypQ.png)

Mude as permissões para rodar o composer sem o sudo

```
sudo chown -R $USER ~/.composer/
```

Também, é possível inicializar um projeto Laravel sem o seu instalador usando o seguinte comando.

```
composer create-project --prefer-dist laravel/laravel project-name
```

Nesse tutorial vou instalar o instalador do Laravel pelo Composer para utilizar o comando *laravel new project*.

```
composer global require "laravel/installer"
```

Para o comando *laravel* funcionar precisamos adicionar uma linha no arquivo*bashrc* se você estiver usando apenas o terminal.

```
echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Ou adicionar uma linha no *zshrc* se estiver usando o [ZSH](https://medium.com/@rgdev/como-instalar-oh-my-zsh-c0f96218fd90).

```
echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >>  ~/.zshrc
source ~/.zshrc
```

Reinicie o terminal. Para testar se deu certo, digite *laravel* no terminal.

Agora vamos inicializar um projeto Laravel.

```
laravel new blog
```



![img](https://cdn-images-1.medium.com/max/800/1*NYgOBZT85LWM0pKjBRY2Wg.png)

Rode o servidor do Laravel. Enjoy!



# Melhorando seu terminal shell bash - Git

> Provavel de estar usando o terminal bash, o mesmo nao indica a branch que voce se encontra, porem ha solucao para seus problemas

1- Instalar git

`sudo apt install git`

2- Instalar vim

`sudo apt install vim`

3- Abra terminal

`sudo vim .bashrc`

4- Habilite as linhas, escreva esse comando com o vim aberto

`:set number`

5- Escreva esse comando com o vim aberto

`/PS1`

6- Comente a linha de codigo PS1 com # antes do comando

7- Insira essa linha de codigo abaxo

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]$(__git_ps1 " (%s)"
)\$ 
```

8- Seja feliz e nao de commit na branch errada!
