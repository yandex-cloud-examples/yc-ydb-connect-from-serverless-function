# Подключение к базе данных Yandex Managed Service for YDB из функции Yandex Cloud Functions на Node.js

Руководство предназначено для пользователей Linux. На Windows пройти руководство можно в среде [WSL](https://learn.microsoft.com/ru-ru/windows/wsl/about).

Вы создадите [функцию](https://yandex.cloud/ru/docs/functions/concepts/function) с [приложением на Node.js](https://ydb.tech/docs/ru/dev/example-app/example-nodejs), которое выполняет простой запрос к базе данных [YDB](https://ydb.tech). Развертывание приложения осуществляется с помощью Bash-скриптов, для компиляции используется команда tcs.

Функция с привязанным [сервисным аккаунтом](https://yandex.cloud/ru/docs/iam/concepts/users/service-accounts) авторизуется в YDB через сервис метаданных.

Приложение создает драйвер подключения к БД YDB, сессию, транзакцию и выполняет запрос, используя библиотеку ydb. Эта библиотека устанавливается как [зависимость](https://yandex.cloud/ru/docs/functions/lang/nodejs/dependencies) при создании [версии](https://yandex.cloud/ru/docs/functions/concepts/function#version) функции. Параметры подключения к БД передаются в приложение через переменные окружения.

Чтобы настроить подключение к базе данных YDB, воспользуйтесь практическим руководством [Подключение к базе данных Yandex Managed Service for YDB из функции Yandex Cloud Functions на Node.js](https://cloud.yandex.ru/docs/tutorials/serverless/connect-from-cf-nodejs). Исходный код, который используется в руководстве, доступен в этом репозитории.

## См. также

* [Подключение к базе данных Yandex Managed Service for YDB из функции Cloud Functions на Python](https://cloud.yandex.ru/docs/functions/solutions/connect-to-ydb#create-function)
