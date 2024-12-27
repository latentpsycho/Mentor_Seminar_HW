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

Интерфейс TODO-Service
-
![image](https://github.com/user-attachments/assets/9e3eeaf9-8724-4ded-8ee8-634bf118b3f9)

***Добавление задачи №1:***

![image](https://github.com/user-attachments/assets/75da00b6-5177-4627-bd15-e7f1561033e2)

***Добавление задачи №2:***

![image](https://github.com/user-attachments/assets/67babd5c-f59b-49a4-bc33-1ee0c20a44fb)

***Добавление задачи №3:***

![image](https://github.com/user-attachments/assets/9ee57b0c-9419-4f06-9c13-4a75e52a7e0f)

***Корректирование задачи №2:***

![image](https://github.com/user-attachments/assets/e43a23a2-e15e-474f-9529-67ebde1bdd1a)

***Удаление задачи №1:***

![image](https://github.com/user-attachments/assets/a94458d1-0a16-4abc-85f6-7e34dc7e5bc6)

***Проверяем что задача №1 удалена:***

![image](https://github.com/user-attachments/assets/632a1e04-bb73-498e-a1d4-9dfe2b59fdec)

Short URL
-
- **POST /shorten** - создание короткой ссылки;
- **GET /{short_id}** - редирект на полный URL;
- **GET /stats/{short_id}** - просмотр информации о короткой ссылке.

Интерфейс ShortUrl
-
![image](https://github.com/user-attachments/assets/7f8d4323-04a7-45cb-a7ce-67d1db1d0aeb)

***Создаем сокращенную ссылку на примере сайта kinopoisk.hd:***

![image](https://github.com/user-attachments/assets/229b95fc-758a-454f-a876-933fddd0e2ff)

***После получения сокращенной ссылки превращаем обратно в полную:***

![image](https://github.com/user-attachments/assets/375d5ad9-de40-48b8-a938-dd8ee0e1021b)

***Вводим значение сокращенной ссылки для редиректа:***
![image](https://github.com/user-attachments/assets/6ceb631f-48ec-4b04-9688-a4f063056af0)

***Получаем финальный результат 😊:***
![image](https://github.com/user-attachments/assets/e643d7ed-b66f-4d46-beb3-fe7c2dc63f0e)




















  
 


