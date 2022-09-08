# Modelagem de Banco de Dados

Há três tipos de modelagem de banco de dados: a conceitual, a lógica e a física.

Elas servem para desenharmos o banco de dados e podermos trabalhar da melhor maneira, além de mostrar, de forma clara, o nosso banco de dados para leigos (que pode ser o diretor que aprovará o orçamento do projeto).

## Modelagem Conceitual

A modelagem conceitual é a mais básica das três. Quando estamos nessa parte, o banco de dados a ser utilizado ainda não importa muito.

A modelagem conceitual é a análise dos elementos e fenômenos relevantes de uma realidade observada ou imaginada e a posterior formação de um modelo abstrato do corpo de conhecimento adquirido: o Modelo Entidade-Relacionamento, ou MER.

Aqui buscamos algumas coisas básicas:

- Conhecer a situação problema; a realidade nebulosa;
- Define a forma das estruturas que receberão os dados;
- Levanta fatos que nos permite conhecer e tornar a realidade mais organizada (fichas, memorandos, leis);
- Representação gráfica do banco de dados.

### Para que serve o MER

O MER serve para criar um desenho do banco de dados para aqueles que não tem conhecimento técnico entenderem ou pode ser usada para discussão entre as partes interessadas numa empresa.

### Composição do MER

O MER é composto por um conjunto de objetos denominados entidades e pelo conjunto de relacionamento entre esses objetos.

Por exemplo:

