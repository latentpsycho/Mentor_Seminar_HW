# Реализация микросервисов на базе FastAPI 🌐

# Описание 📄

**TODO-сервис**: реализует CRUD-операции для списка задач с хранением данных в SQLite

**Сервис сокращения URL (Short URL)**: позволяет создавать короткие ссылки для длинных URL, перенаправлять по короткому идентификатору и предоставлять информацию о ссылке. Также обеспечивает хранение данных в SQLite


# Развертывание через Docker

1. Сбор образов для сервисов локально:
```
docker build -t todo-sqlite: latest
docker build -t short_url: latest
```
2. Создание каталогов:
```
docker volume create todo_data
docker volume create shorturl_data
```

3. Запуск контейнеров:
```
docker run -d -p 8000:80 -v todo_data:/app/data todo-sqlite:latest
docker run -d -p 8001:80 -v short_url:/app/data short_url:latest
```
4. Создание тега и пуш образа в DockerHub:

Для микросервиса TODO-Service:
```
docker tag todo-sqlite darknight4565/todo_service:latest
docker push darknight4565/todo_service:latest
```
Для микросервиса Short URL
```
docker tag short_url darknight4565/short_url:latest
docker push darknight4565/short_url:latest
```

# Готовые Docker-образы
- [darknight4565/todo_service](https://hub.docker.com/r/darknight4565/todo_service)
- [darknight4565/short_url](https://hub.docker.com/r/darknight4565/short_url)

# Работа микросервисов🌐

TODO-Service
-
- **Post /items** - создание задачи;
- **GET /items** - получение списка задач;
- **GET /items/{item_id}** - получение конкретной задачи по ID;
- **PUT /items/{item_id}** - обновление задачи по ID;
- **DELETE /items/{item_id}** - удаление задачи по ID.

Short URL
-
- **POST /shorten** - создание короткой ссылки;
- **GET /{short_id}** - редирект на полный URL;
- **GET /stats/{short_id}** - просмотр информации о короткой ссылке.


  
 


