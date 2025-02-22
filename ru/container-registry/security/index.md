# Управление доступом

В этом разделе вы узнаете:
* [на какие ресурсы можно назначить роль](#resources);
* [какие роли действуют в сервисе](#roles-list);
* [какие роли необходимы](#required-roles) для того или иного действия.

{% include [about-access-management](../../_includes/iam/about-access-management.md) %}

## На какие ресурсы можно назначить роль {#resources}

Сейчас роль можно назначить на [облако](../../resource-manager/concepts/resources-hierarchy.md#cloud) или [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder). Эти роли будут действовать и на вложенные ресурсы.

## Какие роли действуют в сервисе {#roles-list}

На диаграмме показано, какие роли есть в сервисе и как они наследуют разрешения друг друга. Например, в `editor` входят все разрешения `viewer`. После диаграммы дано описание каждой роли.

![image](service-roles-hierarchy.svg)

Роли, действующие в сервисе:

* Сервисные роли:
    * {% include [container-registry.images.puller](../../_includes/iam/roles/short-descriptions/container-registry.images.puller.md) %}
    * {% include [container-registry.images.pusher](../../_includes/iam/roles/short-descriptions/container-registry.images.pusher.md) %}
    * {% include [resource-manager.clouds.owner](../../_includes/iam/roles/short-descriptions/resource-manager.clouds.owner.md) %}
    * {% include [resource-manager.clouds.member](../../_includes/iam/roles/short-descriptions/resource-manager.clouds.member.md) %}
* Примитивные роли:
    * {% include [viewer](../../_includes/iam/roles/short-descriptions/viewer.md) %}
    * {% include [editor](../../_includes/iam/roles/short-descriptions/editor.md) %}
    * {% include [admin](../../_includes/iam/roles/short-descriptions/admin.md) %}

## Какие роли мне необходимы {#required-roles}

В таблице ниже перечислено, какие роли нужны для выполнения указанного действия. Вы всегда можете назначить роль, которая дает более широкие разрешения, нежели указанная. Например, назначить `editor` вместо `viewer`.

Действие | Методы | Необходимые роли
----- | ----- | -----
**Просмотр информации** | |
Получение информации о [реестрах](../operations/registry/registry-list.md), [Docker](../operations/docker-image/docker-image-list.md)-образах и [репозиториях](../operations/repository/repository-list.md) | `get`, `list` | `container-registry.images.puller` на каталог с указанными ресурсами
[Скачивание Docker-образа из реестра](../operations/docker-image/docker-image-pull.md) | — | `container-registry.images.puller`<br>на каталог с указанным реестром
**Управление ресурсами** | |
[Создание реестров в каталоге](../operations/registry/registry-create.md) | `create` | `editor` на каталог
[Изменение](../operations/registry/registry-update.md) и [удаление](../operations/registry/registry-delete.md) реестров | `update`, `delete` | `editor` на каталог с реестром
[Создание Docker-образов](../operations/docker-image/docker-image-create.md) c использованием базовых Docker-образов из реестра | — | `container-registry.images.puller`<br>на каталог с указанным реестром
[Создание Docker-образов](../operations/docker-image/docker-image-create.md) без использования базовых Docker-образов из реестра| — | Не требует ролей
[Загрузка Docker-образов в реестр](../operations/docker-image/docker-image-push.md) | — | `container-registry.images.pusher`<br>на каталог с указанным реестром
[Удаление Docker-образов](../operations/docker-image/docker-image-delete.md) | `delete` | `editor` на каталог с Docker-образом
**Управление доступом к ресурсам** | |
[Назначение роли](../../iam/operations/roles/grant.md), [отзыв роли](../../iam/operations/roles/revoke.md) и просмотр назначенных ролей на каталог или облако | `setAccessBindings`, `updateAccessBindings`, `listAccessBindings` | `admin` на этот ресурс

#### Что дальше

* [Как назначить роль](../../iam/operations/roles/grant.md).
* [Как отозвать роль](../../iam/operations/roles/revoke.md).
* [Подробнее об управлении доступом в Яндекс.Облаке](../../iam/concepts/access-control/index.md).
* [Подробнее о наследовании ролей](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance).
