## Buscando informações
  
Para buscar alguma informação fazemos uso combinado das clausulas `MATCH` e `RETURN`.  
  
O `MATCH` faz a correspondência do nó que estamos buscando com algum elemento no banco. Seria como uma espécie de `WHERE` do modelo relacional.  
  
O `RETURN` funciona de forma parecida com o `select` dos bancos relacionais tradicionais. Ou seja, indica os nós que queremos retornar.  
  
Quando o `MATCH` faz a correspondência e encontra algum nó no banco, esse nó pode ser retornado pelo `RETURN`.  
  
> O `MATCH` não pode ser usado sozinho. Se for usado deverá ser seguido de algo como um `RETURN` ou `UPDATE`.  
  
> O `RETURN` só retorna o que for encontrado no `MATCH`.  
  
### Formas de se fazer buscas
  
```sql
// Retornando todos os nós.
MATCH (f)
RETURN f
```
  
```sql
// Retornando todos os nós de determinado tipo.
MATCH (f:Franquia)
RETURN f
```
  
```sql
// Buscando por um nó específico sem passar o tipo.
MATCH (lebrom {nome:"Lebrom James"})
RETURN lebrom
```
  
```sql
// Buscando por nó específico passando seu tipo.
MATCH (lebrom:Jogador {nome:"Lebrom James"})
RETURN lebrom
```
  
### Busca mais complexa
  
```sql
// Mostra o nome das franquias que Lebrom jogou.
// E mostra quais temporadas ele jogou lá.

MATCH (lebrom:Jogador {nome:"Lebrom James"})-[j:JOGOU]->(franquias:Franquia)
RETURN franquias.nome, j.temporadas
```
  
### Usando Alias(Apelidos)
  
Para usarmos apelidos para resultados usamos o `AS`.  
  
```sql
// Retornando todos os nós de determinado tipo.
MATCH (j:Jogador)
RETURN j AS JOGADOR;

// Retornando todos os nós de determinado tipo.
MATCH (f:Franquia)
RETURN f.nome AS Nome_Da_Franquia;
```

### WHERE
  
Até aqui para fazer a filtragem de elementos com o `MATCH` usamos os parâmetros dentro de chaves. Mas essa é apenas uma forma mais resumida de se usar o `WHERE`.  
  
O `WHERE` também pode ser usado e, dentro dele podemos usar expressões booleanas com operadores como: `=`, `>`, `<`, `>=`, `<=`, `NOT`, `AND`, `OR`, `XOR`, `IN`, `expressões regulares(=~)` e etc.
  
```sql
// Todos os times que começam com ´C´.
// Resultado: Cleveland e Chicago Bulls.
MATCH (f:Franquia)
WHERE f.nome =~ "C.+"
RETURN f AS Time
```
  
```sql
// Times com 5 à 9 títulos ordenados pelo nome.
// Resp: Chicago Bulls, Golden State Warriors, San Antonio Spurs.
MATCH (f:Franquia)
WHERE f.titulos > 4 AND f.titulos < 10
RETURN f AS Time ORDER BY f.nome
```
  
```sql
// Retorna o nó que tem nome `Boston Celtics`.
MATCH (f:Franquia)
WHERE "Boston Celtics" IN f.nome
RETURN f AS Time
```
