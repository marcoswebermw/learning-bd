## Dump e Restore no MongoDB

O mongo vem com utilitários de backup e restore dentro do seu diretório de instalação. Mais específicamente dentro do diretório `/bin` do mongo.  

Para usar esses utilitários é necessário estar dentro da linha de comando e não no shell do mongo.  
  

### Dump sem autenticação

Para fazer o dumpo use o utilitário `mongodump` e parâmetro `--out` para indicar onde ficarão salvos os bancos de dados em formato `BSON`.   

`mongodump --out /backup`  
   
### Dump com autenticação
  
Caso seja necessário atenticar ao banco para fazer o dump use os 
seguintes parâmetros para tal:  
   
-h - para host e porta;  
-u - para usuário;  
-p - para senhas.  
  
`mongodump -h servidor.com:27017 -u marcos -p 12344 --out /backup`  
  

### Restore

O restore será feito do diretório indicado para o banco e caso a base de dados não exista no mongo, ela será criada.  

É possível fazer o restore apenas de alguma coleção em particular. 
Também é possível usar wildcards(coringas) para fazer o restore do banco.  
  
O último parâmetro indica o local onde se encontra o backup.  

Alguns possíveis parâmetros abaixo:

-h ou --hostname - para host e porta;  
-u ou --username - para usuário;  
-p ou --password - para senhas.  
--port - para a porta
-d - Definir como ficará o nome para o banco restaurado no destino.

**Exemplos**
  
`mongorestore -h 127.0.0.1:27017 /backup`  
    
    
`mongorestore --host mongodb1.example.net --port 37017 --username marcos --password "123" /backup/mongodump-2011-10-24`  
    
## Documentação
  
* Estudar mais na [Documentação Oficial](https://docs.mongodb.com/manual/reference/program/mongorestore/).  