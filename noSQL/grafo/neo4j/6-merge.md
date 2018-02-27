## Usando Merge
  
O merge server para inserir novos nós e relacionamentos, ou modificá-los caso existam.  
  
É mais lento do que usar o `CREATE` pois a cada chamada antes de inserir ele verifica se o nó já existe.  
  
Ele também tem a operação `ON CREATE SET` que pode ser usada para atualizar o nó ou relacionamento com novas propriedades.  
  
### Formas de usar o Merge
  
```sql
MERGE (wade:Jogador {nome:"Dwyane Wade"})
RETURN wade
```
  
```sql
MERGE (durant:Jogador {nome:"Kevin Durant"})
ON CREATE SET durant.altura=2.06
RETURN durant
```
  
```sql
MATCH (wade {nome:"Dwyane Wade"})
MATCH (miame {nome:"Miame Heat"})
MERGE (miame)<-[:JOGOU]-(wade)
RETURN miame, wade
```