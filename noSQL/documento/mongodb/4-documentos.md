## Documentos
  
Os documentos são como as linhas, registros ou tuplas de uma tabela relacional.  
  

### Inserir ou criar e inserir documento JSON na colecão
  
`db.novaColecao.insert( {nome:"Fulano", idade: 30} );`  
`db.novaColecao.insert( {nome:"Beltrano", idade: 20, sexo: "Masculino"} );`  
`db.novaColecao.insert( {nome:"Silcranoooo", idade: 18} );`  
`db.novaColecao.insert( {nome:"Fulaninha", dataNascimento: new Date(1986, 0, 30)} );` 
  
### Inserir ou atualizar um documento JSON (Funciona parecido com o insert) 
  
`db.novaColecao.save( {'_id' : ObjectId('59f4bcfa1495c0d6281d65f1'), nome: 'Sicrano', idade: 18'} );`  
> É criado um novo documento ou é substituído o documento inteiro. O comando `update` também 
tem a opção `$set` que permite alterar apenas alguns campos.  
  
### Update - Atualizar determinados campos no documento.
  
`db.novaColecao.update( {nome:"Fulaninha"}, {$set: {idade: 20, sexo: "Feminino"} } );`  
> Atualiza somente os campos indicados pelo `$set`.  Também poderia ser omitido o `$set` e 
ser alterado o documento inteiro como no `save`. O `$set` poderia ser usado também para adicionar 
novos campos.  
  
> Além do `$set` também existe o `$unset` que serve para remover campos que não são mais necessários. 
E isso pode ser feito durante a atualização do documento. O valor a ser removido pelo `$unset` tem 
que receber valor `true`.  
  
`db.novaColecao.update( {nome:"Fulaninha"}, {$unset: {corDoCabelo: true}} );`  
  
Por padrão e por questões de segurança o update somente altera um registro por vez.  
Para permitir que ele altere mais de um registro por vez é necessário passar também o 
argumento `{multi:true}` para o update.  
  
`db.novaColecao.update( {idade:70}, {$set: {idoso: true}}, {multi: true} );`  
    
### Mostrar todos os documentos de uma coleção
  
`db.novaColecao.find()`  
  
> Retorna uma lista vazia caso não exista documentos.  
  
### Mostrar todos os documentos de uma coleção em formato mais amigável
  
`db.novaColecao.find().pretty();`  
   
### Mostrar o primeiro documento da coleção
  
`db.novaColecao.findOne();`  
  
> Retorna `null` caso não exista documento.  
  
### Mostrar um documento da coleção de acordo com um filtro
  
`db.novaColecao.findOne( { nome : 'Beltrano' } );`  
`db.novaColecao.findOne( { idade : 20 } );`  
  
> As chaves `{}` para definir os filtros são chamadas no mongodb de `criteria`.  
  
### Indica a quantidade de registros(documentos) na coleção
  
`db.novaColecao.count();`  
  
> O `count()` também retorna a quantidade de registro que satisfazem uma busca assim como 
o count do sql.  
  
`db.novaColecao.count( {nome: 'Fulano'} );`
  
### Remove um documento de acordo com um ou mais filtros
  
`db.novaColecao.remove( { nome : 'Beltrano' } );`  
`db.novaColecao.remove( { idade : 20, sexo : 'Masculino' } );`  
  
### Removendo todos os documentos de uma coleção
  
`db.novaColecao.remove( {} );`  

