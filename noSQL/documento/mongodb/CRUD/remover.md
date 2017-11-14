## Remover documentos

Para remover documentos podem ser usados os métodos:  

* `delete()`;
* `deleteOne()`;
* `deleteMany()`;
* `remove()`.
  
Aparentemente o remove tem mais opções do que os outros, mas é menos usado.  

O `delete()` deve ser evitado porque é mais fácil cometer erros com ele.  
  

### Usando o `remove()`

**Remove um documento de acordo com um ou mais filtros**
  
`db.novaColecao.remove( { nome : 'Beltrano' } );`  

`db.novaColecao.remove( { idade : 20, sexo : 'Masculino' } );`  
  
**Removendo todos os documentos de uma coleção**
  
`db.novaColecao.remove( {} );`  
  
  
  
### Usando o `deleteOne()`

**Remove um documento de acordo com um ou mais filtros**
  
`db.novaColecao.deleteOne( { nome : 'Beltrano' } );`  

`db.novaColecao.deleteOne( { idade : 20, sexo : 'Masculino' } );`  
  
  

### Usando o `deleteMany()`

**Remove todos os documentos de acordo com um ou mais filtros**
  
`db.novaColecao.deleteMany( { nome : 'Beltrano' } );`  

`db.novaColecao.deleteMany( { idade : 20, sexo : 'Masculino' } );`  
  
> É retornado um documento com o status da operação.     
    
**Removendo todos os documentos**  
  
`db.novaColecao.deleteMany({})`  
  
> É retornado um documento com o status da operação.    
  



### Documentação

* (remove)[https://docs.mongodb.com/manual/reference/method/db.collection.remove/index.html];  

* (delete)[https://docs.mongodb.com/manual/tutorial/remove-documents/index.html]
