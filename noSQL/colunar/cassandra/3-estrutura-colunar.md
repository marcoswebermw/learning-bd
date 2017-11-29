## Estruturas de dados do modelo colunar
  
No Cassandra temos estruturas diferentes do modelo relacional como as `wide rows` ou `dynamic columns`.  

Elas são `schemaless` não possuem colunas predefinidas. Não temos linhas nela e sim `partitions`.    
  
As partitions tem `partition key`(chave única). E cada partition key tem um valor associado(column/row ou chave/valor). A dupla chave/valor formam uma célula.  
  
Apesar de ainda parecer com o modelo relacional, internamente os dados estão armazenados orientados a colunas.  
  
### Criando tabelas com colunas dinâmicas
  
Regras para colunas dinâmicas:  
    
* É obrigatório ter 3 colunas(chave da partição, nome das colunas dinâmicas, valor da linha);  
* A chave primária deve ser composta por (chave da partição, nome da coluna).    
  
```sql
CREATE TABLE projeto (
    id uuid,
    versao int,
    processo text,
    PRIMARY KEY (id, versao)
) WITH COMPACT STORAGE;
```  
  
### Inserindo dados
  
```sql
INSERT INTO projeto (id, versao, processo) 
VALUES (12345678-1234-1234-1234-123456789012, 1, 'Criação');

INSERT INTO projeto (id, versao, processo) 
VALUES (12345678-1234-1234-1234-123456789012, 2, 'Elaboração');

INSERT INTO projeto (id, versao, processo) 
VALUES (12345678-1234-1234-1234-123456789012, 3, 'Monitoramento');

INSERT INTO projeto (id, versao, processo) 
VALUES (12345678-1234-1234-1234-123456789012, 4, 'Monitoramento');

INSERT INTO projeto (id, versao, processo) 
VALUES (12345678-1234-1234-1234-123456789012, 5, 'Encerramento');
```  
  
    
```
+-----------------------------------------------------------------+
| id                                   | versao | processo        |
+--------------------------------------+--------+-----------------+
| 12345678-1234-1234-1234-123456789012 |   1    | 'Criação'       |
| 12345678-1234-1234-1234-123456789012 |   2    | 'Elaboração'    |
| 12345678-1234-1234-1234-123456789012 |   3    | 'Monitoramento' |
| 12345678-1234-1234-1234-123456789012 |   4    | 'Monitoramento' |
| 12345678-1234-1234-1234-123456789012 |   5    | 'Encerramento'  |
+-----------------------------------------------------------------+
```   
  

### Buscando dados
  
`SELECT * FROM projeto;`  
  
