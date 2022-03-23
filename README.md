![yamdb_workflow](https://github.com/github/docs/actions/workflows/main.yml/badge.svg)

# Yamdb

Проект представляет собой сервис по хранению сведений о различных произведениях искусства, а именно - их описание и отзывы к ним.
Хранение самих произведений в рамках этого проекта не предусмотрено.

Список возможностей проекта:
- Регистрация пользователей
- Работа со списками произведений
- Работа со списками категорий
- Работа со списками обзоров
- Работа со списками комментариев к обзрам
- Работа со списками пользователей

## Список используемых технологий:
- Python 3
- Django
- Django REST Framework
- Simple JWT
- Gunicorn


## Последовательность действий, необходимых для запуска проекта
1. Создать и заполнить по образцу .env-файл
```
DB_ENGINE=<...>
DB_NAME=<...>
POSTGRES_USER=<...>
POSTGRES_PASSWORD=<...>
DB_HOST=<...>
DB_PORT=<...>
SECRET_KEY=<...>
```
2. Соберите и запустите контейнер с помощью Docker-compose
```
docker-compose build
docker-compose up
```
3. Выполнить миграции через Docker-compose
```
docker-compose exec web python manage.py makemigrations --noinput  
docker-compose exec web python manage.py migrate --noinput
```
4. Собрать через Docker-compose статики
```
docker-compose exec web python manage.py collectstatic --no-input
```  

## Чтобы создать суперпользователя, выполните эту команду
```
docker-compose exec web python manage.py createsuperuser
```  

## Чтобы заполнить базу начальными данными, выполните эту команду
```
docker-compose exec web python manage.py loaddata fixtures.json
```  

## Чтобы импортировать данные в формате .json, выполните эту команду
```
docker-compose run web python manage.py loaddata path/to/your/json
```

## Для подключения к базе данных
Скопируйте и отредактируйте файл .env  
```
cp .env.template .env
```


Автор: https://github.com/kmilobendzky
