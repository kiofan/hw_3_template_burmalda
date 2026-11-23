HW 3 — Docker

Приложение со счётчиком. Запускается через Docker Compose, для хранения данных используется Redis.

Запуск

Нужны Docker и Docker Compose.


cp .env.example .env
docker compose up -d --build


Приложение доступно по адресу http://localhost:8080/

Настройки

В .env можно изменить:

- GREETING — приветствие.
- APP_PORT — порт приложения (по умолчанию 8080).

Используются два сервиса:
- app — приложение.
- redis — хранилище счётчика.

Redis сохраняет данные в именованный том redis-data. Оба сервиса имеют healthcheck.

проверка

curl http://localhost:8080/
curl -X POST http://localhost:8080/increment
curl http://localhost:8080/healthz
curl http://localhost:8080/readyz

Остановка

docker compose down