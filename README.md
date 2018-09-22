# php-ambiente
Repositório de anotações de configuração PHP sem uso de Docker

# Linux
#### Voce pode escolher instalar via LAMP ou manualmente

* Linux (sistema operacional),
* Apache (servidor web),
* MariaDB ou MySQL (software de banco de dados) e
* PHP (linguagens de programação) ou Python,

### Via LAMP
1- Necessario instalacao: https://bitnami.com/stack/lamp/installer 

2- Logo apos a instalacao do mesmo, provavel de usar um IDEA. Escolha a de sua preferencia. 

3- Recomenda-se PhpStorm da Jetbrains: https://www.jetbrains.com/phpstorm/ 

3.1 - `opcional` instale configuracoes em seu phpStorm, inclusive esquema de cor Monokai Web: https://github.com/gabriel-roque/Jetbrains--Config

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

### Verifique a versao do seu php

```
php -v
```

##### *Obs: porem se faz necessario a instalacao da dependecia do php-cgi*

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

![](/home/gabriel-odyssey/Imagens/Screenshot_20180922_141509.png)



6- Feito a substiucao da pasta, basta abrir seu LAMP e ser feliz!

*mesmo procedimento sever para versoes posteriores, caso nao venha nativo de seu OS ou do LAMP*