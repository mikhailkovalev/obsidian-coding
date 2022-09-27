#db #postgres #explain #index

https://postgrespro.ru/docs/postgrespro/9.5/performance-tips

Посмотреть план выполнения запроса: просто надо добавить `EXPLAIN`  перед

Отключить последовательное сканирование (Seq Scan)
```postgresql
SET enable_seqscan = off;
```

Проверить текущее значение для `enable_seqscan`:
```postgresql
SHOW enable_seqscan;
```

Отключить какой-то индекс:
```postgresql
UPDATE pg_index SET indisvalid = false WHERE indexrelid = 'invest_charge_scheduled_at_5638b65e'::regclass;
```
