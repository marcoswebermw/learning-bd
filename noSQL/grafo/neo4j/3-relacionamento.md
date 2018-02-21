## Sintaxe de um relacionamento
  
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
  
    
### Referências bibliográficas

[Neo4j Get Started](https://neo4j.com/docs/developer-manual/current/get-started/cypher/)  
  
