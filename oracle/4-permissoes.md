## Conceder permissões para o usuário

* Primeiro crie um usuário:  

`CREATE USER fulano IDENTIFIED BY senha_do_fulano;`  

* Dê as permissões para o usuário:  

`GRANT connect, resource TO fulano;`  


### Algumas permissões.

| Permissão | Descrição |
| --------- | --------- |
| connect | Concede permissão de conexão. |  
| dba | Concede permissão de dba(administrador). |  
| resource | Concede permissão de acesso a recursos. |  
