---
title: "Информация о кластерах в {{ mrd-short-name }}"
description: "Вы можете запросить детальную информацию о каждом созданном вами кластере {{ mrd-short-name }}. Чтобы получить список кластеров БД в каталоге, перейдите на страницу каталога и выберите сервис {{ mrd-name }}."
---

# Информация об имеющихся кластерах

Вы можете запросить детальную информацию о каждом созданном вами кластере {{ mrd-short-name }}.


## Получить список кластеров БД в каталоге {#list-clusters}

{% list tabs %}

- Консоль управления
  
  1. В [консоли управления]({{ link-console-main }}) перейдите в каталог, список кластеров которого нужно получить.
  1. Выберите сервис **{{ mrd-name }}**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы запросить список {{ RD }}-кластеров в каталоге по умолчанию, выполните команду:
  
  ```
  {{ yc-mdb-rd }} cluster list
  ```

  Результат:

  ```
  +----------------------+---------------+-----------------------------+--------+---------+
  |          ID          |     NAME      |         CREATED AT          | HEALTH | STATUS  |
  +----------------------+---------------+-----------------------------+--------+---------+
  | c9qp9beeg4oth6lcqvt0 | myredis       | 2018-11-02T10:04:14.645214Z | ALIVE  | RUNNING |
  | ...                                                                                   |
  +----------------------+---------------+-----------------------------+--------+---------+
  ```
  
{% endlist %}


## Получить детальную информацию о кластере {#get-cluster}

{% list tabs %}

- Консоль управления
  
  1. В [консоли управления]({{ link-console-main }}) перейдите в каталог, информацию о кластере которого нужно получить.
  1. Выберите сервис **{{ mrd-name }}**.
  1. Нажмите на имя нужного кластера.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить информацию о {{ RD }}-кластере, выполните команду:
  
  ```
  {{ yc-mdb-rd }} cluster get <имя или идентификатор кластера>
  ```
  
  Идентификатор и имя кластера можно запросить со [списком кластеров в каталоге](#list-clusters).
  
{% endlist %}
