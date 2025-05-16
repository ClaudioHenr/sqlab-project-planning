
`H2` com `MODE=MySQL`

## Cláusulas suportadas pelo H2 (modo MySQL)

|**Cláusula**|**MySQL**|**H2 (modo MySQL)**|**Observação**|
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
|`IFNULL()`|✅|✅|Retorna um valor alternativo se for `NULL`|
|`ROUND()`, `CEIL()`, `FLOOR()`|✅|✅|Funções matemáticas básicas|
|`LENGTH()`, `SUBSTRING()`, `CONCAT()`|✅|✅|Manipulação de strings|
|`NOW()`, `CURDATE()`, `CURTIME()`|✅|✅|Funções de data e hora|
|`DATE_ADD()` e `DATE_SUB()`|✅|✅|Adiciona ou subtrai tempo|
|`EXTRACT(YEAR FROM data)`|✅|✅|Extrai partes de datas|
|`REGEXP` (expressões regulares)|✅|✅|Suporta padrões em strings|
|`AUTO_INCREMENT`|✅|✅|Funciona para geração automática de IDs|
|`FOREIGN KEY`|✅|✅|Suporta chaves estrangeiras|
|`CHECK`|✅|✅|Restrições de validação|
|`ALTER TABLE`|✅|✅|Modifica estrutura da tabela|

---

## Principais cláusulas do **MySQL** que o **H2 (modo MySQL)** **não suporta**:

|**Cláusula/Recurso**|**MySQL**|**H2 (modo MySQL)**|
|---|---|---|
|`INSERT ... RETURNING`|✅ Suportado (desde MySQL 8.0.23)|❌ Não suportado|
|`ON DUPLICATE KEY UPDATE`|✅ Suportado|❌ Não suportado|
|`LOCK IN SHARE MODE`|✅ Suportado|❌ Não suportado|
|`FOR UPDATE SKIP LOCKED`|✅ Suportado|❌ Não suportado|
|`JSON_TABLE()`|✅ Suportado|❌ Não suportado|
|`IGNORE` em `INSERT`|✅ Suportado|❌ Não suportado|
|`INDEX HINTS` (`USE INDEX`, `IGNORE INDEX`)|✅ Suportado|❌ Não suportado|
|`REPLACE INTO` (substitui `INSERT`)|✅ Suportado|❌ Não suportado|
|`REGEXP_LIKE()`, `REGEXP_REPLACE()`|✅ Suportado|❌ Não suportado|
|`WITH ROLLUP` em `GROUP BY`|✅ Suportado|❌ Não suportado|
|`SELECT ... INTO OUTFILE`|✅ Suportado|❌ Não suportado|
|`LIMIT ... OFFSET` com múltiplos valores|✅ Suportado|⚠️ Suporte parcial|
|`SHOW CREATE TABLE`|✅ Suportado|❌ Não suportado|
|`SHOW STATUS`|✅ Suportado|❌ Não suportado|
|`SHOW VARIABLES`|✅ Suportado|❌ Não suportado|
|`SHOW ENGINE STATUS`|✅ Suportado|❌ Não suportado|
|`STORED PROCEDURES` e `FUNCTIONS`|✅ Suportado|❌ Não suportado|
|`EVENT` Scheduler|✅ Suportado|❌ Não suportado|
|`SPATIAL INDEX`|✅ Suportado|❌ Não suportado|
