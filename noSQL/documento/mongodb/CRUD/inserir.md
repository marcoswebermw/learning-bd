## Inserir Documentos


### Inserir, ou criar e inserir documento JSON na colecão
  
Se não existir a coleção, ela é criada e o documento inserido.  
Se a coleção existir, apenas insere o documento.  

`db.novaColecao.insert( {nome:"Fulano", idade: 30} );`  

`db.novaColecao.insert( {nome:"Beltrano", idade: 20, sexo: "Masculino"} );`  
`db.novaColecao.insert( {nome:"Silcranoooo", idade: 18} );`  

`db.novaColecao.insert( {nome:"Fulaninha", dataNascimento: new Date(1986, 0, 30)} );` 

`db.novaColecao.insert( [ {nome:"John Doe"}, {nome:"Mary Doe"} ] );`    
  
### Inserir ou atualizar um documento JSON (Funciona parecido com o insert) 
  
`db.novaColecao.save( {'_id' : ObjectId('59f4bcfa1495c0d6281d65f1'), nome: 'Sicrano', idade: 18'} );`  

Com o `save` é criado um novo documento ou é substituído o documento inteiro.  

O comando `update` tem a opção `$set` que permite alterar apenas alguns campos do documento.  