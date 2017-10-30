## Operadores lógicos
  
Aqui o operador lógico ficará na posição onde normalmente ficam as chaves.  
Os valores serão os critérios de busca. Eles ficam dentro de um array.   
  
### ($and)
  
```
   db.novaColecao.find(  {$and: [ 
                                 { idade: {$gte: 15} }, 
                                 { idade: {$lt:  18} }
                                 ] } );
```  
> Vai retornar os documentos cuja idade for maior e igual à 15 e menor do que 18.
  
### ($or)
  
```
   db.novaColecao.find( {$or: [
       {idade: {$lt: 15} },
       {idade: {$gte : 18} }
   ]} );
```  
> Vai retornar os documentos cuja idade forem menores que 15 ou maiores e igual a 18.  

### ($nor)
  
`db.novaColecao.find( {$nor: [{idade: 15}, {nome: "Beltrano"}] } );`  
> Não vai retornar os documentos com idade igual a 15 e nem os documentos com nome igual a Beltrano.  

### ($not)
  
`db.novaColecao.find( {idade: {$not: {$gte: 18} }} );`  
  
> Inverte a condição. Vai retornar os documentos com idade menor do que 18 e os nulos.  
  
  
