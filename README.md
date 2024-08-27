## Self sail sysetm (3S)

Вынес отдельно скрипты для sail и всё что нужно докеру. Эта штука нужна для 
большего контроля над управлением контейнерами и т.д.

Этот репозиторий можно просто скачать, скопирать в папку проекта, настроить env (если база - постгресс, то просто перенести настройки с подключением к redis, mail и db в свой env, если проект пустой - то просто скопирать `cp .env.example .env`) и запускать. Тут есть дев-докер-компоуз файл с икс-дебагом (IDE ключ docker), но за работоспособность я не ручаюсь тк сделал на скорую руку и лень проверять.

### Вот шаги для установки:
1. перенести файлы в свой проект
2. либо скопировать и настроить свой .env файл (тут нам важно инфа в DB_, REDIS и настроить подключение к SESSION, QUEUE_CONNECTION, CACHE), либо просто `cp .env.example .env` и в `DB_DATABASE` ввести своё название базы данных
3. переименовать `container_name`'ы если надо, а так же docker `networks` сети докера дабы избежать конфликтов
4. `chmod 755 ./sail` если команда `./sail` выдаёт ошибку
5. `./sail up -d` или `./sail -f docker-compose.yml -f docker-compose.dev.yml up -d` что бы запустить

Ну и дальше работать с этим как с обычным Sail.

Тут собираются PHP версии 8.3, 15-й PostgreSQL, Redis и mailhog для тестирования емейлов

**Весь этот проект предоставляется ah-doc, то есть "как есть", и если у вас что-то сломалось - то несете ответсвенность лично вы. Вся эта штука использует базу данных Postgresql как основную, и если вам нужно MySQL, Oracle и т.д. - то меняйте и конфигурируйте сами! (это сделать легко - подменить в docker-compose.yml и настроить .env)**

### Ссылки:
1. [Laravel sail github](https://github.com/laravel/sail)
2. [Laravel sail docs](https://laravel.com/docs/11.x/sail)