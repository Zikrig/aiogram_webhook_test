# Telegram Bot with Webhooks (aiogram + FastAPI)

Этот проект представляет собой шаблон Telegram-бота на `aiogram 3`, настроенный для работы через вебхуки и готовый к деплою на serverless платформы (например, Vercel).

## Особенности
- **aiogram 3.x**: современная библиотека для работы с Telegram Bot API.
- **FastAPI**: быстрый веб-фреймворк для обработки вебхуков.
- **Serverless ready**: оптимизировано для работы в окружениях без постоянного сервера.

## Установка и запуск локально

1. Клонируйте репозиторий.
2. Установите зависимости:
   ```bash
   pip install -r requirements.txt
   ```
3. Создайте переменные окружения:
   - `BOT_TOKEN`: токен вашего бота от @BotFather.
   - `WEBHOOK_URL`: URL вашего сервера (для локального теста используйте ngrok).
4. Запустите:
   ```bash
   python api/index.py
   ```

## Деплой на Render.com

1. Создайте новый **Web Service** на [dashboard.render.com](https://dashboard.render.com).
2. Подключите ваш GitHub репозиторий.
3. Настройки Render:
   - **Runtime**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python api/index.py` (или `uvicorn api.index:app --host 0.0.0.0 --port $PORT`)
4. Добавьте переменные окружения (Environment Variables):
   - `BOT_TOKEN`: ваш токен.
   - `WEBHOOK_URL`: URL вашего сервиса (например, `https://my-bot.onrender.com`).
5. Render сам назначит порт через переменную `$PORT`, которую бот теперь учитывает.

## Деплой на Vercel

1. Установите Vercel CLI: `npm i -g vercel`.
2. Выполните команду `vercel`.
3. Добавьте переменные окружения `BOT_TOKEN` и `WEBHOOK_URL` в панели управления Vercel.
4. После деплоя бот сам установит вебхук при первом запросе.

## Структура проекта
- `api/index.py`: основной код бота и FastAPI приложения.
- `requirements.txt`: зависимости.
- `vercel.json`: конфигурация для Vercel.

