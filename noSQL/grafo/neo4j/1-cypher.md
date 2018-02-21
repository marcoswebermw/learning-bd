## Cypher
  
Cypher é a linguagem de consulta textual e declarativa que surgiu nas últimas versões do Neo4j.  
  
Assim como outras com o mesmo propósito, se parece muito com o sql.  
  
Nela os `Nós/Node` represetam os elementos, entidades, conceitos, eventos, etc.  
  
Os `relacionamentos` servem para unir os Nodes. Um relacionamento pode ter ou não um sentido que aponta para um nó.    
  
Tanto os nós como os relacionamentos além do nome podem ter também propriedades e rótulos(labels).  

Cypher é baseada em padrões. Humanos são bons trabalhando com padrões.  

Fica fácil transformar padrões em diagramas para serem reconhecidos mais facilmente por humanos.  

Padrões complexos podem ser formados com grafos à partir da junção de vários relacionamentos entre os nós.  
  
### Sintaxe de um Nó
  
Na Cypher os nós são representados através de parênteses `()`. E normalmentes tem uma string dentro deles `(uma_string)` que representa um label para o nó.  
  
Formas de declarar um Nó.
  
* `()` - Representa um nó anônimo e descaracterizado.  
* `(uma_variavel)` - Representa uma variável que pode ser referenciada em outra parte da sentença(tem que ser a mesma sentença).  
* `(:SOU_UM_TIPO)` - A palavra `SOU_UM_TIPO` depois dos `:` representa o tipo da informação.  
* `{propriedade_1 : "Minha propriedade", propriedade_2 : 2018}` - Dentro de colchetes estão as propriedades que contém informações do tipo chave/valor.  
  
Exemplos da Documentação
  
```sql
()
(matrix)
(:Filme)
(matrix:Filme)
(matrix:Filme {titulo: "The Matrix"})
(matrix:Filme {titulo: "The Matrix", lancado: 1997})
```
  
### Sintaxe de um relacionamento
  
A sintaxe de um relacionamento é parecida com a sintaxe de um nó. A diferença é que ao invés de usar o par de parênteses, é usados o para de colchetes.  

Relacionamentos sem direção são representados por um par de traços `--`.  

Relacionamentos com direção são representados por `<-` ou por `->` indicando o sentido da relação.   
  
  
Formas de declarar um Relacionamento.
  
* `[]` - Representa um relacionamento sem nome.  
* `[uma_variavel]` - Representa uma variável que pode ser usada para referenciar o relacionamento em outro lugar(tem que ser a mesma sentença).  
* `[ :SOU_UM_TIPO_DO_RELACIONAMENTO]` - A palavra `SOU_UM_TIPO_DO_RELACIONAMENTO` depois dos `:` representa o tipo do relacionamento.  
* `{propriedade_1 : "Minha propriedade", propriedade_2 : 2018}` - Dentro de colchetes estão as propriedades que contém informações do tipo chave/valor.  
    
  
Exemplos da Documentação
  
```sql
-->
-[funcao]->
-[:ATUOU_EM]->
-[funcao:ATUOU_EM]->
-[funcao:ATUOU_EM {papeis: ["Neo"]}]->
```    
  
> Arrays também podem ser passados como valores de propriedades.  
  
  
### Sintaxe de padrões
  
Combinando os nós com os relacionamentos obteremos os padrões. Os padrões podem ser atribuídos à variáveis para serem reutilizados.  
  
Exemplos da Documentação
  
* Nós e relacionamentos combinados  
  
```sql
(keanu:Pessoa:Ator {nome: "Keanu Reeves"}) -[funcao:ATUOU_EM {papeis: ["Neo"]} ]-> (matrix:Filme {titulo: "The Matrix"} )
```  
  
* Variáveis  
  
```sql
atuou_em = ( :Pessoa )-[ :ATUOU_EM ]->( :Filme )
```
  
### Referências bibliográficas

[Neo4j Get Started](https://neo4j.com/docs/developer-manual/current/get-started/cypher/)  
  
