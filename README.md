# Como Alterar Dados de uma Tabela

Depois de criadas, as tabelas podem ser mudadas através de uma fórmula bem simples, que será exposta logo abaixo.<br><br>
Dentre as possibilidades, podemos alterar os tipos das tabelas, seus limites e suas restrições. Não conseguimos alterar o nome usando essa fórmula, mas no fim do artigo eu deixei a fórmula que se usa para mudar os nomes de tabelas e colunas do nosso Banco de Dados.

## Fórmula Usada e Como se Usa

Para isso, usamos o comando ALTER TABLE.<br><br>
*Sintaxe:*<br><br>
```ALTER TABLE nomeTabela```<br>
```AÇÃO```<br><br>

O que pode ser feito com o Alter Table:<br><br>

<ul>
<li>Adicionar, remover ou alterar uma coluna
<li>Setar valores padrões para uma coluna
<li>Adicionar ou remover restrições de uma coluna
</ul><br>

*Exemplo (Adicionando uma coluna nova):*<br><br>

```ALTER TABLE nomeTabela```<br>
```ADD Coluna BIT```<br><br>

Adicionei uma coluna, do tipo booleano, em uma tabela.

Alterando parâmetros de uma coluna da tabela:<br><br>
```ALTER TABLE nomeTabela```<br>
```ALTER COLUMN Categoria VARCHAR(300) NOT NULL```<br><br>

Alteramos o seu VARCHAR. Ele poderia ser 100, 200, 400, mas agora é 300. Ele poderia ser do tipo inteiro, mas agora é VARCHAR de 300 e não nulo.<br><br>

## Para mudar o nome de uma coluna ou tabela:

Não usamos o Alter Table, mas sim o EXEC. Sintaxe:<br><br>

```EXEC sp_RENAME 'nomeTabela.nomeColunaAtual', 'nomeColunaNova', 'COLUMN'```<br>

*Exemplo:*<br><br>

```EXEC sp_RENAME 'Twitter.ativo', 'Ativo', 'COLUMN'```<br><br>

Alteramos o nome de "ativo" para "Ativo"<br><br>

*Exemplo de alteração no nome de uma tabela:*<br><br>

```EXEC sp_RENAME 'novo', 'velho'```
