### SELECT

Fluxo
	1- Recebimento de query
	2- Salvar query em answer_student
	3- Recuperar query resposta de answer_professor/resposta pré cadastrada
	4- Criar 'ambiente'
		1- Criar conexão com DB H2
		2- Executar criação de tabelas do exercicio
	5- Executar as duas queries
	6- Comparar resultados das duas queries
	7- Se correto, setar em aswer_student -> correto
	7- Retornar
		- Certo/Errado
		- Resultado da query

O exercício decide o dialeto

### INSERT

#### Funções

`.getGeneratedKeys()`
`statement.RETURN_GENERATED_KEYS`
`statement.getUpdateCount()`

### UPDATE | DELETE
Ideias 
	1-	Criar dois ambientes, ou seja, duas conexões com exatamente as mesmas tabelas de exercícios
	2- Criar um ambiente e utilizar transação ao executar a queries para não alterar a(s) tabela(s)
	3- Para comparação: 
		1- Executar SELECT * FROM [nome table] nas duas, depois fazer a comparação normal entre tabelas
		2- Executar query para trazer apenas a(s) coluna(s) modificadas
		

Executar query
Recuperar id(s) criados
Executar query recuperando linhas criadas -> `stmt.getGeneratedKeys()`
Comparar resultados das duas queries

Fluxo
	1- Recebimento de query
	2- Salvar query em answer_student
	3- Recuperar query resposta de answer_professor/resposta pré cadastrada
	4- Criar 2 'ambientes'
		1- Criar conexão com DB H2
		2- Executar criação de tabelas do exercício
	5- Executar as duas queries, uma em cada ambiente
	6- Executar SELECT * FROM [nome_tabela] nos dois 'ambientes'
	7- Comparar resultados do passo 6
	8- Retornar
		- Certo/Errado
		- Resultado da query

#### Ideias

Criação de tabelas de exercícios pelo professor
	Cadastrar e validar query de criação das tabelas fornecido pelo professor
	Guardar em uma coluna a query de criação, dai utilizar ela na resolução do exercício para criar o 'ambiente'



