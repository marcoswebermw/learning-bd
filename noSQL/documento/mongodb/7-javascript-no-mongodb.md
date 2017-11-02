## Usando Javascript no MongoDB
  
Dentro do mongo podemos usar o Javascript para aumentar o número de possibilidades 
do que podemos fazer com os dados dentro dele.  
Podem ser usadas instruções condicionais ou loops.  
O objeto `db` atua como se fosse o `window` dos navegadores.  
Vejamos o que é possível fazer.  
  
### Criando banco e inserindo valores
  
`show dbs;`  
`use cinema;`
`db;`

`db.createCollection('artista');`
`show collections;`

`db.artista.insert({nome:'Carrie-Anne Moss', nascimento:new Date(1967,7,21)});`
`db.artista.insert({nome:'Charlize Theron', nascimento:new Date(1975,7,7)});`
`db.artista.insert({nome:'Adrianne Palicki', nascimento:new Date(1983,4,6)});`

`db.artista.count();`

### Usando Javascript
  
```js
let carrie = db.artista.findOne({nome:'Carrie-Anne Moss'});
print(carrie['nome']);        // Carrie-Anne Moss.
print(carrie['nascimento']);  // Mon Aug 21 1967 00:00:00 GMT+0000 (UTC)
```
