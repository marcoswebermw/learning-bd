## Collections - Conjuntos
  
O Cassandra também permite trabalharmos com conjuntos, listas e mapas.  
  
### Conjuntos - SET
  
São grupos de dados que são únicos, ou seja, não se repetem. 
  
São armazenados de forma desordenada. Mas são retornados ordenados, geralmente por ordem alfabética, não mantendo a ordem original de inserção.  
  
São bastante usados em relações `many-to-one`.  
  
* Criando novo Keyspace para o exemplo
  
```sql
CREATE KEYSPACE colecoes WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '3' };

DESCRIBE KEYSPACES;
```    

* Criando tabela e usando um campo do tipo conjunto
  
```sql
CREATE TABLE usuarios(
id_usuario TEXT PRIMARY KEY,
nome_usuario TEXT,
emails set<TEXT>
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

ALTER TABLE usuarios ADD emails set<text>;   
```  
  
* Inserindo dados nos conjuntos
  
```sql
INSERT INTO usuarios (id_usuario, nome_usuario, emails) 
VALUES ('1', 'stark', { 'stark@vingadores.com', 'tony_stark@stark.com' });

INSERT INTO usuarios (id_usuario, nome_usuario, emails) 
VALUES ('2', 'blackwidow', { 'blackwidow@vingadores.com', 'black_widow2000@gmail.com', 'scarllett_bw@outlook.com' });

INSERT INTO usuarios (id_usuario, nome_usuario, emails) 
VALUES ('3', 'capitao_america', { 'capitao_america@hotmail.com' });
```
  
* Atualizando conjunto
  
Se tentarmos inserir novos registros em um conjunto, o conjunto será sobrescrito. A forma correta é atualizarmos o conjunto somando(concatenar) os valores antigos com os novos.  
    
```sql
UPDATE usuarios SET
emails = emails + { 'capitao@primeirovingador.com' }
WHERE id_usuario = '3';
```
  
* Buscando informações de conjuntos
  
```sql
SELECT nome_usuario, emails FROM usuarios;

SELECT nome_usuario, emails FROM usuarios WHERE nome_usuario = 'blackwidow' ALLOW FILTERING;

CREATE INDEX ON usuarios(nome_usuario);

SELECT nome_usuario, emails FROM usuarios WHERE nome_usuario = 'blackwidow';

SELECT id_usuario, nome_usuario FROM usuarios WHERE emails  CONTAINS 'blackwidow@vingadores.com' ALLOW FILTERING;
```
  
* Removendo elemento de um conjunto
  
```sql
UPDATE usuarios SET
emails = emails - { 'capitao_america@hotmail.com' }
WHERE id_usuario = '3';
```
  
  
### Referências
  
[Datastax](https://docs.datastax.com/en/cql/3.3/cql/cql_using/useSet.html)  
[cassandraufg](https://cassandraufg.wordpress.com/category/modelo-de-dados/)  