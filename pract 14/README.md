
1. SQL-скрипты создания структур данных
PostgreSQL (Задание 1)

-- Таблица products (источник)
```
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    category VARCHAR(100),
    price NUMERIC(10,2),
    stock_quantity INTEGER,
    supplier_id INTEGER
);
```

MySQL (Задание 2)

-- Таблица target_products (приемник с меткой времени)
```
CREATE TABLE target_products (
    id INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    category VARCHAR(100),
    price DECIMAL(10,2),
    stock_quantity INT,
    supplier_id INT,
    last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

2. Запуск Pentaho

maybe you need this 

https://github.com/BosenkoTM/workshop-on-ETL/blob/main/practice/lw_01.md#2-%D0%BF%D0%BE%D0%B4%D0%B3%D0%BE%D1%82%D0%BE%D0%B2%D0%BA%D0%B0-%D0%BE%D0%BA%D1%80%D1%83%D0%B6%D0%B5%D0%BD%D0%B8%D1%8F-ubuntu-2204

```
cd ~/Downloads/lab_etl/pdi-ce-9.4.0.0-343/data-integration
```

```
./spoon.sh
```

3. В файлах не забываем менять на свою БД!!!
