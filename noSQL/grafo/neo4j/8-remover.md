## Remover nós e relacionamentos
  
### Removendo um nó específico
  
```sql
MATCH (b {nome:"Boston Celtics"})
DELETE b
```
  
### Removendo todos os nós sem relacionamentos
  
```sql
MATCH (nos)
DELETE nos
```
  
### Removendo todos os nós com relacionamentos
  

Além dos nós, os relacionamentos envolvidos também serão removidos. Os nós sem relacionamentos vão continuar intactos.
  
```sql
MATCH nos_com_relacionamentos = ()-[]-() 
DELETE nos_com_relacionamentos
```
  
### Removendo propriedades de um nó
  
Para remover uma propriedade de um nó é só atribuir o valor `null` para ela através do `SET`.
  
```sql
// Criando a nova propriedade.
MATCH (d:Jogador {nome: "Kevin Durant"})
SET d.all_star = "SIM";
```
  
```sql
// Verificando a nova propriedade.
MATCH (d:Jogador {nome: "Kevin Durant"})
RETURN d;
```
  
```sql
// Removendo a propriedade
MATCH (d:Jogador {nome: "Kevin Durant"})
SET d.all_star = null;
```