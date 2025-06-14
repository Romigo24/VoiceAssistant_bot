# Dialogflow Chatbots: Telegram & VK

Проект включает **Telegram-** и **VK-ботов**, использующих **Dialogflow** для обработки и генерации ответов на сообщения пользователей.

**Dialogflow** — это облачный сервис от Google для создания чат-ботов, который использует технологии обработки естественного языка для генерации умных ответов на сообщения пользователей. Он позволяет строить ботов, которые могут понимать текстовые запросы и давать осмысленные ответы.

### Примеры работающих ботов:
**Telegram-бот:** Перейдите по ссылке, чтобы увидеть пример работы [Telegram-бота](https://t.me/MeetupEvents_bot).

![ScreenRecording](https://github.com/user-attachments/assets/8262f2b4-7ebe-4a01-8bb2-2c00d01d0832)

**VK-бот:** Заходите в [группу в ВКонтакте](https://m.vk.com/club230911669) и напишите сообщение в чат, чтобы увидеть, как бот работает.

![ScreenRecording](https://github.com/user-attachments/assets/7f5d8d40-c094-4cfc-b6e7-b5459943073b)

## Установка и настройка

### 1. Скачайте или клонируйте репозиторий:

```shell
git clone https://github.com/Romigo24/DialogFlow_bot.git
```

### 2. Установите зависимости:

```shell
pip install -r requirements.txt
```

### 3. Настройте переменные окружения:

Создайте файл `.env` в корневой папке вашего проекта и добавьте в него следующие переменные:


```
TELEGRAM_BOT_TOKEN=ваш_токен_телеграм_бота
VK_BOT_TOKEN=ваш_токен_группы_вк
DIALOGFLOW_PROJECT_ID=ваш_id_проекта_dialogflow
ADMIN_CHAT_ID=ваш_чат_айди_для_получения_ошибок
GOOGLE_APPLICATION_CREDENTIALS=путь_к_файлу_учётных_данных
```
`TELEGRAM_BOT_TOKEN` — токен **Telegram-бота**, созданного через [BotFather](https://telegram.me/BotFather). Сохраните и укажите его здесь.

`VK_BOT_TOKEN` — токен доступа группы ВКонтакте. Получается через раздел **"Работа с API"** в настройках группы (разрешите доступ к сообщениям).

`DIALOGFLOW_PROJECT_ID` — ID проекта Dialogflow. Найти его можно в **Google Cloud Console**.

`ADMIN_CHAT_ID` — ID чата в Telegram, куда будут отправляться сообщения об ошибках, если что-то пойдёт не так с ботами.

`GOOGLE_APPLICATION_CREDENTIALS` — путь к JSON-файлу с учётными данными сервисного аккаунта Google. Этот файл нужен для авторизации при работе с Dialogflow API.
Получить его можно в разделе IAM → Сервисные аккаунты в Google Cloud Console. При создании ключа выберите формат JSON.

## Запуск бота
### Для запуска Telegram-бота выполните команду:
```shell
python telegram_bot.py
```
Бот отвечает на текстовые сообщения, используя Dialogflow.
### Для запуска VK-бота выполните команду:
```shell
python vk_bot.py
```
Бот обрабатывает входящие сообщения в группе ВКонтакте и отвечает, используя Dialogflow, при наличии понятного интента.

## Обучение Dialogflow.
Скрипт `create_intents.py` загружает фразы и ответы из файла `training_questions.json` и создаёт соответствующие интенты в вашем проекте **Dialogflow**.

#### 1. Подготовьте файл `training_questions.json`. Пример содержимого:

```json
{
  "faq": [
    {
      "category": "Категория",
      "questions": ["Вопрос 1", "Вопрос 2"],
      "answer": "Ответ"
    }
  ]
}
```
#### 2. Запустите обучение

Убедитесь, что у вас настроены переменные окружения (в частности `DIALOGFLOW_PROJECT_ID`), затем выполните:

```shell
python create_intents.py
```
После запуска в вашей консоли появятся сообщения об успешно созданных интентах.


