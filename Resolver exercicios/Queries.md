#### Verificação de select

Funcionaram:
`SELECT name, age FROM users;`
`SELECT DISTINCT age FROM users;`
`SELECT * FROM users WHERE age > 30;`
`SELECT * FROM users ORDER BY age DESC;`
`SELECT * FROM users LIMIT 5;`

`SELECT age, COUNT(*) FROM users GROUP BY age;`
`SELECT age, COUNT(*) FROM users GROUP BY age HAVING COUNT(*) > 1;`

```
SELECT COUNT(*) FROM users; -- Conta os registros
SELECT AVG(age) FROM users; -- Média de idade
SELECT SUM(age) FROM users; -- Soma total de anos
SELECT MAX(age) FROM users; -- Maior idade
SELECT MIN(age) FROM users; -- Menor idade
```

`SELECT * FROM users WHERE name LIKE 'C%';`
`SELECT * FROM users WHERE name LIKE '%Almeida%';`
`SELECT * FROM users WHERE age BETWEEN 25 AND 29;`
`SELECT * FROM users WHERE age IN (25, 30, 35);`

`SELECT * FROM users WHERE EXISTS (SELECT 1 FROM orders WHERE users.id = orders.user_id);`

Não funcionou:
`SELECT * FROM users LIMIT 5 OFFSET 10;` -> não funcionou (apenas LIMIT funciona)

#### Verificação de update

`UPDATE users SET age = 28 WHERE name = 'Carlos';`


#### Verificação de insert

`INSERT INTO users (name, age, birth_date, has_driver_license) VALUES ('Carlos', 27, '1997-08-10', TRUE);`


#### Verificação de delete

`DELETE FROM users WHERE age < 25;`

### Verificação de Junções e Relações

#### INNER JOIN

```
SELECT users.name, orders.total_amount 
FROM users 
INNER JOIN orders ON users.id = orders.user_id;
```

#### LEFT JOIN

```
SELECT users.name, orders.total_amount 
FROM users 
LEFT JOIN orders ON users.id = orders.user_id;
```

#### RIGHT JOIN

```
SELECT users.name, orders.total_amount 
FROM users 
RIGHT JOIN orders ON users.id = orders.user_id;
```

####  FULL JOIN
Nativo apenas do POSTGRES
**Não funcionou**
```
SELECT users.name, orders.total_amount 
FROM users 
FULL JOIN orders ON users.id = orders.user_id;
```


Apenas usuários que possuem pedidos:
```
SELECT 
    u.id AS user_id, 
    u.name, 
    u.age, 
    o.id AS order_id, 
    o.order_date, 
    o.total_amount, 
    o.status
FROM users u
INNER JOIN orders o ON u.id = o.user_id;
```

Exibe **quantos pedidos cada usuário realizou**:
```
SELECT 
    u.id AS user_id, 
    u.name, 
    COUNT(o.id) AS total_orders
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
GROUP BY u.id, u.name
ORDER BY total_orders DESC;
```

Aqui pegamos apenas os usuários que **não têm pedidos registrados**:
```
SELECT 
    u.id AS user_id, 
    u.name, 
    u.age
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
WHERE o.id IS NULL;
```

Retorna o **pedido de maior valor** para cada usuário.
```
SELECT 
    u.id AS user_id, 
    u.name, 
    o.id AS order_id, 
    o.total_amount
FROM orders o
INNER JOIN users u ON o.user_id = u.id
WHERE o.total_amount = (
    SELECT MAX(o2.total_amount) 
    FROM orders o2 
    WHERE o2.user_id = u.id
);

```

```
SELECT DISTINCT ON (o.user_id) 
    u.id AS user_id, 
    u.name, 
    o.id AS order_id, 
    o.total_amount
FROM orders o
INNER JOIN users u ON o.user_id = u.id
ORDER BY o.user_id, o.total_amount DESC;
```

Exibir pedidos feitos em **março de 2024**.
```
SELECT 
    o.id AS order_id, 
    u.name AS user_name, 
    o.order_date, 
    o.total_amount, 
    o.status
FROM orders o
INNER JOIN users u ON o.user_id = u.id
WHERE EXTRACT(YEAR FROM o.order_date) = 2024
AND EXTRACT(MONTH FROM o.order_date) = 3;
```

O **MySQL** **NÃO tem suporte nativo** para `FULL JOIN`.  
Para simular o comportamento, você deve **combinar um `LEFT JOIN` e um `RIGHT JOIN` com `UNION`**
```
SELECT 
    u.id AS user_id, 
    u.name, 
    o.id AS order_id, 
    o.total_amount
FROM users u
LEFT JOIN orders o ON u.id = o.user_id

UNION

SELECT 
    u.id AS user_id, 
    u.name, 
    o.id AS order_id, 
    o.total_amount
FROM users u
RIGHT JOIN orders o ON u.id = o.user_id;
```


#### CREATE

```
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL CHECK (price > 0),
    stock INT NOT NULL DEFAULT 0 CHECK (stock >= 0),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

```
CREATE TABLE order_items (
    id SERIAL PRIMARY KEY,
    order_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL CHECK (quantity > 0),
    item_price DECIMAL(10, 2) NOT NULL CHECK (item_price >= 0),
    FOREIGN KEY (order_id) REFERENCES orders(id) ON DELETE CASCADE,
    FOREIGN KEY (product_id) REFERENCES products(id) ON DELETE CASCADE,
    UNIQUE (order_id, product_id) -- evita duplicidade do mesmo produto em um pedido
);
```

#### DROP

```
DROP TABLE orders;
```

```
-- Tabelas dependentes primeiro
DROP TABLE IF EXISTS orders;

-- Por fim, a tabela users
DROP TABLE IF EXISTS users;
```

#### ALTER TABLE

Adicionar coluna:
```
ALTER TABLE users
ADD COLUMN email VARCHAR(150);
```

Renomear coluna:
```
ALTER TABLE orders
RENAME COLUMN status TO order_status;
```

Alterar tipo de coluna:
```
ALTER TABLE orders
ALTER COLUMN total_amount TYPE NUMERIC(12,2);
```

Remover uma coluna
```
ALTER TABLE users
DROP COLUMN has_driver_license;
```

Adicionar constraint:
```
ALTER TABLE users
ADD CONSTRAINT unique_email UNIQUE (email);
```

```
ALTER TABLE users
ADD CONSTRAINT check_age_positive CHECK (age > 0);
```

```
ALTER TABLE orders
ADD CONSTRAINT check_total_positive CHECK (total_amount >= 0);
```

```
ALTER TABLE users
ADD CONSTRAINT unique_name UNIQUE (name);
```

```
ALTER TABLE users
ALTER COLUMN has_driver_license SET DEFAULT FALSE;
```

```
ALTER TABLE users
ALTER COLUMN email SET NOT NULL;
```

