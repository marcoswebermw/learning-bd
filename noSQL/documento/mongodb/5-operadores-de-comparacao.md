## Operadores de comparação
  
É possível usar operadores de comparação para melhorar nossas buscas dentro do mongodb.  
  
### Maior que ($gt)
  
`db.novaColecao.find( {idade: { "$gt" : 18} } );`  
  
### Maior igual ($gte)
  
`db.novaColecao.find( {idade: { "$gte" : 18} } );`  
  
### Menor que ($lt)
  
`db.novaColecao.find( {idade: { "$lt" : 18} } );`  
  
### Menor igual ($lte)
  
`db.novaColecao.find( {idade: { "$lte" : 18} } );`  
    
### ($eq - equal) Encontra todos os documentos com o valor do campo igual
  
`db.novaColecao.find( {idade: { $eq: 15 } } ).pretty();`  
> Funciona à partir da versão 3.0. Equivale a `{idade: 15}`.
  
### ($ne - not equal) Encontra todos os elementos diferentes do valor passado na query
  
`db.novaColecao.find( {idade: { $ne: 15 } } );`  
> Retorna todos os documentos cuja idade é diferente de 15, inclusive os documentos que não tem esse campo.
`db.novaColecao.find( {idade: { $ne: null } } ).pretty()`  
> Retorna todos os documentos cuja idade é diferente de null.
  
### ($in) Encontra todos os elementos de um campo à partir de um array
  
`db.novaColecao.find( {idade: { $in: [15, 18] } } );`  
> Retorna todos os documentos com idade que sejam 15 ou 18.  
  
### ($nin - not in) Encontra todos os documentos onde o campo em questão não contém os valores do array 
  
`db.novaColecao.find( {idade: { $nin: [18] } } ).pretty();`  
> Serão retornados inclusive os documentos que não tem o campo idade(valor null).  
  