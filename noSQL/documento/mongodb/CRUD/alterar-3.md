## Operadores do Update


### Incrementar o valor de um campo com `$inc`
  
O `$inc` incrementa um campo de um documento com um determinado valor.  

Esse valor pode ser tanto positivo quanto negativo.  

Se o campo não existe, será criado e o valor dele será o do incremento.  

Não use o `$inc` com valores `null` pois ocorrerão erros.  
  
`db.novaColecao.updateOne( {nome:'Fulana'}, { $inc: {idade: 1, salario:-200} } );`  

> No exemplo acima se 'Fulana' tiver 30 anos sua idade passa a ser 31. E seu sálario diminuiu em 200 reais.  
    
### Multiplicar o valor de um campo com `$mul`
  
O `$mul` surgiu a partir da versão 2.6 e ele serve para multiplicar o valor de um campo por um número.  

Se o campo não existir, ele será criado e terá valor zero do mesmo tipo do valor multiplicador.  
  
`db.novaColecao.updateOne( {nome:'Fulana'}, { $mul: { salario:2 } } );`  
  
> No exemplo acima o salário de 'Fulana' será dobrado.  
    
### Renomear o nome de um campo com `$rename`
  
O `$rename` altera o nome de um campo de apenas um documento.  

Se o campo não existir, nada acontecerá.  
  
`db.novaColecao.update( {nome: 'Fulana' }, { $rename: { 'salario':'remuneracao', 'idade': 'tempoDeVida' } } );`  

> No exemplo acima 'Fulana' terá o campo 'salario' mudado para 'remuneracao'. Também terá o campo 'idade' alterado para 'tempoDeVida'.  

Para alterar o nome de um campo em todos os documentos use `$rename` junto ao `updateMany()`.  
  
`db.novaColecao.updateMany( {}, { $rename: { 'salario':'remuneracao' } } );` 

### Existem mais operadores do `update`
  
Para descobrir mais operadores do `update` acesse a (documentação oficial)[https://docs.mongodb.com/manual/reference/operator/update/].  


