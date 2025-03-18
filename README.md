# 📌 PostgreSQL: Создание базы данных и таблиц

## 🚀 Этап 1: Создание базы данных

Сначала устанавливаем кодировку 1251 для работы с базами данных:
```sql
\!chcp 1251
```

![Screenshot 1](screenshots/screenshot1.png)

Создаём базу данных `usersdb`:

```sql
CREATE DATABASE usersdb;
```

![Screenshot 2](screenshots/screenshot2.png)

Теперь проверяем, что база данных появилась в списке:
```sql
\l
```

![Screenshot 3](screenshots/screenshot3.png)

Подключаемся к базе данных:
```sql
\c usersdb
```

![Screenshot 4](screenshots/screenshot4.png)

## 📋 Этап 2: Создание таблицы "Продукты"
Создаём таблицу products:
```sql
CREATE TABLE products (
    id INTEGER PRIMARY KEY,
    productname CHARACTER VARYING(30),
    manufacturer CHARACTER VARYING(20),
    productcount INTEGER,
    price NUMERIC
);
```

![Screenshot 5](screenshots/screenshot5.png)

Теперь добавляем данные:
```sql
INSERT INTO products (id, productname, manufacturer, productcount, price) VALUES
('1', 'iPhone X', 'Apple', '3', '36000'),
('2', 'iPhone 8', 'Apple', '2', '41000'),
('3', 'Galaxy S9', 'Samsung', '2', '46000'),
('4', 'Galaxy S8 Plus', 'Samsung', '1', '56000'),
('5', 'Desire 12', 'HTC', '5', '28000');
```

![Screenshot 6](screenshots/screenshot6.png)

Проверяем содержимое:
```sql
SELECT * FROM products;
```

![Screenshot 7](screenshots/screenshot7.png)

## 🛠️ Этап 3: Работа с таблицей "Продукты"
Получим данные по столбцам productname и price:
```sql
SELECT productname, price FROM products;
```

![Screenshot 8](screenshots/screenshot8.png)

Найдем все товары, производителем которых является компания Apple:
```sql
SELECT * FROM products WHERE manufacturer = 'Apple';
```
![Screenshot 9](screenshots/screenshot9.png)

Найдем все товары, у которых цена меньше 29000:
```sql
SELECT * FROM products WHERE price < '29000';
```

![Screenshot 10](screenshots/screenshot10.png)

Найдем все товары, у которых совокупная стоимость больше 90 000:
```sql
SELECT * FROM products WHERE price * productcount > '90000';
```

![Screenshot 11](screenshots/screenshot11.png)

Выберем все товары, у которых производитель Samsung и одновременно цена больше 50000:
```sql
SELECT * FROM products WHERE manufacturer = 'Samsung' AND price > '50000';
```

![Screenshot 12](screenshots/screenshot12.png)

Выберем все товары, у которых либо производитель Samsung, либо цена больше 50000:
```sql
SELECT * FROM products WHERE manufacturer = 'Samsung' OR price > '50000';
```

![Screenshot 13](screenshots/screenshot13.png)

Выберем все товары, у которых производитель не Samsung:
```sql
SELECT * FROM products WHERE manufacturer != 'Samsung';
```

![Screenshot 14](screenshots/screenshot14.png)

Удалим строки, у которых производитель - Apple:
```sql
DELETE FROM products WHERE manufacturer = 'Apple';
```

![Screenshot 15](screenshots/screenshot15.png)

## 🔗 Заключение
Мы создали базу данных usersdb, таблицу products, заполнили ее данными и научились работать с ней (создавать запросы, редактировать данные). Теперь можно использовать ее для запросов, анализа или дальнейшей доработки.
