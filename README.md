# PHP SSH

Simples gerenciador de conexões SSH em PHP utilizando a lib SSH2

## Instalação
Para instalar esta dependência bas executar o comando abaixo:
```shell
composer require goofybnu/php-ssh
```

## Utilização

Para user este gerenciador basta seguir o exemplo abaixo:
```php
<?php

require __DIR__ . '/vendor/autoload.php';

// DEPENDÊNCIAS
use GoofyBNU\SecureShell\SSH;

// INSTÂNCIA
$objSSH = new SSH;

// CONEXÃO
if (!$objSSH->connect('127.0.0.1', 22)) die('Conexão falhou');

// AUTENTICAÇÃO
if (!$objSSH->authPassword('demo', '123456')) die('Autenticação falhou');

// EXECUTA COMANDOS
$stdIo = $objSSH->exec('ls -l', $stdErr);
echo "STDERR: \n" . $stdErr;
echo "STDIO: \n" . $stdIo;

// DESCONECTA
$objSSH->disconnect();

```

## Requisitos
- Necessário PHP 7.0 ou superior
- Necessário ter a lib SSH2 instalada e ativa