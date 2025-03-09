## Проект «API для Yatube»

Yatube - проект социальной сети. «API для Yatube» расширяет возможности социальной сети. Новый функционал позволяет пользователям публиковать свои посты и управлять подписками через программный интерфейс взаимодействия.

### Реализованы возможности

- Получение, создание, обновление, удаление публикаций.
- Получение, создание, обновление, удаление комментариев к публикациям.
- Просмотр сообществ и детальной информации о них.
- Отслеживание подписок на авторов, а так же возможность подписки на интересующего автора поста.
- Получение, обновление и проверка JWT авторизации.

### Технологии

- [Python](https://www.python.org/) - язык программирования.
- [Django](https://www.djangoproject.com/) - свободный фреймворк для веб-приложений на языке Python.
- [Django REST Framework](https://www.django-rest-framework.org/) - мощный и гибкий набор инструментов для создания веб-API.
- [Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/) - плагин аутентификации JSON Web Token для Django REST Framework.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

`git clone https://github.com/apolwow/api_final_yatube.git`

`cd api_final_yatube`


Создать и активировать виртуальное окружение:

+ `python3 -m venv env`
+ `source env/bin/activate`
+ `python3 -m pip install --upgrade pip`

Установить зависимости из файла requirements.txt:
`pip install -r requirements.txt`

Выполнить миграции:
`python3 manage.py migrate`


Запустить проект:
`python3 manage.py runserver`
#### После запуска проекта, документация будет доступна по адресу:
`http://localhost:port/redoc/`

#### Примеры запросов:

POST-запрос с токеном, добавление новой публикации в коллекцию публикаций.

`POST http://localhost:port/api/v1/posts/`

```
{
  "text": "Однажды в студеную зимнюю пору, я из лесу вышел, был сильный мороз!",
  "group": 1
}
```

Ответ:

```
{
    "id": 9,
    "author": "root",
    "text": "Однажды в студеную зимнююю пору, я из лесу вышел, был сильный мороз!",
    "pub_date": "2021-09-22T02:37:44.494905Z",
    "image": null,
    "group": 1
}
```


GET-запрос, получение информации о сообществе по id=2.

`GET http://localhost:port/api/v1/groups/2/`

Ответ:

```
{
    "id": 2,
    "title": "group2",
    "slug": "group2",
    "description": "group2"
}
```

POST-запрос, подписка авторизованного пользователя `user=root` от имени которого сделан запрос на автора интересующей публикации `following=admin`.

`POST http://localhost:port/api/v1/follow/`

```
{
  "following": "admin"
}
```

Ответ:

```
{
    "id": 6,
    "user": "root",
    "following": "admin"
}
```