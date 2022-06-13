## CHECK Constraint

Para criarmos restrições específicas de númersos em um banco de dados, usamos o CHECK, como já visto em outros artigos.<br>
Porém ainda não o vimos na prática. Sua sintaxe na criação da tabela:<br><br>

```CREATE TABLE CarteiraMotorista(```<br>
	```Id INT NOT NULL,```<br>
	```Nome VARCHAR(255) NOT NULL,```<br>
	```Idade INT CHECK(Idade >= 18)```<br>
```)```<br><br>

Ou seja, se houver um Insert na idade mmenor que 18, o banco irá conflitar e esse valor não será inserido, porque menor de idade não pode tirar carteira de motorista.<br><br>

Mais um exemplo:<br><br>

```CREATE TABLE SalarioMensal(```<br>
	```Id INT PRIMARY KEY,```<br>
	```Nome VARCHAR(20) NOT NULL,```<br>
	```Idade INT NOT NULL,```<br>
	```Salário INT CHECK(Salário < 100000000)```<br>
```)```<br><br>

Dessa vez de uma tabela que não aceita que o salário de alguém seja maior que 100 milhões.<br><br>

Sendo assim, um Insert assim seria rejetiado:<br><br>

INSERT INTO SalarioMensal(Id, Nome, Idade, Salário) VALUES (1, 'LeitorBonito', 19, 100000000)

## NOT NULL Constraint

Usamos a restrição "NOT NULL" quando não aceitamos valor nulo em um campo, ou seja, o usuário tem que preenchê-lo com algum valor.<br><br>

Sua sintaxe é bem simples e é ainda mais fácil que o CHECK Constraint, e já o usamos na criação da tabela acima. Veja:<br><br>

```CREATE TABLE CarteiraMotorista(```<br>
	```Id INT NOT NULL,```<br><br>

Basta colocarmos "NOT NULL" na parte de restrição e pronto.

## UNIQUE Constraint

Quando precisamos de um valor único para alguma coluna, usamos a restrição UNIQUE.<br>
A diferença do UNIQUE para o PRIMARY KEY é que a PRIMARY KEY só é usada uma única vez por tabela, enquanto o UNIQUE não tem limites.<br><br>

Sintaxe já em forma de exemplo:<br><br>

```CREATE TABLE PlacaCarro(```<br>
	```Id INT NOT NULL,```<br>
	```Nome VARCHAR(20) NOT NULL,```<br>
	```Placa VARCHAR(7) NOT NULL UNIQUE```<br>
```)```<br><br>

Esse Insert Into, por exemplo, não seria aceitado duas vezes:<br><br>

```INSERT INTO PlacaCarro(Id, Nome, Placa)```<br>
```VALUES (1, 'Anderson', 'BRA0S20')```
