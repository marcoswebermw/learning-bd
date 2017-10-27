## Gerenciamento de usuários no Oracle

## Criando um usuário no Oracle

Para criar um novo usuário no Oracle com permissões de admin.  
Execute os seguintes comando dentro do `sqlplus`.  

* Conecte-se como `sys` e dê permissão de `sysdba` para ele. Informe a senha do `sys`.

`CONNECT sys AS sysdba`  

* Crie um usuário `fulano` e dê a senha `senha_fulano` para ele.  

`CREATE USER fulano IDENTIFIED BY senha_fulano;`  

* Dê privilégio de `DBA` para ele.  

`GRANT DBA TO fulano;`  

* Saia do `sqlplus` com `exit` e tente se logar com o usuário `fulano` com permissões de dba.  

> Depois caso queira conectar com outro usuário é só usar o comando `connect` que será pedido
o login e senha do usuário.  


### Listando usuários do banco de dados  

O Oracle cria uma view com todos os usuários do banco de dados chamada `ALL_USERS`.  

`SELECT * FROM ALL_USERS;`  


### Deletando usuário  

`DROP USER fulano;`
