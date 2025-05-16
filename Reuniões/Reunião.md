
CRUD AUTOCADASTRO DE PROFESSOR  
CRUD CADASTRO DE ALUNO  
CRUD DE TURMAS  
VINCULAR ALUNOS A TURMAS (PROFESSOR VÍNCULA)  
ALUNO ACESSO AS QUESTÕES A PARTIR DE SUA VÍNCULAÇÃO A TURMA  
INSERIR QUESTÕES -> RESPOSTA(S) CORRETA(S) -> CAMPO DE NOTA DA QUESTÃO  
TABELA DE LOGS DE TENTATIVAS  
VALIDAÇÃO DA RESPOSTA  
RELATÓRIO DE DESEMPENHO DE ALUNO INDIVIDUAL  
NOTA GERAL DO ALUNO (TIPO A NOTA DO SEMESTRE A PARTIR DAS NOTAS DAS LISTAS/EXERCICIOS)

Talvez

??RELATÓRIOS??  
??FÓRUM??  
??TABELA RELACIONAMENTO COM NOTAS DOS ALUNOS??  
??VISUALIZAÇÃO E FEEDBACK DO PROFESSOR SOBRE AS TENTATIVAS DO ALUNO??  
??CHAT COM O PROFESSOR??  
??RANKING DO DESEMPENHO DOS ALUNOS PONTUAÇÃO GERAL E POR QUESTÃO??  
??LISTA DE EXERCICIOS??





Pesquisar o uso de Transaction -> rollBackFor, rollBackForClass etc para tentar usar uma classe de verificação customizada ou algo assim...

Classe genérica de configuração de banco de dados para ser possível usar vários bancos na plataforma

Acessar metadados das tabelas temporárias, independentemente do banco

Usar ou não tabelas temporárias??

Validar utilizando metadados pois string tem muita possibilidade de erros

TESTAR

Uso de rollback

Comparação utilizando metadados

Ver níveis de segurança

Ver segurança quanto a querys maus...


### Reunião

Chave composta em answer_student
	id answer_student e id student

Devido a alta chance de estourar...
Uso de MAX

Avançar com update, insert e delete

Reunião depois da semana do dia 9
Dia 15 reunião

Para 01/05
Israel -> Terminar Autocadastro front/back
	Terminar Login front/back
	Terminar cadastro ALUNO
	Terminar cadastro PROFESSOR

Claudio -> Estruturar as mudanças relacionais do banco,
	update, insert, delete

Michelly -> Estrutura e fluxo telas do professor no front
	Cadastro de exercício

### Reunião - 02/05

Israel -> Esqueci minha senha
	Revisão de validações
	Editar perfil - professor/student
	Backend CRUD Turma
	Backend CRUD Listas


Claudio -> Testar mais tipos de queries de exercícios
	Revisar função de comparação de resultados das queries, -> Validação de metadados de ALTER TABLE, etc
	Alterar campo type_exercise para entidade Exercise
	Estudante (FRONT):
		Montagem turmas- listagem
		Montagem listas - listagem
		Montagem exercícios - listagem


Michelly -> Estrutura e fluxo telas do professor no front
	Telas -> turmas - listas - exercícios
		Montagem especificas de turmas- listagem/cadastro/edição
		Montagem especificas de listas - listagem/cadastro/edição
		Montagem especificas de exercícios - listagem/cadastro/edição -> Adicionar nome tabela no cadastro do exercício - setar o tipo de exercício

### Reunião - 11/05

Israel -> Esqueci minha senha
	Revisão de validações
	Editar perfil - professor/student
	Backend CRUD Turma
	Backend CRUD Listas


Claudio -> Testar mais tipos de queries de exercícios
	Revisar função de comparação de resultados das queries, -> Validação de metadados de ALTER TABLE, etc
	Alterar campo type_exercise para entidade Exercise


Michelly -> Estrutura e fluxo telas do professor no front
	Telas -> turmas - listas - exercícios
		Montagem especificas de turmas- listagem/cadastro/edição
		Montagem especificas de listas - listagem/cadastro/edição
		Montagem especificas de exercícios - listagem/cadastro/edição -> Adicionar nome tabela no cadastro do exercício - setar o tipo de exercício

Vácuo -> 
	Estudante (FRONT):
	Montagem turmas- listagem
	Montagem listas - listagem
	Montagem exercícios - listagem