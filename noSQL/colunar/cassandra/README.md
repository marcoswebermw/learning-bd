## Apache Cassandra

O Cassandra é um banco `colunar`, usa `tabela`, não tem esquema(`schemaless` - porém pode ser usado com esquema).  
  
Os bancos colunares são os bancos nosql que se parecem mais com os relacionais por causa da tabela, mas tirando isto, internamente são completamente diferentes.  
  
O Cassandra foi criado pelo Facebook e foi baseado no banco de dados BigTable do Google.  
  
O BigTable, consequentemente, o Cassandra, trabalham como sistemas distribuídos. São vários servidores coordenados suportando `grandes volumes de dados` com `alta disponibilidade`.   
  
Agora é `opensource` e gerenciado pelo projeto Apache.  Ele é feito em `Java`.  
  
Geralmente é usado por grandes empresas que tem dados na casa dos gigabytes e até petabytes.  
  
`Não aceita join`.  
   
Bancos colunares tem o mesmo problema de bancos de documentos e chave valor: `N+1 queries` e `desnormalização dos dados`.  
A desnormalização é boa prática em bancos colunares.  
   
O Cassandra tem a operação `upsert`. Durante a inserção, se já existir um registro com mesma chave primária, esse será substituido pelos novos valores. Caso contrário, será criado.  
  
  
### Algumas características
  
* Disponibilidade;  
* Performance;  
* Tolerância a falhas;  
* Escalabilidade;  
  

### Comparação com o modelo relacional
  
* No Cassandra temos o `Keyspace` que equivale no relacional ao nosso `banco de dados`.  
* As `Column Families(CF)` são às `tabelas`.  
* As `Chaves primárias` equivalem às `Row key`.  
* O `nome da coluna` equivale à `Column name/key`.  
* O `valor da coluna` equivale à `Column value`.  
* O Cassandra tem um linguagem de manipulação chamada `Cassandra Query Language(CQL)` que pode ser acessada pelo comando `cqlsh`.  
  
  
### Referências
  
* [Cassandra](http://cassandra.apache.org/);  
* [Wikipedia](https://pt.wikipedia.org/wiki/Apache_Cassandra);  