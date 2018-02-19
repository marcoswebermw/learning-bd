## Collections - Listas
  
As listas podem ter valores repetidos(duplicados), e a ordem de retorno da lista é feita de acordo com um índice, geralmente é retornado na mesma ordem de inserção.  
  
É usado geralmente em relacionamentos `many-to-many`.  
  
### Listas
  

* Criando novo Keyspace para o exemplo
  
```sql
CREATE KEYSPACE colecoes WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '3' };

DESCRIBE KEYSPACES;
```    

* Criando tabela e usando um campo do tipo lista
  
```sql
CREATE TABLE usuarios(
id_usuario TEXT PRIMARY KEY,
nome_usuario TEXT,
emails list<TEXT>
);

DESCRIBE TABLES;

DESCRIBE TABLE usuarios;
```
  
Ou alterando a tabela:
  
```sql
CREATE TABLE usuarios(
id_usuario TEXT PRIMARY KEY,
nome_usuario TEXT,
);

ALTER TABLE usuarios ADD emails list<text>;   
```  
  
* Inserindo dados nas listas
  
```sql
INSERT INTO usuarios (id_usuario, nome_usuario, emails) 
VALUES ('1', 'stark', [ 'stark@vingadores.com', 'tony_stark@stark.com' ]);

INSERT INTO usuarios (id_usuario, nome_usuario, emails) 
VALUES ('2', 'blackwidow', [ 'blackwidow@vingadores.com', 'black_widow2000@gmail.com', 'scarllett_bw@outlook.com' ]);

INSERT INTO usuarios (id_usuario, nome_usuario, emails) 
VALUES ('3', 'capitao_america', [ 'capitao_america@hotmail.com' ]);
```
  
* Atualizando lista
  
Se tentarmos inserir novos registros em uma lista, a lista será sobrescrita. A forma correta é atualizarmos a lista somando(concatenar) os valores antigos com os novos.  
    
```sql
UPDATE usuarios SET
emails = emails + [ 'capitao@primeirovingador.com' ]
WHERE id_usuario = '3';
```
  
* Buscando informações de listas
  
```sql
SELECT nome_usuario, emails FROM usuarios;

SELECT nome_usuario, emails FROM usuarios WHERE nome_usuario = 'blackwidow' ALLOW FILTERING;

CREATE INDEX ON usuarios(nome_usuario);

SELECT nome_usuario, emails FROM usuarios WHERE nome_usuario = 'blackwidow';

SELECT id_usuario, nome_usuario FROM usuarios WHERE emails  CONTAINS 'blackwidow@vingadores.com' ALLOW FILTERING;
```
  
* Removendo coluna com conjunto
  
```sql
UPDATE usuarios SET
emails = emails - [ 'capitao_america@hotmail.com' ]
WHERE id_usuario = '3';
```
  
  
### Referências
  
[Datastax](https://docs.datastax.com/en/cql/3.3/cql/cql_using/useList.html)  
[cassandraufg](https://cassandraufg.wordpress.com/category/modelo-de-dados/)  