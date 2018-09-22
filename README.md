# php-ambiente
![apm](https://img.shields.io/badge/NOTES-update-blue.svg?longCache=true&style=flat-square)

Repositório de anotações de configuração PHP sem uso de Docker

# Linux
#### Há a opção de escolher instalar via LAMP ou manualmente

* Linux (sistema operacional),
* Apache (servidor web),
* MariaDB ou MySQL (software de banco de dados) e
* PHP (linguagens de programação) ou Python,

### Via LAMP
1- Necessário instalação: https://bitnami.com/stack/lamp/installer 

2- Logo apos a instalação do mesmo, provável de usar uma IDEA. Escolha a de sua preferência. 

3- Recomenda-se PhpStorm da Jetbrains: https://www.jetbrains.com/phpstorm/ 

3.1 - `opcional` instale configurações em seu phpStorm, inclusive esquema de cor Monokai Web 
https://github.com/gabriel-roque/Jetbrains--Config

4 - Abra o terminal e uso execute o seguintes comandos:

```
apt-get update && apt-get upgrade
```

### Add o PHP repository

Adicionando php em seus repositorios de att

```
add-apt-repository ppa:ondrej/php
```

##### Update

```
apt-get update
```

### Install PHP 7.2

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

### Verifique a versão do seu php

```
php -v
```

##### *Obs: porem se faz necessario a instalação da dependêcia do php-cgi*

> retire as " " e coloque as versao ex: 7.2

```
sudo apt-get install php"versao do seu php"-cgi
```

```
sudo apt-get install php7.2-cgi
```

5- Basta copiarmos o a pasta php e colaca-la na pasta do LAMP

`/home/nome-do-computador/lampstack-7.0.32-0/php` 

sera substituida pela pasta que esta em:

`/etc/php/`

![](https://i.imgur.com/3PuJSlb.png)


6- Feito a substiução da pasta, basta abrir seu LAMP e ser feliz!

*mesmo procedimento sever para versoes posteriores, caso nao venha nativo de seu OS ou do LAMP*

### Manualmente

##### Instalar o Apache

Para instalar o Apache, abra o terminal e digite os seguintes comandos:
`sudo apt-get updatesudo apt-get install apache2`

##### Install MySQL

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

##### Instalar o php, segue o mesmo processo do LAMP

#### Install Composer

1- Basta executar o comando para instalar

`sudo apt install composer`

2- Execute o comando para verificar 

`composer -v`

3- Finalizado, Bom coder! 
