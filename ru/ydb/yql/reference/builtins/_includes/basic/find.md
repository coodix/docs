---
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/reference/yql-core/builtins/_includes/basic/find.md
sourcePath: ru/ydb/yql/reference/yql-core/builtins/_includes/basic/find.md
---
## FIND {#find}

Поиск позиции подстроки в строке.

Обязательные аргументы:

* Исходная строка;
* Искомая подстрока.

Опциональные аргументы:

* Позиция — в байтах, с которой начинать поиск (целое число, или `NULL` по умолчанию, означающий «от начала исходной строки»).

Возвращает первую найденную позицию подстроки или `NULL`, означающий что искомая подстрока с указанной позиции не найдена.

**Примеры**
``` yql
SELECT FIND("abcdefg_abcdefg", "abc"); -- 0
```
``` yql
SELECT FIND("abcdefg_abcdefg", "abc", 1); -- 8
```
``` yql
SELECT FIND("abcdefg_abcdefg", "abc", 9); -- null
```

## RFIND {#rfind}

Обратный поиск позиции подстроки в строке, от конца к началу.

Обязательные аргументы:

* Исходная строка;
* Искомая подстрока.

Опциональные аргументы:

* Позиция — в байтах, с которой начинать поиск (целое число, или `NULL` по умолчанию, означающий «от конца исходной строки»).

Возвращает первую найденную позицию подстроки или `NULL`, означающий, что искомая подстрока с указанной позиции не найдена.

**Примеры**
``` yql
SELECT RFIND("abcdefg_abcdefg", "bcd"); -- 9
```
``` yql
SELECT RFIND("abcdefg_abcdefg", "bcd", 8); -- 1
```
``` yql
SELECT RFIND("abcdefg_abcdefg", "bcd", 0); -- null
```
