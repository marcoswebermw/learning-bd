## Collections (Coleções)

A coleções são equivalentes às tabelas no modelo relacional.  
  
 
### Mostrar todas as coleções do banco ativo
  
`show collections;`  
  
### Cria uma nova coleção no banco ativo
  
`db.createCollection('novaColecao');`  
  
### Exclui uma coleção do banco
  
`db.novaColecao.drop();`  
  
### Renomear uma coleção
  
`db.novaColecao.renameCollection('velhaColecao');`  
  
