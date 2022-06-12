# Tipos de Dados em SQL

São eles:

1. Booleanos
2. Caractere
3. Números
4. Temporais

## Booleanos

É inicializado como nulo, mas pode receber também o valor 0 e 1. Usamos ele como "BIT" no SQL Server.

## Caractere

Há dois tipos de caracteres: os de tamanho fixo e os de tamanhoo variáveis.<br><br>

Os de tamanho fixo ocupam espaço que você determinou na memória. Se você definiu  seu tamanho como sendo 50, 50 espaçoes de caracter serão reservados na memória, mesmo que você não os use.<br>
Usamos como "char" no SQL<br><br>

Os de tamanho variável ocupam somente o espaço de caracteres que você utilizar; é dinâmico.<br>
Usamos como "varchar" ou "nvarchar" no SQL Server.<br><br>

## Números

### Valores Exatos

Não tem valores fracionados; são os números inteiros.<br><br>

<ul>
<li>O TINYINT são os valores exatos no SQL<br>
<li>O SMALLINT é a  mesma coisa, porém com limites maiores.<br>
<li>O INT é a  mesma coisa, porém com limites maiores.<br>
<li>O BIGINT é a  mesma coisa, porém com limites maiores.<br>
<li>NUMERIC ou DECIMAL são valores exatos, porém que permitem parte fracionada, especificando precisão (número de digitos suportados) e escala (número de digitos na parte fracional) -ex: NUMERIC (5, 2)
</ul>

### Valores Aproximados

<ul>
<li>REAL - Tem uma precisão aproximada de até 15 dígitos.
<li>FLOAT - É a mesma coisa do real
</ul>
  
### Valores Temporais

<ul>
<li>DATE - Armazena a data no formato AAAA/MM/DD
<li>DATETIME - Aramzena data e horas no formato AAAA/MM/DD:HH:MM:SS
<li>DATETIME2 - É mais específico que o DATETIME, especificando também os milissegundos no formato AAAA/MM/DD:HH:MM:SSSSSS
<li>SMALLDATETIME - Armazena data e hora dentro do limite: '1900-01-01:00:00:00' até '2079-06-06:23:59:59'
<li>TIME - Armazena apenas horas, minutos, segundos e milissegundos, respeitando o limite '00:00:00.000000' até '23:59:59.999999'
<li>DATETIMEOFFSET - Armazena data e hora e também fuso horário.
</ul>
