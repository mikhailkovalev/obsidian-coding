#postgres #json
[Source](https://popsql.com/learn-sql/postgresql/how-to-query-a-json-column-in-postgresql)

Чтобы обратиться к "начинке" JSON-поля, нужно использовать операторы `->` и `->>`
```postgresql
-- Give me params.name (text) from the events table
select params->>'name' from events;

-- Find only events with a specific name
select * from events where params->>'name' = 'Click Button';

-- Give me the first index of a JSON array
select params->ids->0 from events;

-- Find users where preferences.beta is true (boolean)
-- This requires type casting preferences->'beta' from json to boolean
select preferences->'beta' from users where (preferences->>'beta')::boolean is true;
```

Check if key in json-array
[Source](https://stackoverflow.com/a/33631247)
```sql
SELECT '{"key_a":1}'::jsonb ? 'key_a'
```
```sql
SELECT '{"key_a": {"nested_key": "a"}}'::jsonb -> 'key_a' ? 'nested_key' 
```