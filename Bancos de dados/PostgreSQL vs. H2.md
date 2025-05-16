
`H2` com `MODE=PostgreSQL`

## Cláusulas do PostgreSQL Suportadas pelo H2 (modo PostgreSQL)

|**Cláusula**|**PostgreSQL**|**H2 (modo PostgreSQL)**|**Observação**|
|---|---|---|---|
|`CREATE TABLE`|✅|✅|Suporta criação de tabelas normalmente|
|`INSERT INTO`|✅|✅|Suporta inserções básicas|
|`UPDATE`|✅|✅|Suporta atualização de registros|
|`DELETE`|✅|✅|Suporta remoção de registros|
|`SELECT`|✅|✅|Consultas básicas e avançadas funcionam|
|`JOIN` (`INNER`, `LEFT`, `RIGHT`, `FULL`)|✅|✅|Todos os tipos de `JOIN` são suportados|
|`GROUP BY`|✅|✅|Funciona normalmente, mas sem `WITH ROLLUP`|
|`HAVING`|✅|✅|Filtragem de agregações funciona|
|`ORDER BY`|✅|✅|Ordenação de resultados|
|`LIMIT`|✅|✅|Funciona para paginação|
|`OFFSET`|✅|✅|Funciona para pular registros|
|`DISTINCT`|✅|✅|Funciona para remover duplicatas|
|`UNION` e `UNION ALL`|✅|✅|Combina resultados de múltiplas consultas|
|`EXISTS`|✅|✅|Subconsultas funcionam corretamente|
|`IN` e `NOT IN`|✅|✅|Funciona em filtros de consulta|
|`CASE`|✅|✅|Permite condicionais dentro da consulta|
|`BETWEEN`|✅|✅|Filtra intervalos de valores|
|`LIKE` e `ILIKE`|✅|✅|Funciona para buscas textuais|
|`IS NULL` e `IS NOT NULL`|✅|✅|Suporta verificação de `NULL`|
|`CAST()`|✅|✅|Converte tipos de dados|
|`COALESCE()`|✅|✅|Retorna o primeiro valor não nulo|
|`ROUND()`, `CEIL()`, `FLOOR()`|✅|✅|Funções matemáticas básicas|
|`LENGTH()`, `SUBSTRING()`, `CONCAT()`|✅|✅|Manipulação de strings|
|`NOW()`, `CURRENT_TIMESTAMP`, `CURRENT_DATE`|✅|✅|Funções de data e hora|
|`EXTRACT(YEAR FROM data)`|✅|✅|Extrai partes de datas|
|`REGEXP` (expressões regulares)|✅|✅|Suporta padrões em strings|
|`SERIAL`|✅|✅|Simula auto incremento (`AUTO_INCREMENT`)|
|`FOREIGN KEY`|✅|✅|Suporta chaves estrangeiras|
|`CHECK`|✅|✅|Restrições de validação|
|`ALTER TABLE`|✅|✅|Modifica estrutura da tabela|
|`DROP TABLE`|✅|✅|Remove tabelas do banco|

---

## Principais diferenças entre **PostgreSQL** e **H2 (modo PostgreSQL)**:

|**Recurso**|**PostgreSQL**|**H2 (modo PostgreSQL)**|
|---|---|---|
|`RETURNING` no `INSERT`, `UPDATE`, `DELETE`|✅ Suportado|❌ Não suportado|
|`DISTINCT ON`|✅ Suportado|❌ Não suportado|
|`FOR UPDATE SKIP LOCKED`|✅ Suportado|❌ Não suportado|
|Tipos de dados `JSONB` e `JSON`|✅ Suportado (`JSONB` e `JSON`)|⚠️ Apenas `JSON` simples|
|Funções de janela (`ROW_NUMBER()`, `RANK()`, etc.)|✅ Suportado|⚠️ Suporte limitado|
|`DO` para blocos PL/pgSQL|✅ Suportado|❌ Não suportado|
|Constraint `EXCLUDE`|✅ Suportado|❌ Não suportado|
|`TABLESAMPLE`|✅ Suportado|❌ Não suportado|
|`SET CONSTRAINTS`|✅ Suportado|❌ Não suportado|
|`DEFERRABLE` em constraints|✅ Suportado|❌ Não suportado|
|Tipos `int4range`, `numrange`, `tsrange`|✅ Suportado|❌ Não suportado|
|`CREATE INDEX CONCURRENTLY`|✅ Suportado|❌ Não suportado|
|`WITH RECURSIVE` em CTEs|✅ Suportado|❌ Não suportado|
|`SIMILAR TO` e expressões regulares avançadas|✅ Suportado|⚠️ Suporte limitado|
|`LISTEN` / `NOTIFY` (comunicação assíncrona)|✅ Suportado|❌ Não suportado|


