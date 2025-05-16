
### Tabela de Informações Disponíveis via `Connection.getMetaData()` (`DatabaseMetaData`)

| Categoria                     | Método                                | Descrição                                                          |
| ----------------------------- | ------------------------------------- | ------------------------------------------------------------------ |
| **Geral sobre o banco**       | `getDatabaseProductName()`            | Nome do SGBD (ex: PostgreSQL, MySQL)                               |
|                               | `getDatabaseProductVersion()`         | Versão do SGBD                                                     |
|                               | `getDriverName()`                     | Nome do driver JDBC em uso                                         |
|                               | `getDriverVersion()`                  | Versão do driver JDBC                                              |
|                               | `getUserName()`                       | Usuário conectado                                                  |
| **Tabelas e Views**           | `getTables(...)`                      | Lista de tabelas, views e outros objetos                           |
|                               | `getSchemas()`                        | Lista de esquemas disponíveis                                      |
|                               | `getCatalogs()`                       | Lista de catálogos (em bancos que usam esse conceito)              |
| **Colunas de tabelas**        | `getColumns(...)`                     | Nome, tipo, tamanho, nullability, autoincremento, etc. das colunas |
|                               | `getPrimaryKeys(...)`                 | Lista de colunas que compõem a chave primária                      |
|                               | `getImportedKeys(...)`                | Foreign keys (restrições de chave estrangeira) da tabela           |
|                               | `getExportedKeys(...)`                | Outras tabelas que referenciam a tabela atual                      |
|                               | `getColumnPrivileges(...)`            | Permissões associadas às colunas                                   |
| **Índices e Chaves**          | `getIndexInfo(...)`                   | Informações sobre índices e unicidade                              |
|                               | `getBestRowIdentifier(...)`           | Melhor identificador para linhas da tabela                         |
| **Tipos de dados suportados** | `getTypeInfo()`                       | Tipos de dados disponíveis no banco                                |
| **Capacidades do banco**      | `supportsTransactions()`              | Se o banco suporta transações                                      |
|                               | `supportsStoredProcedures()`          | Se o banco suporta procedures                                      |
|                               | `supportsBatchUpdates()`              | Se o banco suporta batch updates                                   |
|                               | `supportsSchemasInTableDefinitions()` | Suporte a schemas em tabelas                                       |
|                               | `supportsResultSetType(...)`          | Suporte a diferentes tipos de `ResultSet`                          |
| **Procedures & funções**      | `getProcedures(...)`                  | Lista de stored procedures                                         |
|                               | `getFunctions(...)`                   | Lista de funções definidas no banco (quando suportado)             |
| **Usuários e permissões**     | `getUserName()`                       | Nome do usuário atual conectado                                    |
|                               | `getTablePrivileges(...)`             | Permissões sobre tabelas                                           |

---
