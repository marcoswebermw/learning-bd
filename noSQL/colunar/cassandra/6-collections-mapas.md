## Collections - Mapas
  
Os mapas relacionam elementos através de um par de chave/valor.   
  
Somente existe um valor para uma chave. E a chave não pode ser duplicada.  
  
São muito usados como timestamp.  
  
Cada elemento de um mapa é armazenado internamente para uma coluna no Cassandra.  
  
Esses elementos podem ser consultados, modificados, substituídos e deletados.  
  
Cada elemento pode ter um tempo de vida que expira quando o TTL(time-to-live) termina.  
  
### Mapas
  

* Criando novo Keyspace para o exemplo
  
```sql
CREATE KEYSPACE colecoes WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '3' };

DESCRIBE KEYSPACES;
```    

* Criando tabela e usando um campo do tipo map
  
```sql
CREATE TABLE usuarios(
id_usuario TEXT PRIMARY KEY,
nome_usuario TEXT,
datas_de_login map<TIMESTAMP, TEXT>
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

ALTER TABLE usuarios ADD datas_de_login map<TIMESTAMP, TEXT>;   
```  
  
* Inserindo dados no mapa
  
```sql
INSERT INTO usuarios (id_usuario, nome_usuario, datas_de_login) 
VALUES ('1', 'stark', {'2018-01-20 23:45': 'Primeiro Acesso do Iron Man'});

INSERT INTO usuarios (id_usuario, nome_usuario, datas_de_login) 
VALUES ('2', 'blackwidow', {'2018-01-14 10:07': 'Acesso 1 da Viúva Negra', '2018-02-22 03:00': 'Acesso 2 da Viúva Negra'});

INSERT INTO usuarios (id_usuario, nome_usuario, datas_de_login) 
VALUES ('3', 'capitao_america', {'2018-03-30': 'O capitão acessou o sistema'});
```
  
* Atualizando mapa
  
Se tentarmos inserir novos registros em um mapa, ele será sobrescrito. A forma correta é atualizarmos um mapa somando(concatenar) os valores antigos com os novos.  
    
```sql
UPDATE usuarios SET
datas_de_login = datas_de_login + {'2018-05-07': 'O capitão acessou novamente'}
WHERE id_usuario = '3';

UPDATE usuarios SET
datas_de_login['2018-02-22 03:00'] = 'Essa mensagem foi alterada.'
WHERE id_usuario = '2';
```
  
* Buscando informações dos mapas
  
```sql
SELECT nome_usuario, datas_de_login FROM usuarios;

SELECT nome_usuario, datas_de_login FROM usuarios WHERE nome_usuario = 'blackwidow' ALLOW FILTERING;

CREATE INDEX ON usuarios(nome_usuario);

SELECT nome_usuario, datas_de_login FROM usuarios WHERE nome_usuario = 'blackwidow';

```
  
* Removendo elemento do mapa
  
```sql
DELETE datas_de_login['2018-05-07'] FROM usuarios 
WHERE id_usuario = '3';
```
  
* Usando TTL(Time-To-Live) em um campo
  
No exemplo abaixo o valor do campo `nome_usuario` será mudado para `Viuva Negra`, mas depois de 20 segundos esse valor expirará. Então, o valor passará a ser `null`.  

```sql
UPDATE usuarios USING TTL 20 SET nome_usuario = 'Viuva Negra' WHERE id_usuario = '2';

SELECT TTL (nome_usuario) from usuarios WHERE id_usuario = '2';
```
  
### Referências
  
[Datastax](https://docs.datastax.com/en/cql/3.3/cql/cql_using/useMap.html)  
[cassandraufg](https://cassandraufg.wordpress.com/category/modelo-de-dados/)  
[Datastax](https://docs.datastax.com/en/cql/3.3/cql/cql_using/useTTL.html)  

