`getMetaData()` do `ResultSet`

Principais propriedades que se pode obter sobre as colunas de uma tabela:

| **Informação**                       | **Método**                              | **Descrição**                                                                                                                                      |
| ------------------------------------ | --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Número de Colunas**                | `getColumnCount()`                      | Retorna o número total de colunas na consulta.                                                                                                     |
| **Nome da Coluna**                   | `getColumnName(int columnIndex)`        | Retorna o nome da coluna com base no índice (começando em 1).                                                                                      |
| **Tipo de Dados da Coluna**          | `getColumnType(int columnIndex)`        | Retorna o tipo SQL da coluna (valor inteiro, corresponde a constantes do `java.sql.Types`).                                                        |
| **Nome do Tipo de Dados**            | `getColumnTypeName(int columnIndex)`    | Retorna o nome do tipo de dados da coluna (por exemplo, `VARCHAR`, `INT`, `DATE`).                                                                 |
| **Permite NULL?**                    | `isNullable(int columnIndex)`           | Retorna se a coluna permite valores `NULL` (com base nos valores de `ResultSetMetaData.columnNoNulls`, `columnNullable`, `columnNullableUnknown`). |
| **Precisão da Coluna**               | `getPrecision(int columnIndex)`         | Retorna o número de dígitos ou caracteres de uma coluna (para tipos numéricos ou strings).                                                         |
| **Escala da Coluna**                 | `getScale(int columnIndex)`             | Retorna o número de casas decimais para uma coluna de tipo numérico.                                                                               |
| **Auto-Incremento**                  | `isAutoIncrement(int columnIndex)`      | Retorna `true` se a coluna for auto-incremento (por exemplo, chave primária).                                                                      |
| **Leitura Apenas (Read-Only)**       | `isReadOnly(int columnIndex)`           | Retorna `true` se a coluna for apenas leitura e não pode ser alterada.                                                                             |
| **Se a Coluna Pode Ser Gravada**     | `isWritable(int columnIndex)`           | Retorna `true` se a coluna puder ser escrita (dados podem ser alterados).                                                                          |
| **Tamanho da Coluna (Display Size)** | `getColumnDisplaySize(int columnIndex)` | Retorna o tamanho máximo exibido da coluna (ou o número de caracteres se for do tipo `VARCHAR`).                                                   |
| **Tabela da Coluna**                 | `getTableName(int columnIndex)`         | Retorna o nome da tabela à qual a coluna pertence.                                                                                                 |
| **Esquema da Coluna**                | `getSchemaName(int columnIndex)`        | Retorna o nome do esquema da tabela à qual a coluna pertence.                                                                                      |
| **Classe Java da Coluna**            | `getColumnClassName(int columnIndex)`   | Retorna o nome da classe Java que representa os dados da coluna.                                                                                   |

Essa tabela fornece uma visão completa das informações que você pode acessar usando `ResultSetMetaData`, permitindo explorar a estrutura de qualquer conjunto de resultados retornado por uma consulta SQL, incluindo detalhes sobre o tipo de dados, permissão para `NULL`, auto-incremento e outras propriedades das colunas.