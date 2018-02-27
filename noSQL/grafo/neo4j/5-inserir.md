## Inserindo dados no banco
  
Para inserir dados no banco o Neo4j oferece a declaração `CREATE`.  
  
Através do uso dos padrões e com o `CREATE` podemos criar a estrutura do banco. Essa estrutura também é constituída pelo dado propriamente dito. 
  
Isso é diferente do modo que usamos no modelo relacional onde criamos as estruturas e, depois inserimos os dados. No modelo de grafos do Neo4j os elementos vão sendo inseridos com sua estrutura conforme a necessidade. 

O `CREATE` tem o problema de inserir um novo nó sem verificar se já existe um com as mesmas informações, ocasionando em nós repetidos.
  
### Usando o `CREATE`
  
```sql
// Criando um novo nó
CREATE (:Franquia { nome:"Boston Celtics", titulos:17 })
```

```sql
// Criando vários nós de uma vez, usando vários `CREATE`
CREATE (:Franquia { nome:"Los Angeles Lakers", titulos:16 })
CREATE (:Franquia { nome:"Chicago Bulls", titulos:6 })
```

```sql
// Criando vários nós com um `CREATE` usando vírgulas
CREATE (:Franquia { nome:"San Antonio Spurs", titulos:5 }),
       (:Franquia { nome:"Philadelphia 76ers", titulos:3 }),
       (:Franquia { nome:"Cleveland Cavaliers", titulos:1 })
```

```sql
// Criando e retornando um novo nó pela variável
CREATE (gsw:Franquia { nome:"Golden State Warriors", titulos:5 })
RETURN gsw
```

```sql
//Criando e retornando um novo nó com saída limitada
CREATE (pistons:Franquia { nome:"Detroit Pistons", titulos:3 })
RETURN pistons LIMIT 50
```
  
### Criando uma estrutura mais complexa
  
```sql
CREATE (lebrom: Jogador {nome: "Lebrom James"})
-[j:JOGOU {temporadas:["2010/2011","2011/2012","2012/2013","2013/2014"]}]
->(miame:Franquia {nome:"Miame Heat", titulos:3})
<-[t:TREINOU]-(spoelstra:Treinador {nome:"Erik Spoelstra"})
RETURN lebrom, j,miame, t
```
  
```sql
MATCH (lebrom:Jogador {nome:"Lebrom James"})
CREATE(cleveland:Franquia {nome:"Cleveland Cavaliers", titulos:1})<-[j:JOGOU]-(lebrom)
RETURN lebrom, cleveland
```


* Criando um novo nó e definido propriedades com o `SET`
  
```sql

```
