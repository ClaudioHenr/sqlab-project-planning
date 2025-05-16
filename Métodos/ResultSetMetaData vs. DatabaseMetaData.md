
O `ResultSetMetaData` vem de `ResultSet.getMetaData()`
O `DatabaseMetaData` vem de `Connection.getMetaData()`

### Tabela de Comparação: `ResultSetMetaData` vs `DatabaseMetaData`

| Critério                           | `ResultSet.getMetaData()` (`ResultSetMetaData`)              | `Connection.getMetaData()` (`DatabaseMetaData`)            |
| ---------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| **Objetivo principal**             | Descrever as **colunas retornadas por uma query** (`SELECT`) | Descrever a **estrutura do banco de dados** completo       |
| **Origem**                         | A partir de um `ResultSet` (de uma query executada)          | A partir de uma `Connection` ativa com o banco             |
| **Escopo de análise**              | Apenas o resultado de uma consulta específica                | Todas as tabelas, colunas, chaves, views, índices do banco |
| **Tipo retornado**                 | `ResultSetMetaData`                                          | `DatabaseMetaData`                                         |
| **Precisa de query prévia?**       | ✅ Sim — requer execução de um `SELECT`                       | ❌ Não — pode ser acessado diretamente pela conexão         |
| **Informa nome de colunas**        | ✅ Sim                                                        | ✅ Sim                                                      |
| **Informa tipo de dados**          | ✅ Sim (`getColumnTypeName()`)                                | ✅ Sim (`getColumns(...)`)                                  |
| **Informa se é NULL/NOT NULL**     | ✅ Sim (`isNullable()`)                                       | ✅ Sim (`IS_NULLABLE` via `getColumns(...)`)                |
| **Informa tamanho da coluna**      | ✅ Sim (`getPrecision()`)                                     | ✅ Sim (`COLUMN_SIZE` via `getColumns(...)`)                |
| **Informa chave primária**         | ❌ Não                                                        | ✅ Sim (`getPrimaryKeys(...)`)                              |
| **Informa chave estrangeira**      | ❌ Não                                                        | ✅ Sim (`getImportedKeys(...)`)                             |
| **Informa se é autoincremento**    | ✅ Sim (`isAutoIncrement()`)                                  | ✅ Sim (`IS_AUTOINCREMENT` via `getColumns(...)`)           |
| **Permite descobrir tabelas?**     | ❌ Não                                                        | ✅ Sim (`getTables(...)`)                                   |
| **Permite descobrir views?**       | ❌ Não                                                        | ✅ Sim (`getTables(..., new String[]{"VIEW"})`)             |
| **Usado para comparar resultados** | ✅ Ideal para comparar com valores de uma query               | ❌ Não usado para dados, mas sim para estrutura             |
| **Compatível com constraints**     | ❌ Limitado                                                   | ✅ Suporta verificação de constraints (PK, FK, etc.)        |

---