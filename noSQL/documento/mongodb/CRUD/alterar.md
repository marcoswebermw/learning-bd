## Alterar documentos

### Atualizar documento inteiro(Não recomendado)
  
Este método é desencorajado pois algum erro e o documento pode ser perdido. Nele primeiramente é passado o objeto a ser alterado, e depois o documento inteiro com as alterações.  

> Prefira nunca atualizar um documento por inteiro.  

`db.novaColecao.update( {nome:"Fulaninha"}, {nome:"Fulana", idade:18} );` 

### Atualizar determinados campos no documento com `$set`.
    
Atualiza somente os campos indicados pelo `$set`.  

`db.novaColecao.update( {nome:"Fulana"}, {$set: {idade: 20}} );`  
  
> Um campo pode ser limpo ser for passado o valor `null` para ele.    
  
### Atulizar usando o `updateOne` no lugar do `update`
  
O `updateOne` vai garantir que somente um documento será alterado diminuindo os riscos durante a alteração.  

Sempre use o `updateOne` em detrimento do `update`.
  
`db.novaColecao.updateOne( {nome:"Fulana"}, {$set: {idade: 20}} );`  
  
### Adicionando novos campos com update
  
O `$set` poderia ser usado também para adicionar novos campos.  
Se o campo não existir atualiza o documento criando o campo.  

`db.novaColecao.updateOne( {nome:"Fulana"}, {$set: {idade: 20, sexo: "Feminino"} } );`  
  
### Removendo campos desnecessários com `$unset`

O `$unset` serve para remover campos que não são mais necessários. 

E isso pode ser feito durante a atualização do documento.  

O valor a ser removido pelo `$unset` tem que receber valor `true`.  
  
`db.novaColecao.updateOne( {nome:"Fulana"}, {$unset: {corDoCabelo: true}} );`  
  
