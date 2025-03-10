---
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/tutorial/conditional_values.md
---
# Дополнительные условия выборки

Выберите все названия эпизодов первого сезона каждого сериала и отсортируйте их по имени.

{% include [yql-reference-prerequisites](_includes/yql_tutorial_prerequisites.md) %}

```sql
SELECT
    series_title,               -- series_title будет определен ниже в GROUP BY

    String::JoinFromList(       -- вызов С++ UDF,
                                -- см. ниже

        AGGREGATE_LIST(title),  -- функция агрегации,
                                -- возвращающая все переданные значения в виде списка

        ", "                    -- String::JoinFromList преобразует
                                -- элементы указанного списка (первый аргумент)
                                -- в строку, используя разделитель (второй аргумент)
    ) AS episode_titles
FROM episodes
WHERE series_id IN (1,2)        -- IN определяет набор значений в условии WHERE,
                                -- которые должны попасть в результат.
                                -- Синтаксис:
                                -- test_expression (NOT) IN
                                -- ( subquery | expression ` ,...n ` )
                                -- Если значение test_expression равно
                                -- любому значению, возвращаемому подзапросом, или равно
                                -- любому выражению из списка, разделенного запятыми,
                                -- результатом будет TRUE; в противном случае — FALSE.
                                -- NOT IN означает, что значение НЕ присутствует в результате подзапроса
                                -- или в выражении.
                                -- Предупреждение: использование значений null вместе с
                                -- IN или NOT IN может привести к нежелательным результатам.
AND season_id = 1
GROUP BY
    CASE                        -- CASE проверяет список условий
                                -- и возвращает одно из нескольких возможных
                                -- выражений. CASE может быть использован в любом
                                -- выражении или с любым оператором,
                                -- поддерживающим данное выражение. Например, CASE можно использовать
                                -- выражениях SELECT, UPDATE, DELETE,
                                -- и с операторами IN, WHERE, ORDER BY.
        WHEN series_id = 1
        THEN "IT Crowd"
        ELSE "Other series"
    END AS series_title         -- GROUP BY можно выполнить
                                -- для произвольного выражения.
                                -- Результат будет доступен в SELECT
                                -- через алиас, указанный с помощью AS.
;

COMMIT;
```