![MER-exemplo-simples](https://user-images.githubusercontent.com/97858145/189017317-c90781bc-e04f-473a-8b39-4d2b8a883969.png)

"Cliente" e "Produto" em retangulo são as entidades e o losango representa o relacionamento entre essas duas entidades.

O que esse MER quer nos dizer é que Cliente compra Produto.


### Cardinalidade

Também chamado de grau de relacionamento, a cardinalidade nos diz quantas vezes uma entidade pode se relacionar com a outra.

- Um para Um (1:1): Uma entidade pode ou deve se relacionar com uma, apenas uma, instância de outra entidade;
- Um para Muitos (1:N): Uma instância de uma entidade pode ou deve se relacionar com uma ou mais instâncias de outra entidade. É a cardinalidade mais encontrada em banco de dados;
- Muitos para Muitos (N:N): Uma ou mais instâncias de uma entidade podem ou devem se relacionar com uma ou mais instâncias de outra entidade.

Na imagem acima podemos ver o número 1 no cliente e a letra N perto do produto. Isso significa que a cardinalidade é de um para muitos. Um cliente compra um ou mais produtos.

### Categorias nas Entidades (1:N)

- "Fortes": para entidades do lado 1 da relação; e
- "Fracas": para entidades do lado N.

Entidade fraca significa que ela só existe porque outra entidade forte a sustenta.

No exemplo da imagem, o cliente é a entidade fraca, pois, se não houvesse o produto, ele não existiria.

Saber a força das entidades nos ajudará mais para frente, quando formos montar a modelagem lógica.

**Alguns exemplos de formas em modelagem de banco de dados:**

![formas-em-modelagem-de-BD](https://user-images.githubusercontent.com/97858145/189020848-82678401-4ae7-4d15-80da-4c56ba2471d4.png)

## Modelagem Lógica

Aqui, são adicionados ao nosso MER os atributos e chaves, constituindo o DER (Diagrama Entidade Relacionamento).

O DER dá uma visão mais detalhada do banco de dados, contendo as entidades, atributos e relacionamentos entre elas (em forma de tabelas).

### Chaves em Banco de Dados

Já falei um pouco sobre chaves em banco de dados em outro [artigo](https://github.com/andersonr-o/Banco-de-Dados-SQL/tree/Chaves-em-SQL), mas irei aprofundar aqui.

As marcações para chaves podem ser: primária simples, primária composta, estrangeira e candidata.

Chave é quando uma coluna de uma tabela identifica de maneira exclusiva essa tabela.

- Chave Única: identifica uma única linha de uma tabela;
- Chave não Única: identifica um conjunto de linhas de uma tabela.

Tipos de chaves únicas: candidata, composta, primária, surrogada (substituta) e alternativa.

Tipos de chaves não únicas: estrangeira.

#### Candidata

Atributo ou grupo de atributos com potencial para se tornarem chave primária. Uma chave candidata que não é uma chave primária é chamada de alternativa.

Exemplo: o número de matrícula e o CPF podem ser chaves primárias, mas só uma será a chave primária, e a outra será uma chave alternativa.

#### Chave Primária (PK)

Uma chave primária identifica de forma exclusiva os registros de uma tabela, não podendo haver repetição de valores e nem valor nulo (vazio) neste campo.

No DER, podemos indicar uma PK por #nomeChave ou sublinhar o nomeChave.

#### Chave Estrangeira (FK)

É uma coluna de uma tabela que referencia a chave primária de uma outra tabela.

Por exemplo: há duas tabelas, uma de venda e outra de produto, e eu quero colocar na tabela de venda qual produto está sendo vendido.

Em vez de escrever o produto toda vez que for fazer uma venda, eu só passo o código dele através de uma chave estrangeira e faço essa relação com a tabela de produto.

Agora, na tabela de vendas eu também sei qual produto que foi vendido.

#### Chave Composta

É quando eu não consigo definir uma chave primária, porque não há nenhuma coluna em que os valores não se repitam, então uso a chave composta.

Ela basicamente nos diz que um conjunto de colunas está sendo referenciado, portanto esses valores, em conjunto, não podem ser repetidos.

Número de agência e conta de banco, por exemplo. Cada conta é individual, mas outros clientes que abriram conta naquela agência possui o mesmo número de agência que eu. Mas eles nunca terão a minha agência E a minha conta, pois isso é exclusivo meu.

Eles também podem ter a mesma conta, mas em uma agência diferente. Percebe como os dois não se repetem juntos? Mas um ou outro pode se repetir em outro cliente.

#### Chave Surrogada

É um valor numérico, único, adicionado a uma relação para servir como chave primária, quando nenhuma candidata aparecer.

Ela não possui significado para os usuários, pois geralmente nem aparece nas aplicações.

São bastante usadas no lugar de uma chave primária composta, para simplificação de relacionamentos.

### Para criar PK e FK

É importante saber que:

- Não é possível haver valores duplicados em uma chave primária;
- Não é recomendado alterar valores de chaves primárias;
- Chaves estrangeiras são baseadas em valores de dados, classificados como ponteiros lógicos;
- O valor de uma chave estrangeira deve corresponder ao valor de sua chave primária associada ou valor de chave única. Caso contrário, deve ser nulo;

### Diferenças do MER e do DER

![MERvsDER](https://user-images.githubusercontent.com/97858145/189194596-9d034e9b-33b1-4c72-a4c2-efa444b61683.png)

Visualmente, podemos ver que o DER é uma representação mais elaborada, pois contém tudo o que o MER possui e ainda tem os atributos de cada entidade na forma de tabela.

## Modelagem Física

Na modelagem física, a única coisa que é incrementado ao DER são os tipos de dados.

Tenho um artigo sobre os [tipos de dados](https://github.com/andersonr-o/Banco-de-Dados-SQL/tree/Tipos-de-Dados), portanto irei focar em outras partes aqui.

### Natureza dos Scripts

Há algumas categorias de comandos no SQL (Structured Query Language), como:

#### Data Definition Language (DDL) &rightarrow; Refere-se à estrutura;

Alguns comandos DDL:

- ALTER: É usado para modificar a definição das entidades existentes;

    ALTER TABLE para adicionar uma nova coluna à tabela. Mais sobre como alterar tabelas [aqui](https://github.com/andersonr-o/Banco-de-Dados-SQL/tree/Alterando-Tabelas);

    ALTER DATABASE para definir as opções do banco de dados;

- CREATE: Usado para definir novas entidades;

    CREATE TABLE adiciona uma nova tabela no banco de dados. Já vimos como no artigo [Criando Tabelas](https://github.com/andersonr-o/Banco-de-Dados-SQL/tree/Criando-Tabelas);

    Exemplo de criação de tabela:

    ![create-table-example](https://user-images.githubusercontent.com/97858145/189204394-9153fe4e-678f-420e-8a30-29b4d9fe7db7.png)

- DROP: O comando DROP remove entidades existentes;

    DROP TABLE é o comando para remover uma tabela do banco de dados;

- DISABLE TRIGGER: Desabilita uma trigger DML, DDL ou de logon;

- ENABLE TRIGGER: Habilita uma trigger DML, DDL ou de logon;

- TRUNCATE TABLE: Remove todas as linhas de uma tabela;

- UPDATE STATISTICS: Atualiza estatísticas de otimização de consulta de uma tabela ou view indexada;


#### Data Manipulation Language &rightarrow; Refere-se à entrada e saída de dados;

Alguns comandos DML:

- INSERT: Instrução utilizada para **inserir dados**  a uma ou mais tabelas do banco de dados;

- UPDATE: Instrução utilizada para **atualizar dados**  a uma ou mais tabelas do banco de dados;

- DELETE: Instrução utilizada para **excluir dados**  a uma ou mais tabelas do banco de dados;

- MERGE: Realiza operações de inserção, atualização ou exclusão em uma tabela de destino com base nos resultados da junção com a tabela de origem;

- BULK INSET: Importa um arquivo de dados em uma tabela ou exibição do banco de dados em um formato especificado pelo usuário.

#### Data Query Language (DQL) &rightarrow; Refere-se à consulta dos dados;

Alguns comandos DQL:

- SELECT: Especifica as colunas da(s) tabela(s) de origem ou visualizações que deseja retornar como resultado da consulta;

    FROM especifica o nome da tabela que contém a coluna requerida pelo comando SELECT;

    WHERE especifica a condição que filtra os registros retornados das colunas declaradas na cláusula SELECT.

#### Transactional Control Language &rightarrow; Controla a sequência de execução de comandos;

Alguns comandos TCL:

- COMMIT: Usado para salvar permanentemente qualquer transação no banco de dados;

- ROLLBACK: Restaura o banco de dados para o último estado commited.

#### Data Control Language &rightarrow; Controla o acesso aos dados do banco.

Alguns comandos DCL:

- GRANT: Atribui privilégios de acesso do usuário a objetos do banco de dados;

- REVOKE: Remove os privilégios de acesso aos objetos obtidos com o comando GRANT;

- DENY: É usado para impedir explicitamente que um usuário receba uma permissão específica.

## Modelagem Conceitual x Lógica x Física

A modelagem e diagramas agora apresentados são evoluções de um mesmo banco de dados, onde a situação é a seguinte:

![ex-bd](https://user-images.githubusercontent.com/97858145/189206975-2e6c616c-0b5d-4c20-adbc-db944f20c09d.png)

Três imagens diferentes, com os tipos de modelagem:

### Modelagem Conceitual:

![MC-example](https://user-images.githubusercontent.com/97858145/189205886-a204d863-c7cf-4f2b-856e-c763222f7332.png)

### Modelagem Lógica:

![ML-example](https://user-images.githubusercontent.com/97858145/189206249-7928dc2f-5703-4e8d-a316-dfc9f3e6cf9b.png)

### Modelagem Física:

![MF-example](https://user-images.githubusercontent.com/97858145/189206300-b8d4578c-ad5e-4605-943c-db31c928c079.png)

**Poderíamos incluir os relacionamentos na modelagem lógica e física também. Não o fiz para a melhor visualização do diagrama.
