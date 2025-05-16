
# PostgreSQL vs. MySQL

## **1. Tipos de Dados**

|**Tipo**|**PostgreSQL**|**MySQL**|**Diferença**|
|---|---|---|---|
|Auto Incremento|`SERIAL`|`AUTO_INCREMENT`|O PostgreSQL usa `SERIAL`, enquanto o MySQL usa `AUTO_INCREMENT`.|
|Data/Hora|`TIMESTAMP`, `DATE`|`DATETIME`, `DATE`|O PostgreSQL tem um suporte mais avançado para fusos horários com `TIMESTAMP WITH TIME ZONE`.|
|Texto|`TEXT`, `VARCHAR(n)`|`TEXT`, `VARCHAR(n)`|Ambos suportam, mas o PostgreSQL trata `TEXT` como ilimitado sem impacto na performance.|

---

## **2. Criando Tabelas**

### **PostgreSQL**

`CREATE TABLE users (     id SERIAL PRIMARY KEY,     name VARCHAR(100) NOT NULL,     email VARCHAR(255) UNIQUE NOT NULL );`

### **MySQL**

`CREATE TABLE users (     id INT AUTO_INCREMENT PRIMARY KEY,     name VARCHAR(100) NOT NULL,     email VARCHAR(255) UNIQUE NOT NULL );`

✅ **Diferença:** PostgreSQL usa `SERIAL`, enquanto MySQL usa `AUTO_INCREMENT`.

---

## **3. Inserindo Dados**

### **PostgreSQL**

`INSERT INTO users (name, email) VALUES ('Alice', 'alice@email.com') RETURNING id;`


**O H2 não suporta a cláusula `RETURNING` como o PostgreSQL**

### **MySQL**

`INSERT INTO users (name, email) VALUES ('Alice', 'alice@email.com'); SELECT LAST_INSERT_ID();`

✅ **Diferença:** PostgreSQL permite `RETURNING` para obter o ID gerado, enquanto MySQL usa `LAST_INSERT_ID()`.

