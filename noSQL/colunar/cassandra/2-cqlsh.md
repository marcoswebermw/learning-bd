### Usando o cqlsh para manipular dados (DML)

Podemos manipular os dados de forma parecida com os bancos relacionais.  
  
### Inserindo dados
  
```sql
INSERT INTO pessoas(id, nome, sobrenome) 
VALUES (12345678-1234-1234-1234-123456789012, 'Scarlet', 'Ingrid Johanson');  
  
INSERT INTO pessoas()
VALUES (12345678-1234-1234-1234-123456789012, 'Margot', 'Elise Robbie');  
```
  
### Criando indices
  
```sql
CREATE INDEX ON pessoas (nome);
```
  

### Buscando dados
  
O Cassandra não permite fazer buscas com `where` em campos que não possuem um `índice`, pois não são performáticas.  
  
```sql
SELECT * FROM pessoas;

SELECT * FROM pessoas WHERE nome = 'Margot';

SELECT * FROM pessoas WHERE nome = 'Margot' ALLOW FILTERING;
```   
  
> Para conseguir passar filtros para o where sem usar os índices, use a opção `ALLOW FILTERING`.  
  

### Atualizando dados
  
```sql
UPDATE pessoas SET
  nome='Scarlett',
  sobrenome='Ingrid Johansson'
WHERE id = 12345678-1234-1234-1234-123456789012;
```  
  
### Apagando dados
  
```sql
DELETE FROM pessoas
WHERE id = 12345678-1234-1234-1234-123456789012;
```  
  
  
### Referências
  
* [Wikipedia UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier);  
* [DML Cassandra](http://cassandra.apache.org/doc/latest/cql/dml.html);  
