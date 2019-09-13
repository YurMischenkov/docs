# Управление правами на запуск функции

Чтобы любой пользователь мог вызывать функцию, необходимо сделать ее публичной. Для этого назначьте роль `serverless.functions.invoker` на каталог с функцией для всех неавторизованных пользователей — системная группа `allUsers`.

Рекомендуется создать отдельный каталог для всех публичных функций, чтобы случайно не дать доступ всем пользователям в интернете до ваших приватных функций.

{% note important %}

Не давайте права `editor` и `admin` на системную группу `allUsers`. Это позволит любому пользователю в интернете использовать ресурсы вашего Облака за ваш счет. Подробнее о системных группах читайте в разделе [{#T}](../../../iam/concepts/access-control/system-group.md).

{% endnote %}

Назначить необходимые права можно с помощью команды:

```
$ yc resource-manager folder add-access-binding <ID каталога>
                             --role serverless.functions.invoker
                             --subject system:allUsers
```

Подробнее о правах, читайте в разделе [{#T}](../../security/index.md).