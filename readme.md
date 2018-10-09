# Moodle-Docker

Стек

  - nginx latest version
  - Php-fpm 7.0
  - postgres 9.6
  - phppgadmin
  - jwilder nginx-proxy

# Порядок установки
```sh
$ git@github.com:mufasadev/moodle-docker.git .
```
В папку app положить исходники moodle
Проверить, что бы порты 80, 9000, 5432 были открыты и свободны.
```sh
$ cd ./docker
$ docker network create moodle-nginx-proxy
$ docker-compose up -d
```

Открыть в браузере http://moodle.localhost и пройти процедуру установки.
В качестве папки moodledata указать /moodledata

Выбрать из предложенных баз данных postgresql

Параметры подключения к бызе данных
  - host: moodle_postgresql
  - db_name: moodle
  - user: postgres
  - password: root

phpPgAdmin http://pg.localhost