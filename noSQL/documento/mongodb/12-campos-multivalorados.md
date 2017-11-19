## Campos multivalorados
  
São campos que recebem mais de um valor através de um array usando colchetes. Dentre esses valores também podemos ter outros objetos(documentos).  
  
Os valores possíveis são o `null` ou um `array` com colchetes `[]`.

### Inserir
  
`db.novaColecao.insert( {nome: "Fulano", filhos: ["Sicrano", "Beltrana"] } );`  

`db.novaColecao.insert( {nome: "Sicrano", filhos: null} );`  

`db.novaColecao.insert( {nome: "Beltrana", filhos: [ {nome:"John Doe", idade: 10} ] } );`  
      
`db.novaColecao.insert( {nome: "John Doe", endereco:{ cidade: "Roma" } });`  
  

### Alterar adicionando com `$push`
  
`db.novaColecao.updateOne( {nome:"Fulano"}, {$push: {filhos: "Sicraninha"}} );`    
  

### Alterar removendo com `$pull`
  
`db.novaColecao.updateOne( {nome:"Fulano"}, {$pull: {filhos: "Sicraninha"}} );`    
  

### Buscar com o operador `$all`
    
Serão retornados somente os elementos que contenham `todos` os parâmetros do filtro.
  
`db.novaColecao.find( {filhos: {$all: ["Sicrano","Beltrana"] } );`  
  
Irá retornar `Fulano`.
  

### Buscar com o operador `$in`
  
Serão retornados os elementos que tenham pelo menos um dos parâmetros passados pelo filtro.  

`db.novaColecao.find( {filhos: {$in: ["Sicrano", "John Doe"] }} );`  
     
Irá retornar `Fulano` e `Beltrana`.     
  

### Buscar em subdocumentos
    
`db.novaColecao.find( {endereco: {cidade:"Roma"} } );`  
  
Irá retornar `John Doe` pois é o único que tem um endereço(subdocmento) com cidade com nome `Roma`.  
  

### Remover
  
`db.novaColecao.deleteOne( {filhos: {$in: ["John Doe"] }} );`    
  
Remove `Beltrana` que é a mãe de `John Doe`.  
  


