Para verificar tentativas de solução e exercícios, vamos tentar por camadas:

Quais camadas?

## Usando `JDBC` puro
### Ideias de camadas de verificação das tentativas de respostas

Para recuperar informações de tabela -> ´getMetaData()´

#### Verificação de criação de tabela

**Clausulas corretas?**
Dá para conferir se na resposta dada há as clausulas necessárias para a resposta

Vantagens: verificação precoce de se esta certo ou errado
Desvantagem: como mesmo se o usuário mandar a resposta incorreta, ainda sim devemos enviar a resposta da query na tabela de exercício

**Verificar colunas**
Pode-se:
Verificar quantidade com `getColumnCount()`
Verificar nomes com `getColumnName(int columnIndex)`
Verificar tipos com `getColumnType(int columnIndex)` ou `getColumnTypeName(int columnIndex)`



