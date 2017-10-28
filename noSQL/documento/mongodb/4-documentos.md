## Documentos
  
Os documentos são como as linhas, registros ou tuplas de uma tabela relacional.  
  

### Inserir ou criar e inserir documento JSON na colecão
  
`db.novaColecao.insert( {nome:"Fulano", idade: 30} );`  
`db.novaColecao.insert( {nome:"Beltrano", idade: 20, sexo: "Masculino"} );`  
`db.novaColecao.insert( {nome:"Silcranoooo", idade: 18} );`  
  
### Inserir ou atualizar um documento JSON (Funciona parecido com o insert) 
  
`db.novaColecao.save( {'_id' : ObjectId('59f4bcfa1495c0d6281d65f1'), nome: 'Sicrano', idade: 18'} );`
  
### Mostrar todos os documentos de uma coleção
  
`db.novaColecao.find()`  
  
### Mostrar todos os documentos de uma coleção em formato mais amigável
  
`db.novaColecao.find().pretty();`  
   
### Mostrar o primeiro documento da coleção
  
`db.novaColecao.findOne();`  
  
### Mostrar um documento da coleção de acordo com um filtro
  
`db.novaColecao.findOne( { nome : 'Beltrano' } );`  
`db.novaColecao.findOne( { idade : 20 } );`  
  
### Indica a quantidade de registros(documentos) na coleção
  
`db.novaColecao.count();`  
  
### Remove um documento de acordo com um ou mais filtros
  
`db.novaColecao.remove( { nome : 'Beltrano' } );`  
`db.novaColecao.remove( { idade : 20, sexo : 'Masculino' } );`  
  

