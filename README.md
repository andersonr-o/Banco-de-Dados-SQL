# Como Criar Visualizações em SQL

Geralmente usada para a criação de relatórios, a Visualização é uma maneira que temos de extrair dados específicos de uma tabela já existente e colocarmos em uma tabela nova, que será usada para consulta.<br><br>

Sintaxe + Exemplo:<br><br>

CREATE VIEW [Pessoas Simplificado] AS
SELECT FirstName, MiddleName, LastName
FROM Person.Person
WHERE Title = 'Ms.'

Entre colchetes, é o nome dado à nossa tabela genérica.<br><br>

Depois de AS, será tudo o SELECT da tabela já existente.<br><br>

Nesse caso, extraímos três colunas (FirstName, MiddleName e LastName) da tabela Person.Person com a condição do título = "Ms.".<br><br>

Depois de dado o enter, temos a visualização com o nome "Pessoas Simplificado" disponível.
