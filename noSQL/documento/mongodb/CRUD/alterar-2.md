## Opções de parâmetros do Update

### Alterando vários registros de uma única vez com `{multi: true}`

Por padrão e por questões de segurança o update somente altera um registro por vez mesmo que o intuito seja outro.  

Para permitir que ele altere mais de um registro por vez é necessário passar também o terceiro parâmetro `{multi:true}` para o update.  
  
`db.novaColecao.update( {idade:70}, {$set: {idoso: true}}, {multi: true} );`  

> No exemplo acima serão alterados todos os documentos cujo valor da idade seja igual à 70.  

> Obs: Aqui acredito que tenha que ser o `update` mesmo. 
  
### Atualizando campo. Caso não exista será inserido com `{upsert: true}`
  
O `upsert`, assim como o `multi`, funciona como terceiro parâmetro do `update`, ou parâmetro de opções. Geralmente esses parâmetros são ocultados.  

O `upsert` vem de: `update + insert`. E significa que será feita uma alteração qualquer em um determinado campo de acordo com algum filtro. Mas se esse campo não existir será criado e o valor inserido.  
  
`db.novaColecao.updateOne( {nome:'Fulana'}, {$set:{sobrenome:'Silva'}}, {upsert:true} );`
  
> Muda o valor do sobrenome de ´Fulana´, se não existir esse campo, ele será criado e será inserido o valor ´Silva´.  
  
    
### Existem mais parâmetros do `update`
  
Para descobrir mais parâmetros do `update` acesse a (documentação oficial)[https://docs.mongodb.com/manual/reference/method/db.collection.update/index.html].  



