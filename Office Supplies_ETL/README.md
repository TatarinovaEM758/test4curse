
1. скрипты с mySQL - phpmyadmin

-- Создание базы данных
```
CREATE DATABASE IF NOT EXISTS etl_sales_db;
USE etl_sales_db;
```

---1. Основная таблица для отфильтрованных данных (Office Supplies)
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

