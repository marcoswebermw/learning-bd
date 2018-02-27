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