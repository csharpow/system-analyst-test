# system-analyst-test
Тестовое задание для компании Effective Mobile
Базы данных — тест

1) Содержит ли какую-то информацию таблица, в которой нет полей?
Ответ: 3. Таблица без полей существовать не может

3) В записи файла реляционной БД может содержаться:
Ответ: 4. Неоднородная информация (данные разных типов)

3)Чем первичный ключ отличается от внешнего ключа?
Ответ: 2. Значения первичного ключа всегда должны быть уникальными и не могут быть null, значения внешнего ключа могут повторяться. И 4. Первичный ключ является идентификатором для строки, а внешний ключ используется для связывания таблиц
(2,4)

4)В какой нормальной форме говорится о том, что все атрибуты зависят от первичного ключа, а не от его части?
Ответ: 2. 2НФ

5)В каком порядке в СУБД выполняются операторы SELECT, FROM, GROUP BY?
Ответ: 4. Сначала FROM, потом GROUP BY и только потом SELECT

6)Чем отличается оператор WHERE от HAVING
Ответ: 2. Оператор HAVING применяется для фильтрации групп, а WHERE - для фильтрации отдельных строк

7) Какой результат покажет выполнение операторов SELECT COUNT (*)?
Ответ: 3. Число строк таблицы, указанной во FROM, включая значение NULL

8) В таблице «Animals» базы данных зоопарка содержится информация обо всех обитающих там животных, в том числе о лисах: red fox, grey fox, little fox. Напишите запрос, возвращающий информацию о возрасте лис
Ответ: 1. SELECT age FROM Animals WHERE Animal LIKE “%fox”

9)Чем отличается DELETE от TRUNCATE?
Ответ: 2. DELETE используется для удаления одной или нескольких строк из таблицы, а TRUNCATE используется для удаления всех строк из таблицы. И
3. DELETE может использовать условие WHERE, а TRUNCATE всегда удаляет все записи из таблицы
(2,3)

10)Дана таблица:

COLOR 
BLUE
RED
null
RED

Каким будет результат запроса?
SELECT COUNT (DISTINCT color) FROM Table

Ответ:4. Результат запроса будет 2

Задание 2. Базы данных - ER
```mermaid
erDiagram
  CUSTOMERS ||--o{ ORDERS : оформляет            
  TOWNS     ||--o{ ORDERS : доставляется_в       
  ORDERS    ||--|{ ORDER_ITEMS : содержит       
  ITEMS     ||--o{ ORDER_ITEMS : присутствует_в  

  CUSTOMERS {
    BIGINT id PK
    TEXT   full_name
    TEXT   email
    TEXT   phone
    TIMESTAMP created_at
  }

  TOWNS {
    BIGINT id PK
    TEXT   name
    TEXT   region
  }

  ITEMS {
    BIGINT id PK
    TEXT   sku
    TEXT   title
    NUMERIC price
    BOOLEAN active
  }

  ORDERS {
    BIGINT id PK
    TEXT   name
    BIGINT customer_id FK
    BIGINT town_id FK
    NUMERIC price
    TEXT   status
    TIMESTAMP created_at
    TIMESTAMP updated_at
  }

  ORDER_ITEMS {
    BIGINT order_id PK, FK
    BIGINT item_id  PK, FK
    INT    qty                NN
    NUMERIC unit_price        NN
    NUMERIC line_amount       -- qty*unit_price
  }
