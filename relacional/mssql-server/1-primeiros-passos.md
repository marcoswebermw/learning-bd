## Primeiros passos com MSSqlServer

Aqui estão alguns passos de como começar a usar o MSSqlServer no Linux.  
Será usada a ferramenta de linha de comando `sqlcmd` dentro do container para enviar
os comandos para o servidor.  Essa ferramenta se encontra no diretório `/opt/mssql-tools/bin/sqlcmd`.  



### Altere a senha padrão

Por padrão durante a instalação é criada a conta `SA` para administração do servidor.
Também é inserida uma senha para essa conta. Por questões de segurança é melhor trocar
essa senha depois da instalação.  
Vamos usar o `Transact-SQL` para alterar a senha:  

`sudo docker exec -it sqlserver1 /opt/mssql-tools/bin/sqlcmd
  -S localhost -U SA -P '<senha_forte>'
  -Q 'ALTER LOGIN SA WITH PASSWORD="Nova_Senha_Forte"'`  

* Primeiro é usado o `exec` para acessar o `sqlcmd` para inserirmos os comandos.
* Depois é definido o servidor `-S localhost` e usuário e senha que serão acessados `-U SA -P '<senha_forte>'`.
* E no fim com o parâmetro '-Q' é efetivamente alterado a senha através de uma query em `Transact-SQL`.   


### Conectando-se ao servidor

  * Entre dentro do servidor com:  

  `docker exec -it sqlserver1 "bash"`  

  * Depois execute o `sqlcmd` de uma das duas formas abaixo:  

  * Primeiro método passando a senha:  
  `/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'nova_senha_forte'`  

  * Segundo método não passando a senha e esperando o prompt pedir:  
  `/opt/mssql-tools/bin/sqlcmd -S localhost -U SA`  

  * Será aberto um prompt logo em seguida.  


### Sair do sqlcmd

`quit` ou `exit`  
