## Sqlplus

Existe uma ferramenta interativa(cli), chamada `sqlplus`.  
Com ela é possível acessar o Oracle via linha de comando.  

### Executando o sqlplus no container  

* Crie um container:  

`docker run -d --shm-size=2g -p 1521:1521 -p 8080:8080 --name oracle1 alexeiled/docker-oracle-xe-11g`  

* Entre dentro de um container Oracle em execução:  

`docker exec -it oracle1 "bash"`  

* Entre no sqlplus:  

`sqlplus`  

* será pedido um usuário e senha que podem ser:  

`system` e `oracle`  ou `admin` e `oracle` ou `sys` e `oracle`  

### Outra forma de logar no Sqlplus

`sqlplus usuario/senha;` ou também como dba `sqlplus usuario/senha as sysdba;`  

### Testando o sqlplus

Dentro do Sqlplus execute o seguinte comando para testar se a conexão funcionou:  

`SELECT name FROM v$database;`  





### Sql Developer  

Também é possível trabalhar no Oracle com uma ferramenta gráfica chamada `Sql Developer`.  
Baixe-a em: (Sql Developer)[http://www.oracle.com/technetwork/pt/developer-tools/sql-developer/downloads/index.htm]  
