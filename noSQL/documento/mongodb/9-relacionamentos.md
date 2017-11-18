## Abordagens de relacionamento no MongoDB

Pode ser usada uma forma parecida com a usada no modelo relacional(mas não recomendada).  

Poderia ser usado o id de um documento em uma colecao como chave estrangeira de um documento em outra.  

O problema dessa abordagem é que conforme o número de tabelas aumenta, 
a complexidade para montar as junções "joins" fica cada vez maior.  

Existe também o problema chamado `n+1 query` onde o número de consultas no banco de dados 
é igual ao número de registros(`n`) mais `1`.  Isso acontece em todos os bancos de dados.  

> Lembrando que em bancos orientados a documentos não temos `joins`.  
  
Outra forma é com documentos embebidos(aninhados) dentro de outros.  
  
O ideal é misturar as duas abordagens. 
  

### Usando modelo relacional no Mongodb
  
Usando uma abordagem parecida com o relacional no mongodb teríamos uma abordagem 
semalhente a mostrada a seguir usada na criação das coleções e do acesso aos dados.  
Alguns campos foram recriados na coleção elenco para não precisar ir em outras coleções buscá-los 
evitando perda de performance. É bom evitar normalização em bancos orientados a documento por isso a duplicação.  
  
### Criando as coleções

```js

// Mostrando todos os bds, escolhendo ou criando bd, mostrando bd usado no momento.
show dbs;  
use cinema;
db;

// Criando coleções e as mostrando.
db.createCollection('filme');
db.createCollection('artista');
db.createCollection('elenco');
show collections;

// Inserindo filmes.
db.filme.insert( {nome:'The Matrix', ano:new Date(1999,4,21), minutosDuracao:136} );
db.filme.insert( {nome:'Mad Max: Fury Road', ano:new Date(2015,4,14), minutosDuracao:120} );
db.filme.insert( {nome:'John Wick',  ano:new Date(2014,10,27), minutosDuracao:101} );

//Inserindo atores e atrizes.
db.artista.insert( {nome:'Carrie-Anne Moss', nascimento:new Date(1967,7,21)} );
db.artista.insert( {nome:'Keanu Reeves', nascimento:new Date(1964,8,2)} );
db.artista.insert( {nome:'Laurence Fishburne', nascimento:new Date(1961,6,30)} );

db.artista.insert( {nome:'Charlize Theron', nascimento:new Date(1975,7,7)} );
db.artista.insert( {nome:'Tom Hardy', nascimento:new Date(1977,8,15)} );

db.artista.insert( {nome:'Adrianne Palicki', nascimento:new Date(1983,4,6)} );


db.artista.count();
db.filme.count();
db.elenco.count();
```  

### Criando as relações

```js
// Preenchendo o elenco.
// Usando Javascript em algumas operações.
let f = '';
let a = '';

// Inserindo elenco do filme The Matrix.
f = db.filme.findOne( {nome:'The Matrix'} );

a = db.artista.findOne({nome:'Carrie-Anne Moss'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );

a = db.artista.findOne({nome:'Keanu Reeves'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );

a = db.artista.findOne({nome:'Laurence Fishburne'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );

// Inserindo elenco do filme Mad Max: Fury Road.
f = db.filme.findOne( {nome:'Mad Max: Fury Road'} );

a = db.artista.findOne({nome:'Charlize Theron'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );

a = db.artista.findOne({nome:'Tom Hardy'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );

// Inserindo elenco do filme John Wick.
f = db.filme.findOne( {nome:'John Wick'} );

a = db.artista.findOne({nome:'Adrianne Palicki'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );

a = db.artista.findOne({nome:'Keanu Reeves'});
db.elenco.insert( { filme_nome: f.nome, filme_id: f._id, artista_nome: a.nome, artista_id: a._id} );


```

### Buscando os dados

```js

// Encontrando filmes que tem o Keanu Reeves.
let keanu = db.elenco.find( {artista_nome:"Keanu Reeves"} ).pretty();

keanu[0].filme_id;
keanu[0].filme_nome;

keanu[1].filme_id;
keanu[1].filme_nome;


// Encontrando artistas que trabalharam no filme madmax.
let mad_max_elenco = db.elenco.find( {filme_nome:"Mad Max: Fury Road"} ).pretty();

mad_max_elenco[0].artista_nome;
mad_max_elenco[1].artista_nome;


```  
