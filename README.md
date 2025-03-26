# Подключение к базе данных Yandex Managed Service for YDB из функции Yandex Cloud Functions на Node.js

Пример по развертыванию функции [Yandex Cloud Functions](https://cloud.yandex.ru/docs/functions/) на Node.js и [подключению](https://cloud.yandex.ru/docs/ydb/concepts/connect) к базе данных [Yandex Managed Service for YDB](https://cloud.yandex.ru/docs/ydb/) с помощью сервиса метаданных.

Сервис метаданных работает на виртуальных машинах [Yandex Compute Cloud](https://cloud.yandex.ru/docs/compute/), а также функциях Yandex Cloud Functions.

## Перед началом работы

Руководство предназначено для пользователей Linux. На Windows пройти руководство можно в среде [WSL](https://learn.microsoft.com/ru-ru/windows/wsl/about).

1. Клонируйте этот репозиторий.
     На Windows необходимо проконтролировать, что при импорте из github в файлах `*.sh` перевод каретки установлен только в `LF` - иначе скрипты выдадут ошибку.
1. Если у вас еще нет интерфейса командной строки Yandex Cloud, [установите и инициализируйте его](https://yandex.cloud/ru/docs/cli/quickstart#install).
1. [Создайте](https://yandex.cloud/ru/docs/iam/operations/sa/create) сервисный аккаунт и [назначьте](https://yandex.cloud/ru/docs/iam/operations/sa/assign-role-for-sa) ему роль `admin`.
1. [Создайте](https://cloud.yandex.ru/docs/iam/operations/authorized-key/create) авторизованный ключ для сервисного аккаунта:

    ```bash
    yc iam key create --service-account-name <имя_сервисного_аккаунта> -o service_account_key_file.json
    ```

   Где: 
   * `--service-account-name` — имя сервисного аккаунта, созданного ранее.


## Запуск примера

1. Перейдите в терминале в папку проекта и установите зависимости командой:
    ```bash
    npm i
    ```
1. Внесите пользовательские значения данные в файле `.env`.


1. Для создания новую публичной функции выполните: 
    ```bash
    ./deploy/create-func.sh
    ```
1. Запустите установку зависимостей:
    ```bash
    npm install
    ```

1. Создайте экземпляра функции:
    ```bash
    ./deploy/create-func-ver.sh
    ```

    Скрипт разделен на две части потому что Вам потребуется один раз создать функцию и по мере разработки запускать создание версий функции.

    Обратите внимание, что при создании версии функции автоматически создаются и заполняются необходимые для работы функции env переменные.

1. Вызовите функцию передав ей параметр `api_key`— имя создаваемой таблицы.

Данный шаблон подразумевает отладку кода на локальном компьютере. Для этого запускайте программу с помощью файла `index-local.ts` и проводите отладку вашего кода.

## См. также

* [Подключение к базе данных Yandex Managed Service for YDB из функции Cloud Functions на Python](https://cloud.yandex.ru/docs/functions/solutions/connect-to-ydb#create-function)

