# Установка Gitlab

## Создание контейнеров

```bash
$ docker-compose up --no-start
```

## Настройка PostgreSQL

```bash
$ docker start postgresql
$ docker exec -i -t postgresql /bin/bash
$ su - postgres
$ createuser -P gitlab
$ createdb -O gitlab gitlabhq_production
$ echo 'CREATE EXTENSION pg_trgm;' | psql gitlabhq_production
$ docker stop postgresql
```

## Запуск контейнеров

```bash
$ docker-compose up -d
```

## Проверка настройки SMTP

```bash
$ docker exec -it gitlab_app gitlab-rails console
$ Notify.test_email('email', 'Test', 'Test').deliver
```