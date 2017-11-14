## Buscar documentos
  

    
### Buscar todos os documentos de uma coleção
  
`db.novaColecao.find()`  
  
> Retorna uma lista vazia caso não exista documentos.  
  
### Buscar todos os documentos de uma coleção em formato mais amigável
  
`db.novaColecao.find().pretty();`  
  
### Limitando a quantidade de documentos buscados 

`db.novaColecao.find().limit(5);`  
`db.novaColecao.find().limit(30);`  

### Ignorando alguns documentos de uma busca
  
> Ignorando o primeiro documento.  
`db.novaColecao.find().skip(1);`  
  
> Ignorando os 3 primeiros documentos.  
`db.novaColecao.find().skip(3);`  

> Ignorando o primeiro documento de 5 buscados.  
`db.novaColecao.find().skip(1).limit(5);`  

### Buscar o primeiro documento da coleção
  
`db.novaColecao.findOne();`  
  
> Retorna `null` caso não exista documento.  
  
### Buscar um documento da coleção de acordo com um filtro
  
`db.novaColecao.findOne( { nome : 'Beltrano' } );`  
`db.novaColecao.findOne( { idade : 20 } );`  
  
> As chaves `{}` para definir os filtros são chamadas no mongodb de `criteria`.  

> Pode ser usado expressão regular com as buscas no mongodb.  
`db.novaColecao.findOne( { nome : { $regex: /B/} } );`  

### Indica a quantidade de registros(documentos) na coleção
  
`db.novaColecao.count();`  
  
> O `count()` também retorna a quantidade de registro que satisfazem uma busca assim como 
o count do sql.  
  
`db.novaColecao.count( {nome: 'Fulano'} );`
  
