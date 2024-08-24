# SQL_second

### Создание таблицы "Orders"

```sql
CREATE TABLE IF NOT EXISTS orders (
    order_id SERIAL PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    shipping_address VARCHAR(255),
    order_status VARCHAR(50),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE CASCADE
);
```

### Создание таблицы "Customers"

```sql
CREATE TABLE IF NOT EXISTS customers (
    customer_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    phone VARCHAR(20) NOT NULL,
    address VARCHAR(255)
);
```

#### Вставка данных в таблицу "Customers"

```sql
INSERT INTO customers (first_name, last_name, email, phone, address)
VALUES
('John', 'Doe', 'john.doe@example.com', '123-456-7890', '123 Elm St'),
('Jane', 'Doe', 'jane.doe@example.com', '987-654-3210', '456 Oak St'),
('Alice', 'Johnson', 'alice.johnson@example.com', '555-678-1234', '789 Pine St'),
('Bob', 'Smith', 'bob.smith@example.com', '555-123-4567', '789 Maple St'),
('Charlie', 'Brown', 'charlie.brown@example.com', '555-987-6543', '321 Chestnut St');
```

#### Вставка данных в таблицу "Orders"

```sql
INSERT INTO orders (customer_id, order_date, shipping_address, order_status)
VALUES
(1, '2023-01-01', '123 Elm St', 'Shipped'),
(2, '2023-01-02', '456 Oak St', 'Pending'),
(3, '2023-01-03', '789 Pine St', 'Delivered'),
(4, '2023-01-04', '789 Maple St', 'Cancelled'),
(5, '2023-01-05', '321 Chestnut St', 'Shipped');
```

### Проверка корректности вставки данных

- Проверка вставки данных в таблицу "Customers"
```sql
SELECT * FROM customers;
```
- Проверка вставки данных в таблицу "Orders"
```sql
SELECT * FROM orders;
```
- Проверка связей FOREIGN KEY
```sql
SELECT orders.order_id, orders.order_date, orders.shipping_address, orders.order_status, customers.first_name, customers.last_name
FROM orders
JOIN customers ON orders.customer_id = customers.customer_id;
```

Задание выполнено с помощью сайта `https://sqliteonline.com/`.
