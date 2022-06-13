# Criando Tabelas em SQL

Para criarmos tabelas, temos que usar o seguinte código:<br><br>

```CREATE TABLE nomeTabela(```
	```coluna1 | tipo | restricaoDaColuna```
	```coluna2 | tipo | restricaoDaColuna```
	```coluna3 | tipo | restricaoDaColuna```
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

```CREATE TABLE Canal(```
	```CanalId INT PRIMARY KEY,```
	```Nome VARCHAR(150) NOT NULL,```
	```ContagemInscritos INT DEFAULT 0,```
	```DataCriacao DATETIME NOT NULL```
```)```<br><br>


*A estrutura da tabela do Vídeo:*<br><br>

VideoId INT PRIMARY KEY
Nome VARCHAR(150)
Visualizações INT DEFAULT 0
Likes INT DEFAULT 0
Dislikes INT DEFAULT 0
Duracao INT NOT NULL
CanalId INT FOREIGN KEY REFERENCES Canal(CanalId)<br><br>

*Criando a tabela do Vídeo:*<br><br>

```CREATE TABLE Video(```
	```VideoId int primary key,```
	```Nome varchar(150) not null,```
	```Visualizações int default 0,```
	```Likes int default 0,```
	```Dislikes int default 0,```
	```Duracao int default 0,```
	```CanalId int Foreign Key References Canal(CanalId)```
```)```
