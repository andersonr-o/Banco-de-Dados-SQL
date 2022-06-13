# Chave Primária (PK)

Uma chave primária é basicamente uma coluna ou grupo de colunas, que identificam uma linha dentro da tabela.<br>
Chaves primárias são criadas através de constraints, que são regras que você define ao criar uma coluna.<br>
Quando você faz isso, está criando um índice único para aquela coluna. PKs não se repetem.<br><br>

Criando uma PK:

CREATE TABLE nome_Tabela(
	nomeColuna tipoDeDados PRIMARY KEY
	nomeColuna tipoDeDados...
)

# Chave Estrangeira (FK)

É uma coluna ou grupo de colunas em uma tabela que identifica unicamente uma linha em outra tabela.<br><br>
Ela é uma referência dentro de outra tabela, não abrangendo todos os dados que estão ali. Geralmente são números ou strings.<br><br>
Chave de referência é a representação de uma chave primária em outra tabela.<br><br>
A tabela que recebe a chave estrangeira é chamada de tabela referenciadora ou tabela filho. A tabela que contém a chave primária e a estrangeira é chamada de tabela referenciada ou tabela pai.<br><br>
Uma tabela pode ter mais de uma chave estrangeira dependendo da sua relação com as outras tabelas.<br><br>

No SQL Server, você define uma chave estrangeira através de um "Foreign Key Constraint".<br><br>
Uma Foreign Key Constraint indica a relação entre os valores que estão na tabela filho e os valores que estão na tabela pai, ou seja, que indicam a mesma coisa em lugares diferentes.
Essa construção de relação mantém a integridade referencial dos dados, isto é, estarão em mais lugares fazendo a conversação e funcionamento.
