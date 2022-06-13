# Criando Tabelas em SQL

Para criarmos tabelas, temos que usar o seguinte código:<br><br>

```CREATE TABLE nomeTabela(```<br>
	```coluna1 | tipo | restricaoDaColuna```<br>
	```coluna2 | tipo | restricaoDaColuna```<br>
	```coluna3 | tipo | restricaoDaColuna```<br>
```)```

## Tipos de Restrições em SQL:

° NOT NULL - Não permite valores nulos;<br><br>
° UNIQUE - Não permite valores duplicados;<br><br>
° PRIMARY KEY - É a junção do Not Null e do Unique;<br><br>
° FOREIGN KEY - É usado para identificar outra tabela dentro da tabela atual;<br><br>
° CHECK - Força uma condição especificada pelo usuário;<br><br>
° DEFAULT - Força um valor padrão quando ela está vazia.

## Exemplo

Suponha que queremos criar um banco de dados para o YouTube (um para os canais e outro para os vídeos).<br>
Precisamos, então, montar as suas estruturas e depois criamos a tabela:<br><br>

*A estrutura da tabela do Canal:*<br><br>

CanalId INT PRIMARY KEY<br>
Nome VARCHAR(150) NOT NULL<br>
ContagemInscritos INT DEFAULT 0 (O valor padrão será 0 na ausência de valores)<br>
DataCriacao DATETIME NOT NULL<br><br>

*Criando a tabela do Canal:*<br><br>

```CREATE TABLE Canal(```<br>
	```CanalId INT PRIMARY KEY,```<br>
	```Nome VARCHAR(150) NOT NULL,```<br>
	```ContagemInscritos INT DEFAULT 0,```<br>
	```DataCriacao DATETIME NOT NULL```<br>
```)```<br><br>


*A estrutura da tabela do Vídeo:*<br><br>

VideoId INT PRIMARY KEY<br>
Nome VARCHAR(150)<br>
Visualizações INT DEFAULT 0<br>
Likes INT DEFAULT 0<br>
Dislikes INT DEFAULT 0<br>
Duracao INT NOT NULL<br>
CanalId INT FOREIGN KEY REFERENCES Canal(CanalId)<br><br>

*Criando a tabela do Vídeo:*<br><br>

```CREATE TABLE Video(```<br>
	```VideoId int primary key,```<br>
	```Nome varchar(150) not null,```<br>
	```Visualizações int default 0,```<br>
	```Likes int default 0,```<br>
	```Dislikes int default 0,```<br>
	```Duracao int default 0,```<br>
	```CanalId int Foreign Key References Canal(CanalId)```<br>
```)```
