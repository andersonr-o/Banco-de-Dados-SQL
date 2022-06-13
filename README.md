# Maneiras diferentes de se chegar ao mesmo resultado.

Resultado esperado &rightarrow; Queremos o nome dos funcionários que têm o cargo de Engenheiro de Design.<br>
A informação dos cargos se encontram na tabela HumanResources.Employee e os seus nomes na tabela Person.Person<br><br>

As duas maneiras são dinâmicas, isto é, se algum dado mudar, poderíamos rodar o mesmo script e teríamos resultados atualizados.<br><br>

**Primeira maneira:**<br><br>

É um pouco mais simples em seu output. Utilizamos o SUBQUERY (ou SUBSELECT)<br><br> 

```SELECT FirstName```<br>
```FROM Person.Person```<br>
```WHERE BusinessEntityID IN (SELECT BusinessEntityID FROM HumanResources.Employee WHERE JobTitle = 'Design Engineer')```<br><br>

**Segunda maneira:**<br><br>

A saída é um pouco mais decorada. Aqui, usamos o INNER JOIN para juntar as tabelas através do BusinessEntityID.<br><br>

```SELECT HR.BusinessEntityID, HR.JobTitle, CONCAT(PP.FirstName, ' ', PP.LastName) AS "Engenheiros de Design"```<br>
```FROM HumanResources.Employee HR```<br>
```INNER JOIN Person.Person PP ON PP.BusinessEntityID = HR.BusinessEntityID```<br>
```WHERE JobTitle = 'Design Engineer'```

# Como saber qual é melhor?

Basta rodar o "Incluir Plano de Execução Real" junto ao código. Aquele que demonstrar maior porcentagem é o pior, pois demora mais para rodar.<br><br>

Nesse caso os dois demoram a mesma quantidade de tempo para rodar, como vemos no print, sendo opcional a utilização deles.<br><br>

Outro exemplo de como podemos chegar ao mesmo resultado usando scripts diferentes é:<br><br>

Queremos informações de endereço de todo o estado 'Alberta'. Teremos que usar duas tabelas: a Person.Address e a Person.StateProvince<br><br>

**Primeira maneira, usando SUBSELECT:**<br><br>

```SELECT AddressLine1```<br>
```FROM Person.Address```<br>
```WHERE StateProvinceID IN (SELECT StateProvinceID FROM Person.StateProvince WHERE Name = 'Alberta')```<br><br>

**Segunda maneira, usando INNER JOIN:**<br><br>

```SELECT PS.Name, PS.StateProvinceCode, PP.AddressLine1, PP.City```<br>
```FROM PERSON.StateProvince PS```<br>
```INNER JOIN Person.Address PP ON PP.StateProvinceID = PS.StateProvinceID```<br>
```WHERE PS.Name = 'Alberta'```
