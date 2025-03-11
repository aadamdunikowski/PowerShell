CREATE TABLE customers (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100) UNIQUE NOT NULL
);

CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    price DECIMAL(10,2)
);

CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    customer_id INT REFERENCES customers(id),
    product_id INT REFERENCES products(id),
    quantity INT
);

INSERT INTO customers (name, email) VALUES ('John Doe', 'john@example.com');
INSERT INTO products (name, price) VALUES ('Laptop', 999.99);
INSERT INTO orders (customer_id, product_id, quantity) VALUES (1, 1, 2);

SELECT customers.name, products.name, orders.quantity 
FROM orders
JOIN customers ON orders.customer_id = customers.id
JOIN products ON orders.product_id = products.id;
