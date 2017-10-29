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
  
