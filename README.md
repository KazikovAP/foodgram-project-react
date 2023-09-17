[![Python](https://img.shields.io/badge/-Python-464646?style=flat-square&logo=Python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/-Django-464646?style=flat-square&logo=Django)](https://www.djangoproject.com/)
[![Django REST Framework](https://img.shields.io/badge/-Django%20REST%20Framework-464646?style=flat-square&logo=Django%20REST%20Framework)](https://www.django-rest-framework.org/)
[![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-464646?style=flat-square&logo=PostgreSQL)](https://www.postgresql.org/)
[![Nginx](https://img.shields.io/badge/-NGINX-464646?style=flat-square&logo=NGINX)](https://nginx.org/ru/)
[![gunicorn](https://img.shields.io/badge/-gunicorn-464646?style=flat-square&logo=gunicorn)](https://gunicorn.org/)
[![docker](https://img.shields.io/badge/-Docker-464646?style=flat-square&logo=docker)](https://www.docker.com/)
[![GitHub%20Actions](https://img.shields.io/badge/-GitHub%20Actions-464646?style=flat-square&logo=GitHub%20actions)](https://github.com/features/actions)

# FOODGRAM
# Дипломный проект Яндекс.Практикум Python-developer 58 когорта

---
Доступен по адресу http://kazikovfoodgram.viewdns.net/recipes

---
## Описание приложения
Foodgram («Продуктовый помощник») - это сайт, на котором вы можете добавлять свои рецепты, просматривать рецепты других пользователей, подписываться на foodgram-блоги других авторов, добавлять рецепты в избранное и в корзину покупок. Из корзины покупок вы можете выгрузить список покупок, составленный из продуктов выбранных вами рецептов. И вам больше не придется  вспоминать, что же нужно было докупить для приготовления понравившихся вам рецептов.

---
## Технологии
* Python 3.9
* Django 3.2.3
* Django Rest Framework 3.12.4
* djoser==2.1.0
* gunicorn==20.1.0
* psycopg2-binary==2.9.3

---
## Запуск проекта локально:

**1. Клонировать репозиторий и перейти в него в командной строке:**
```
git clone https://github.com/KazikovAP/foodgram-project-react.git
```

**2. В терминале перейти в каталог:**
```
cd .../foodgram-project-react/infra
```

**3. Создать файл .env для хранения ключей:**
```
DEBUG_STATUS = False # или True еcли планируете использовать проект в режиме разработки
SECRET_KEY = '<ваш секретный ключ Django проекта>'
ALLOWED_HOSTS = <ваш IP XXX.XXX.XXX.XXX> 127.0.0.1 localhost <ваше доменное имя>
POSTGRES_DB = foodgram # указываем имя базы данных
POSTGRES_USER = foodgram_user # указываем имя своего пользователя для подключения к БД
POSTGRES_PASSWORD = foodgram_password # устанавливаем свой пароль для подключения к БД
DB_NAME = foodgram # указываем имя созданной базы данных
DB_HOST = db # указываем название сервиса (контейнера)
DB_PORT = 5432 # указываем порт для подключения к БД 
```

**4. Запустите окружение:**
- Запустите docker-compose, развёртывание контейнеров выполниться в «фоновом режиме»:

```
docker-compose up
```

- выполните миграции:

```
docker-compose exec backend python manage.py makemigrations
docker-compose exec backend python manage.py migrate
```

- соберите статику:

```
docker-compose exec backend python manage.py collectstatic
docker compose exec backend cp -r /app/collected_static/. /backend_static/static/
```

- загрузите в базу данных список ингредиентов:

```
docker-compose exec backend python manage.py load_csv

```

- загрузите в базу данных заготовленные теги:

```
docker-compose exec backend python manage.py create_tags

```

- создайте суперпользователя:

```
docker-compose exec backend python manage.py createsuperuser
```

---
## Workflow
- **tests:** Проверка кода на соответствие PEP8.
- **push Docker image to Docker Hub:** Сборка и публикация образа на DockerHub.
- **deploy:** Автоматический деплой на боевой сервер при пуше в главную ветку main.
- **send_massage:** Отправка уведомления в телеграм-чат.


---
## Разработал:
[Aleksey Kazikov](https://github.com/KazikovAP)

---
## Лицензия:
[MIT](https://opensource.org/licenses/MIT)
