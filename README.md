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

### Introdução

[MySQL](https://www.mysql.com/) é um sistema de gerenciamento de banco de dados open-source, comumente instalado como parte da popular pilha [LAMP](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04) (Linux, Apache, MySQL, PHP/Python/Perl). Ele utiliza um banco de dados relacional e SQL (Linguagem de Consulta Estruturada) para gerenciar seus dados.

A versão curta da instalação é simples: atualize seu índice de pacotes, instale o `pacote mysql-server`, e então execute o script de segurança que vem incluído.

```
sudo apt update
sudo apt install mysql-server
mysql_secure_installation
```

Este tutorial irá explicar como instalar o MySQL versão 5.7 em um servidor Ubuntu 18.04. Contudo, se você estiver querendo atualizar uma instalação MySQL existente, você pode ler [esse guia de atualização do MySQL 5.7](https://www.digitalocean.com/community/tutorials/how-to-prepare-for-your-mysql-5-7-upgrade) em vez disso.



## Pré-requisitos

Para seguir esse tutorial, você vai precisar de:

- Um servidor Ubuntu 18.04 configurado seguindo [esse guia de configuração inicial de servidor](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04), incluindo um usuário com sudo que não seja root e um firewall.



## Passo 1 — Instalando o MySQL

No Ubuntu 18.04, somente a última versão do MySQL está incluída no repositório de pacotes APT por padrão. No momento em que escrevo, ela é a MySQL 5.7.

Para instalá-la, atualize o índice de pacotes em seu servidor e instale o pacote padrão com `apt`:

```
sudo apt update
sudo apt install mysql-server
```

Isso irá instalar o MySQL, mas não solicitará que você configure uma senha ou faça quaisquer outras alterações de configuração. Como isso deixa a sua instalação do MySQL insegura, vamos abordar isso a seguir.



## Passo 2 — Configurando o MySQL

Para novas instalações, você vai querer executar o script de segurança que está incluído. Isso altera algumas das opções padrão menos seguras para coisas como logins de root e usuários de exemplo. Em versões mais antigas do MySQL, você precisava inicializar o diretório de dados manualmente também, mas isso é feito automaticamente agora.

Execute o script de segurança:

```
sudo mysql_secure_installation
```

Isto irá levá-lo através de uma série de prompts onde você poderá realizar algumas alterações nas opções de segurança da sua instalação do MySQL. O primeiro prompt irá perguntar se você quer configurar o Plugin Validate Password, que pode ser utilizado para testar a força de sua senha do MySQL. Independentemente de sua escolha, o próximo prompt será para configurar a senha do usuário root do MySQL. Entre e então confirme uma senha segura de sua escolha.

A partir daí, você pode pressionar `Y` e então `ENTER` para aceitar as respostas padrão para todas as questões subsequentes. Isso irá remover alguns usuários anônimos e o banco de dados de teste, desativar login remoto para o root, e carregar todas essas novas regras para que o MySQL respeite imediatamente as alterações que você fez.

Para inicializar o diretório de dados do MySQL, você usaria `mysql_install_db` para versões anteriores à versão 5.7.6, e `mysqld --initialize` para versão 5.7.6 e posteriores. Contudo, se você instalou o MySQL da distribuição Debian, como descrito no Passo 1, o diretório de dados foi iniciado automaticamente; você não tem que fazer nada. Se você tentar executar o comando de qualquer maneira, você verá o seguinte erro:

Output

```
2018-04-23T20:11:15.998193Z 0 [ERROR] --initialize specified but the data directory has files in it. Aborting.
```

Finalmente, vamos testar a instalação do MySQL.



## Passo 3 — Testando o MySQL

Independentemente de como você o instalou, o MySQL deve ter iniciado executando automaticamente. Para testar isso, verifique seu status.

```
systemctl status mysql.service
```

Você verá uma saída similar à seguinte:

Output

```
● mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
   Active: active (running) since Wed 2018-04-23 21:21:25 UTC; 30min ago
 Main PID: 3754 (mysqld)
    Tasks: 28
   Memory: 142.3M
      CPU: 1.994s
   CGroup: /system.slice/mysql.service
           └─3754 /usr/sbin/mysqld
```

Se o MySQL não está executando, você pode iniciá-lo com `sudo systemctl start mysql`.

Para uma verificação adicional, você pode tentar se conectar ao banco de dados utilizando a ferramenta `mysqladmin`, que é um cliente que lhe permite executar comandos administrativos. Por exemplo, este comando diz para conectar como root (`-u root`), solicitar uma senha (`-p`), e retornar a versão.

```
sudo mysqladmin -p -u root version
```

Você deverá ver uma saída similar a essa:

Output

```
mysqladmin  Ver 8.42 Distrib 5.7.21, for Linux on x86_64
Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Server version      5.7.21-1ubuntu1
Protocol version    10
Connection      Localhost via UNIX socket
UNIX socket     /var/run/mysqld/mysqld.sock
Uptime:         30 min 54 sec

Threads: 1  Questions: 12  Slow queries: 0  Opens: 115  Flush tables: 1  Open tables: 34  Queries per second avg: 0.006
```

Isso significa que o MySQL está funcionando.



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
