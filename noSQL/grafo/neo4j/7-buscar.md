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