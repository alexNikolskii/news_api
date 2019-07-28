# News API

Версия: 0.1.0

Автор: Никольский Александр

## Требования

- Python версии не ниже 3.7



## Состав

- Файл запуска сервера: **app.py**
- Файл логики API: **server_api.py**
- Файл создания и инициализации базы данных: **models.py**



## Описание

Сервер взаимодействует с базой данных, в которой есть следующие таблицы:

1. Новости с атрибутами:
   - id
   - title
   - date
   - body
   - deleted
2. Комментарии с атрибутами:
   - id
   - news_id
   - title
   - date
   - comment

Сервер отвечает на 2 типа запросов:

1. Получение всех **валидных** новостей: 

   - Не удаленных.
   - Дата публикации новости произошла раньше или в момент обращения к базе данных.

2. Получения данных о **конкретной** новости. Сервер возвращает ошибку 404, если:

   1. Новости с таким id нет
   2. Новость удалена
   3. Время публикации новости еще не наступило

   В остальных случаях возвращается запрашиваемая новость.



## Запуск сервера

Для того, чтобы запустить программу, необходимо:

1. Создать базу данных:  `python models.py`

2. Запустить сервер: `python app.py`

3. В браузере/с помощью скрипта обратиться к серверу по следующему URL: *http://localhost:8080/*

   В данном случае будет выведен JSON с всеми новостями.

   Если нужна информация о конкретной новости, используйте следующий URL: http://localhost:8080/news/{id конкретной новости}