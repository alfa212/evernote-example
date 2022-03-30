# evernote-example
Приложение для работы с сервисом Evernote через API.

## Установка
Скопируйте файлы приложения к себе на компьютер:
```
git clone https://github.com/alfa212/evernote-example
```
Для работы приложения требуется Python 2.7.

Для установки библиотек, необходимых для работы приложения, выполните команду:
```
pip install -r requirements.txt
```

## Настройка
Перед запуском в папке приложения переименуйте файл `.env_example` в `.env`.


В данном файле хранятся настройки, необходимые для работы приложения:
- EVERNOTE_CONSUMER_KEY - ваш consumer key, получите его на [dev.evernote.com](https://dev.evernote.com/#apikey).
- EVERNOTE_CONSUMER_SECRET - ваш consumer secret, получите его на [dev.evernote.com](https://dev.evernote.com/#apikey).
- EVERNOTE_PERSONAL_TOKEN - ваш ключ разработчика, получите его на [evernote](https://www.evernote.com/Login.action?targetUrl=%2Fapi%2FDeveloperToken.action).
- JOURNAL_TEMPLATE_NOTE_GUID - GUID заметки. Будет использоваться в качестве шаблона. 
- JOURNAL_NOTEBOOK_GUID - GUID блокнота для заметок.
- INBOX_NOTEBOOK_GUID - GUID блокнота, здесь хранятся входящие сообщения.

## Описание
Функционал приложения распределен по файлам:

### add_note2journal.py
Создает новую запись, используя шаблон (настройка `JOURNAL_TEMPLATE_NOTE_GUID` в файле `.env`) и сохраняет ее в блокноте, который указанном в настройке `JOURNAL_NOTEBOOK_GUID`.

В заголовке шаблона должны быть предусмотрены места для вставки даты и дня недели (`{date}--{dow}`).
По умолчанию в заголовок вставляются текущие дата и время из настроек системы. Если вам необходимо установить
другие дату и время, вы можете передать их в ISO-формате(YYYY-MM-DD) в виде аргумента при вызове скрипта:
```
python add_note2journal.py [YYYY-MM-DD]
```

### dump_inbox.py
Показывает список заметок, которые хранятся в блокноте для входящих сообщений. GUID блокнота указывается в настройке `INBOX_NOTEBOOK_GUID`, в файле .env.

В консоль выводится 10 последних заметок (по умолчанию). Однако вы можете изменить количество отображаемых заметок, передав нужное число в качестве аргумента при запуске файла:
```
python dump_inbox.py [ваше количество заметок]
```

### list_notebooks.py
Делает запрос к API Evernote и выводит в консоль список всех блокнотов в аккаунте (GUID, заголовок).

## Цель проекта
Автоматизация работы с заметками в сервисе Evernote.