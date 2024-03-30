# URL
API по выдачи коротких ссылок и перенаправлению по ним.

Сервер стартует по адресу `http://127.0.0.1:8080`.

<details>
<summary> Список эндпойнтов </summary>

1. Получить сокращённый вариант переданного URL.

```python
POST /
```

Метод принимает в теле запроса строку URL для сокращения и возвращает ответ с кодом `201`.

2. Вернуть оригинальный URL.

```python
GET /<shorten-url-id>
```

Метод принимает в качестве параметра идентификатор сокращённого URL и возвращает ответ с кодом `307` и оригинальным URL в заголовке `Location`.

3. Вернуть статус использования URL.

```python
GET /<shorten-url-id>/status?[full-info]&[max-result=10]&[offset=0]
```

Метод принимает в качестве параметра идентификатор сокращённого URL и возвращает информацию о количестве переходов, совершенных по ссылке.
______________________________________________________
Создание БД:
docker run ——rm ——name postgres-fastapi -p 5432:5432 -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -e POSTGRES_DB=collection -d postgres:16

docker exec -it postgres-fastapi psql -U postgres

CREATE DATABASE shorturl;

Создание таблицы в БД:

alembic revision ——autogenerate -m 01_initial-db

alembic upgrade head

Запуск приложения:
python main.py
