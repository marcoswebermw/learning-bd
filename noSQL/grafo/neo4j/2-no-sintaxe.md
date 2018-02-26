## Sintaxe de um Nó
  
Na Cypher os nós são representados através de parênteses `()`. E normalmentes tem uma string dentro deles `(uma_string)` que representa um label para o nó.  
  
Formas de declarar um Nó.
  
* `()` - Representa um nó anônimo e descaracterizado.  
* `(uma_variavel)` - Representa uma variável que pode ser referenciada em outra parte da sentença(tem que ser a mesma sentença).  
* `(:SOU_UM_TIPO)` - A palavra `SOU_UM_TIPO` depois dos `:` representa o tipo da informação.  
* `{propriedade_1 : "Minha propriedade", propriedade_2 : 2018}` - Dentro das chaves estão as propriedades que contém informações do tipo chave/valor.  
  
Exemplos da Documentação
  
```sql
()
(matrix)
(:Filme)
(matrix:Filme)
(matrix:Filme {titulo: "The Matrix"})
(matrix:Filme {titulo: "The Matrix", lancado: 1997})
```
     
### Referências bibliográficas

[Neo4j Get Started](https://neo4j.com/docs/developer-manual/current/get-started/cypher/)  
  
