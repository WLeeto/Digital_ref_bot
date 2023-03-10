# Бот для проекта "Цифровое спасибо"



#### Реализовано:
* **/balance, /баланс** - бот отвечает текущий баланс, при обращении в ЛС берется баланс активной организации
* **+n Необязательный комментарий** - используется при цитировании сообщения в группе с ботом, отправляет n спасибок цитируемому пользователю
* **/ct** - в личных сообщениях. Выводит список не проведенных транзакций. При клике на транзакцию отменяет ее
* **/go** - в личных сообщениях. Выводит список групп. При клике по группе делает ее активной.
* **/export** - отправляет в ЛС фаил .xlsx со списком транзакций по пользователю. При общении в ЛС формирует список по активной группе


### Структура:
* /API/ - функции связанные с получение responce от api
* /handlers/admin.py - хендлеры для админки, все проверяются по id листу админа
* /handlers/client.py - хендлеры для клиентов, все команды общего пользования
* /handlers/other.py - хендлеры общего назначения, ловят обычные сообщения по фильтрам *ОБЯЗАТЕЛЬНО СТАВЯТСЯ ПОСЛЕДНИМИ В ИСПОЛНЕНИЕ*
* /keyboards - кнопки клавиатур
* /dict_cloud/dicts - словари с сообщениями (центральная переменная)


### База данных:
Для определения текущей организации при общении с ботом в ЛС добавлена БД со статусом is_active для организайций пользователя

При общении с ботом в ЛС пользователь и все его текущие организации заносятся в БД

Реализована проверка на наличие пользователей и организайций в БД для избежания дублей

Структура БД:
![Структура БД](/source/db_scheme.png)

### Точка входа:
    
    main.py

### Для запуска:

    Для запуска создается фаил censored.py в корне с переменными:
    token_tg (str)= токен телеграм бота
    token_drf (str) = токен бота для работы с API
    drf_url (str) = базовый домен для работы с API (http://176.99.6.251:8888/)

### Установка зависимостей:

    pip install requirements.txt