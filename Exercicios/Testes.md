É preciso criar as querys executa-las e compara-las para saber se o exercício foi feito corretamente

**Desafios:**
	Como comparar resultados de querys?
	Como utilizar variadas nomenclaturas de bancos de dados diferentes?


Tipos de querys:


SELECT


INSERT


UPDATE


DELETE


### Test mysql

SELECT * FROM exercise_example;
retorno: 


INSERT INTO exercise_example VALUES
(DEFAULT,  "Dieval", 30);
retorno: 


UPDATE exercise_example 
SET name="Orlando"
WHERE id = 1;
retorno: 


DELETE FROM exercise_example WHERE id=3;
retorno: 



## JDBC Template

jdbcTemplate

.queryForList
	retorna: 

.queryForMap
	retorna: 

.update
	retorna: número de linhas afetadas