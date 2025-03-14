---
title: Что такое YQL? Обзор YDB Query Language
description: YQL (YDB Query Language) — универсальный декларативный язык запросов к системам хранения и обработки данных, диалект SQL. Начать работать с YQL можно в веб-интерфейсе после создания базы данных.
keywords:
  - yql
  - что такое yql
  - YDB Query Language
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/reference/_includes/index/intro.md
---

# YQL - Обзор

*YQL* (YDB Query Language) — универсальный декларативный язык запросов к YDB, диалект SQL. YQL создавался для работы с большими распределенными базами данных, и поэтому обладает рядом отличий от стандарта SQL.

Инструменты работы с YDB поддерживают интерфейсы отправки YQL-запросов и получения результатов их исполнения:

{% include [yql/ui_prompt.md](yql/ui_prompt.md) %}

- [YDB CLI](../../../../reference/ydb-cli/index.md)
- [YDB SDK](../../../../reference/ydb-sdk/index.md)

В данном разделе документации находится справочник по YQL, который включает разделы:
- [Типы данных](../../types/index.md) с описанием типов данных, применяемых в YQL
- [Синтаксис](../../syntax/index.md) с полным перечнем команд YQL
- [Встроенные функции](../../builtins/index.md) с описанием доступных встроенных функций

Также вы можете пройти серию уроков, знакомящих вас с основными командами YQL, в разделе
- [Туториал YQL](../../../tutorial/index.md)

