api_final
# Доработка CRUD для Yatube
Настроена проверка прав и пермишены, ограничение количества запросов, фильтрация сортировка и поиск.

## _Как запустить проект:_
Клонировать репозиторий и перейти в него в командной строке:
```sh
git clone https://github.com/redbull7214/api_final_yatube.git
cd api_final_yatube 
```
Cоздать и активировать виртуальное окружение:
```sh
python -m venv venv
source venv/Scripts/activate 
python -m pip install --upgrade pip
```
Установить зависимости из файла requirements.txt:
```sh
pip install -r requirements.txt
```
Выполнить миграции:
```sh
python manage.py migrate
```
Запустить проект:
```sh
cd yatube_api
python manage.py runserver
```

## _Примеры запросов_
> Получение публикаций

GET http://127.0.0.1:8000/api/v1/posts/
Response samples
```sh
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 1
    }
  ]
}
```

> Создание публикации

POST http://127.0.0.1:8000/api/v1/posts/
```sh
{
    "text": "string",
    "group": 1
}
```
Response samples
```sh
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 1
}
```
> Получение комментариев 

GET http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
Response samples
```sh
[
  {
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
  }
]
```
>Список сообществ

GET http://127.0.0.1:8000/api/v1/groups/
Response samples
```sh
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
```
>Получить JWT-токен

POST http://127.0.0.1:8000/api/v1/jwt/create/
```sh
{
  "username": "string",
  "password": "string"
}
```
Response samples
```sh
{
  "refresh": "string",
  "access": "string"
}
```
