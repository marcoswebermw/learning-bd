## Sintaxe de padrões
  
Combinando os nós com os relacionamentos obteremos os padrões. Os padrões podem ser atribuídos à variáveis para serem reutilizados.  
  
Dentros dos padrões podem ser formados vários caminhos(`paths`) entre os nós através dos relacionamentos.  
  
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
  
