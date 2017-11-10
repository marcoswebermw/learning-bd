## MongoDB
  
MongoDB é um banco open source orientado a documento.  
Os seus dados são armazenados no formato `BSON` parecido com o `JSON`.  
Suas consultas são feitas em JavaScript.  
É case sensitive.  
  
### Documentos  
  
Documentos são armazenados em `coleções`, e não tabelas.  
Os `documentos` são como uma `linha` ou `tupla` no modelo relacional.  
Ao invés de colunas os documentos tem `campos`.  
Também possuem `índices` como no modelo relacional.  
Joins são substituídos por documentos aninhados e vinculados.  
A chave primária é definida automaticamente no campo `_id` em todos documentos.  
Não existe `esquema` em sgbds baseados em documentos.  Ou seja, 
Cada documento pode ter qualquer campo, ou não.  
E a agregação é feita por pipeline.  
  
Bancos orientados a documento evitam a normalização pois podem perder performance. 
Então, é frequente o uso de dados duplicados.  

### Vantagens
  
Sem esquema o que o torna bastante flexível.  
Fácil uso o que permite uma curva de aprendizado baixa.  
Preparado para trabalhar com grandes quantidades de dados.  
  
### Desvantagens
  
Tem muita redundância gastando mais espaço de disco pois campos podem ser repetidos em vários documentos para aumentar a performance.  

Não tem a flexibilidade das joins em consultas(Apesar das joins prejudicarem a performance das consultas).  

Não tem transações fazendo com que ele não tenha rollbacks.  

### Quando é usado
  
* Big Data;
* Quando há muitas operações de escrita;
* Busca simples, porém pesadas;
* Alta escala;
* Alta disponibilidade;
* Quando o schema é instável, ou seja, pode variar em cada documento.
  
