Задание:
Фильтр по категории: только Office Supplies
Анализ продаж по месяцам
Отчет по клиентам


1. скрипты в mySQL - phpmyadmin

---1. Основная таблица для отфильтрованных данных (Office Supplies) - не нужно!!!
```
CREATE TABLE IF NOT EXISTS sales_office_supplies (
    row_id INT PRIMARY KEY,
    order_id VARCHAR(50),
    order_date DATE,
    ship_date DATE,
    ship_mode VARCHAR(50),
    customer_id VARCHAR(50),
    customer_name VARCHAR(100),
    segment VARCHAR(50),
    country VARCHAR(100),
    city VARCHAR(100),
    state VARCHAR(100),
    postal_code VARCHAR(20),
    region VARCHAR(50),
    product_id VARCHAR(50),
    category VARCHAR(50),
    sub_category VARCHAR(50),
    product_name VARCHAR(255),
    sales DECIMAL(15,4),
    quantity INT,
    discount DECIMAL(10,4),
    profit DECIMAL(15,4),
    load_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

-- 2. Таблица для анализа продаж по месяцам (Доп. задание 1)
```
CREATE TABLE IF NOT EXISTS monthly_sales_analysis (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_month DATE,  -- Первый день месяца
    total_sales DECIMAL(15,4),
    total_profit DECIMAL(15,4),
    order_count INT,
    avg_discount DECIMAL(10,4),
    load_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

-- 3. Таблица для отчета по клиентам (Доп. задание 2)
```
CREATE TABLE IF NOT EXISTS customer_report (
    customer_id VARCHAR(50) PRIMARY KEY,
    customer_name VARCHAR(100),
    total_sales DECIMAL(15,4),
    total_profit DECIMAL(15,4),
    order_count INT,
    avg_order_value DECIMAL(15,4),
    last_order_date DATE,
    segment VARCHAR(50),
    load_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```
-- 4. Таблица для логирования ошибок ETL
```
CREATE TABLE IF NOT EXISTS etl_error_log (
    error_id INT AUTO_INCREMENT PRIMARY KEY,
    transformation_name VARCHAR(100),
    step_name VARCHAR(100),
    error_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    error_message TEXT,
    error_row_data TEXT,
    error_field VARCHAR(100)
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
