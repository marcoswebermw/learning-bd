## Usando o cqlsh na definição de dados (DDL)
  
O `cqlsh` é um prompt de comando para enviarmos comandos para o Cassandra através da linguagem `CQL`.  
  
Aparentemente os comandos do cqlsh não são case-sensitive.  
  
### Entrando no prompt
  
`cqlsh`  

### Listando keyspaces
   
`DESCRIBE KEYSPACES;`      
  
### Criando um novo keyspace
  
Um keyspace precisa de um nome e de uma estratégia de replicação.  
  
* SimpleStrategy - Não leva em consideração a topologia da rede. Os dados são replicados nos próximos servidores.  
* NetworkTopologyStrategy - Pode-se configurar réplicas por Rack, Data Center etc. Mais complexo.  
  
Geralmentes será usada a SimpleStrategy.  
Em produção para garantir a durabilidade e disponíbilidade usa-se o NetworkTopologyStrategy.    
  
`CREATE KEYSPACE meu_banco WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '3' };`  
  
`DESCRIBE KEYSPACES;`    
  
  
### Selecionando um keyspace  
   
`USE meu_banco;`  
  

### Mostrando todas as tabelas(column families) de um keyspace
   
`describe tables;`  
   

### Criando column family ou tabela
  
Temos que passar o nome da coluna, tipo, e qual será a row key(chave primária).  
  
```sql
CREATE TABLE pessoas(
    id uuid PRIMARY KEY,
    nome text,
    sobrenome text 
);

CREATE TABLE pessoas(
    nome text,
    sobrenome text,
    sexo text,
    PRIMARY KEY (nome, sobrenome) 
);
```   
  
> A tabela será criada com várias informações adicionais automaticamente.   
  
> O `uuid` é mostrado em 5 grupos separados por hifens, no formato 8-4-4-4-12 num total de 36 caracteres(32 alfanuméricos e 4 hifens).  
  
   

### Mostrando informações detalhadas de uma tabela  
   
`describe table pessoas;`  
  
  
### Alterando uma tabela

``      
   

### Apagando tabelas

`DROP TABLE pessoas;`  
    

### Referências
  
* [Wikipedia UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier);  
* [DDL Cassandra](http://cassandra.apache.org/doc/latest/cql/ddl.html#);  