# Классификация архитектурных стилей

Учебный проект по курсу «Введение в ИИ»: модель определяет архитектурный стиль
здания по фотографии (25 классов). Обучение — fastai, ResNet50 с дообучением;
точность на валидации около 76%.

Модель доступна в Telegram-боте [@architecturestylesbot](https://t.me/architecturestylesbot).

## Файлы

| Файл | Что внутри |
|---|---|
| `architectural_style_recognition.ipynb` | основной ноутбук: загрузка данных, ResNet50 со взвешенной функцией потерь, дообучение, метрики (accuracy, F1), экспорт модели в `architecture_style.pkl` |
| `architectural_style_recognition_intro_to_ai.ipynb` | версия для курса: ResNet50 и сравнение с MobileNetV2 |
| `telegram_bot.ipynb` | Telegram-бот: принимает фото и отвечает стилем здания |
| `architec classification.pdf` | презентация проекта |
| `Доклад по введению в ИИ. Углов 2025.pdf` | доклад |

## Данные

[Architectural Styles Dataset](https://www.kaggle.com/datasets/dumitrux/architectural-styles-dataset)
с Kaggle, 20% изображений уходит в валидацию.

## Запуск

Ноутбуки рассчитаны на Google Colab (GPU).

1. Получите `kaggle.json` (kaggle.com → Settings → API) и загрузите его в `/content`.
   Ноутбук переносит его в `~/.config/kaggle` и скачивает датасет.
2. Выполните `architectural_style_recognition.ipynb` — в конце появится
   `architecture_style.pkl`.
3. Для бота положите `architecture_style.pkl` в `/content`, задайте токен
   и запустите `telegram_bot.ipynb`:

   ```python
   import os
   os.environ["TELEGRAM_BOT_TOKEN"] = "<токен от @BotFather>"
   ```

Не сохраняйте `kaggle.json` и токен бота в ноутбуках: при коммите они
попадут в репозиторий.
