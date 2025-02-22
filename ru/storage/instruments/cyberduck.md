# CyberDuck

CyberDuck — это графический клиент к облачным хранилищам для Mac и Windows (в виде консольного клиента доступен для всех операционных систем).

## Подготовка к работе {#preparations}

{% include [storage-s3-http-api-preps](../_includes_service/storage-s3-http-api-preps.md) %}

## Установка {#installation}

Для установки CyberDuck перейдите на [сайт производителя](https://cyberduck.io) и скачайте необходимый дистрибутив.

## Подключение {#connection}

Создайте соединение со следующими параметрами:

  - Тип подключения: `Amazon S3`.
  - Сервер и порт: `{{ s3-storage-host }}:443`.
  - Access Key ID: `id`, который вы получили при генерации статического ключа.
  - Пароль: `secretKey`, который вы получили при генерации статического ключа.

{% note info %}

CyberDuck работает с {{ objstorage-name }} как с иерархической файловой системой. Это значит, что ключи для загруженных через CyberDuck объектов будут иметь вид пути к файлу. Например, `prefix/subprefix/picture.jpg`.

{% endnote %}