## Detalhes das cláusulas do PostgreSQL que **não são suportadas** pelo H2

### `RETURNING`

`INSERT INTO users (name) VALUES ('Olavo') RETURNING id;`

### **`FOR UPDATE` com `SKIP LOCKED`**

No PostgreSQL, a cláusula `SKIP LOCKED` pode ser usada com a instrução `FOR UPDATE` para ignorar linhas que estão bloqueadas. O H2 não suporta o `SKIP LOCKED`.

`SELECT * FROM users WHERE status = 'pending' FOR UPDATE SKIP LOCKED;`

### `DISTINCT ON`

`SELECT DISTINCT ON (id) id, name FROM users ORDER BY id, name;`

### `JSONB`

O H2 não suporta esse tipo de dados, embora o H2 tenha suporte limitado para o tipo `JSON` simples.

### Funções de Janela (Window Functions)

O PostgreSQL oferece suporte completo para funções de janela (ex. `ROW_NUMBER()`, `RANK()`, `LEAD()`, `LAG()`). O H2 tem suporte limitado e não oferece todas as funções de janela que o PostgreSQL tem.

`SELECT name, ROW_NUMBER() OVER (ORDER BY name) FROM users;`

### `DO` para blocos anônimos de código PL/pgSQL

O PostgreSQL suporta a execução de blocos anônimos com a instrução `DO`, que permite a execução de código PL/pgSQL diretamente. O H2 não suporta essa funcionalidade.

```
DO $$ 
BEGIN
  -- Código PL/pgSQL
END $$;
```

### `EXCLUDE` Constraint

O PostgreSQL oferece o comando `EXCLUDE` para definir restrições de exclusão, permitindo criar regras mais complexas que não podem ser expressas apenas com chaves primárias ou estrangeiras. O H2 não suporta essa cláusula.

```
CREATE TABLE events (
  room int,
  during tstzrange,
  EXCLUDE USING gist (room WITH =, during WITH &&)
);
```

### **`TABLESAMPLE`**

O PostgreSQL oferece a cláusula `TABLESAMPLE`, que permite amostrar uma porcentagem das linhas de uma tabela de maneira aleatória. O H2 não suporta essa funcionalidade.

`SELECT * FROM users TABLESAMPLE SYSTEM (10);`

### `SET CONSTRAINTS`

O PostgreSQL permite o uso de `SET CONSTRAINTS` para definir quando as verificações de restrições devem ser executadas. O H2 não oferece suporte para isso.

`SET CONSTRAINTS ALL IMMEDIATE;`

### Cláusula `DEFERRABLE` para `CONSTRAINTS`

O PostgreSQL permite que você defina restrições `DEFERRABLE`, que podem ser adiadas até o final de uma transação. O H2 não tem suporte para esse tipo de restrição.

```
CREATE TABLE my_table (
  id SERIAL PRIMARY KEY,
  CONSTRAINT my_constraint FOREIGN KEY (other_id) REFERENCES other_table DEFERRABLE INITIALLY DEFERRED
);
```

### `RANGE` para o tipo de dado `int4range`, `numrange`, etc.

```
CREATE TABLE my_table (
  range_column int4range
);
```

