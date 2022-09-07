#db #postgres #index 

[Source](https://postgrespro.ru/docs/postgrespro/9.5/indexes)
 Пусть есть таблица
```postgresql
CREATE TABLE test1 (id integer, content varchar);
```

Пусть к ней есть много запросов вида
```postgresql
SELECT content FROM test1 WHERE id='smth';
```

Для оптимизации запроса надо создать индекс
```postgresql
CREATE INDEX test_id_index ON test1 (id);
```

Имя индекса `test_id_index` может быть произвольным.

Индексы также могут быть полезны при выполнении `UPDATE` и `DELETE` запросов, а также могут быть полезны для столбцов, участвующих в условии для `JOIN`.


Важно!
> После создания индекса СУБД сама его обновляет при изменении данных в таблице, никаких дополнительных действий не требуется!
>
> На время построения индекса блокируются операции `INSERT`, `UPDATE`, `DELETE`
> 
> Построение индекса для больших таблиц может занимать много времени

###  Синтаксис создания индекса
[Source](https://postgrespro.ru/docs/postgrespro/9.5/sql-createindex#sql-createindex-concurrently)
```
CREATE [ UNIQUE ] INDEX [ CONCURRENTLY ] [ [ IF NOT EXISTS ] имя ] ON имя_таблицы [ USING метод ] 
    ( { имя_столбца | ( выражение ) } [ COLLATE правило_сортировки ] [ класс_операторов ] [ ASC | DESC ] [ NULLS { FIRST | LAST } ] [, ...] )
    [ INCLUDING ( имя_столбца [, ...] ) ]
    [ WITH ( параметр_хранения = значение [, ... ] ) ]
    [ TABLESPACE табл_пространство ]
    [ WHERE предикат ]
```

### Посмотреть имеющиеся индексы:
```postgresql
SELECT * FROM pg_indexes WHERE tablename = 'table_name';
```

### [[_postgres_explain|Использование `EXPLAIN`]]
### [Неблокирующее построение индексов](https://postgrespro.ru/docs/postgrespro/9.5/sql-createindex#sql-createindex-concurrently)


