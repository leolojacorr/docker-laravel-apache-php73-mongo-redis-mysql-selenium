# docker-laravel-apache-php73-mongo-redis-mysql-selenium


## Como usar em varios projetos
Coloque estes arquivos no mesmo diretorio raiz do site
- Rode docker-compose up
- Acesse http://localhost/nomeprojeto

## Como usar somente em um projeto
- Estes arquivos devem estar dentro do projeto
- Copie as configuracoes do .env para o .env do projeto
- Copie o arquivo docker-compose.yml
- Copie a pasta docker
- Rode docker-compose up
- Acesse http://localhost 

## Para enviar email
.env
```
MAIL_DRIVER=smtp
MAIL_HOST=mail
MAIL_PORT=1025
```
Para ler as mensagens: http://localhost/1085

### /.env
Configuracoes usadas no docker-compose.yml

```
# DOCKER
## webserver
APACHE_DOCUMENT_ROOT="/var/www/"
APP_PORT=80
WWWGROUP=www-data
WWWUSER=www-data
SAIL_XDEBUG_MODE=ON
## MONGO
MONGODB_USERNAME=root
MONGODB_PASSWORD=root
MONGODB_PORT=27017
## MYSQL
FORWARD_DB_PORT=3306
## OTHER
FORWARD_REDIS_PORT=6379
FORWARD_MAIL_PORT=1025
FORWARD_MAILHOG_PORT=1025
FORWARD_MAILHOG_DASHBOARD_PORT=8025
```
