---
sourcePath: ru/ydb/overlay/db/cloud_console/create_manage_database.md
---
# Создание, изменение и удаление баз данных

В этом разделе описано, как в облачной консоли управления:

* [{#T}](#create-db).
* [{#T}](#db-list).
* [{#T}](#change-db-params).
* [{#T}](#delete-db).

Данные операции также могут быть выполнены в командной строке [с использованием {{ yandex-cloud }} CLI](../yc_cli.md).

## Создать базу данных {#create-db}

Вы можете создать базу данных в бессерверной (Serverless) конфигурации или с выделенными серверами (Dedicated). Подробнее о различиях в конфигурациях читайте в разделе [Serverless и Dedicated режимы работы](../../concepts/serverless_and_dedicated.md).

{% include [create-db-via-console](../../_includes/create-db-via-console.md) %}

## Посмотреть список баз данных {#db-list}

1. В [консоли управления]({{ link-console-main }}) выберите каталог, для которого нужно получить список баз данных.
1. В списке сервисов выберите **{{ ydb-name }}**.

## Изменить настройки базы данных {#change-db-params}

1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором нужно изменить настройки базы данных.
1. В списке сервисов выберите **{{ ydb-name }}**.
1. Нажмите значок ![horizontal-ellipsis](../../../_assets/horizontal-ellipsis.svg) в строке нужной БД и выберите пункт **Изменить**.
1. Настройте параметры БД:
   1. В блоке **Вычислительные ресурсы** выберите тип и количество [вычислительных ресурсов](../../concepts/databases.md#compute-units).
   1. В блоке **Группы хранения** выберите тип диска и количество [групп хранения](../../concepts/databases.md#storage-groups), определяющее суммарный объем хранилища.
1. Нажмите кнопку **Изменить базу данных**.

## Удалить базу данных {#delete-db}

1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором нужно удалить базу данных.
1. В списке сервисов выберите **{{ ydb-name }}**.
1. Нажмите значок ![horizontal-ellipsis](../../../_assets/horizontal-ellipsis.svg) в строке нужной БД и выберите пункт **Удалить**.
1. Подтвердите удаление.
