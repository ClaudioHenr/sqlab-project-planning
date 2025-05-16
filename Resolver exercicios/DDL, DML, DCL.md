## 📊 Comparação entre DDL, DML e DCL

|Categoria|Nome Completo|Foco Principal|Exemplos de Comandos|Atua em|Reversível?|Faz COMMIT automático?|
|---|---|---|---|---|---|---|
|**DDL**|Data Definition Language|Estrutura do banco de dados|`CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME`|Estrutura (tabelas, schemas)|❌ Geralmente não|✅ Sim|
|**DML**|Data Manipulation Language|Dados dentro das tabelas|`SELECT`, `INSERT`, `UPDATE`, `DELETE`|Dados|✅ Sim|❌ Não (em geral)|
|**DCL**|Data Control Language|Permissões e segurança|`GRANT`, `REVOKE`|Usuários e permissões|✅ Sim|✅ Depende do SGBD|
