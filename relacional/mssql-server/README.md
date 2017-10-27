## Microsoft Sql Server

Usarei a versão da imagem do Docker `SQL Server Developer edition` que pode usar
todas as funcionalidades da versão `Enterprise` mas somente para testes e desenvolvimento.
Para produção terá que ser adquirida uma licença.  
O MSSqlServer usa como linguagem o `Transact-SQL` para comunicação com banco de dados.

> Usarei aqui a versão 2017 do MSSqlServer.  

Será usado aqui o `cli` que vem com o MSSqlServer que é chamado de `sqlcmd`.  


### Baixando a imagem mssql-server-linux para Docker

O mssql-server-linux será usado como um container do Docker.   
Primeiramente temos que baixar a imagem do repositório oficial.  
> A imagem tem mais de 1GB.  

`docker pull microsoft/mssql-server-linux:2017-latest`

### Executando o servidor em um container

O comando abaixo vai criar um container de desenvolvimento.

`docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<senha_forte>' -p 1401:1433 --name sqlserver1 -d microsoft/mssql-server-linux:2017-latest`


**Descrição dos parâmetros:**

  | Comando | Descrição |
  |----------|----------|
  | -e 'ACCEPT_EULA=Y' | Aceita a licença da Microsoft para desenvolvimento. |
  | -e 'MSSQL_SA_PASSWORD=<senha_forte>' | Define uma senha forte de pelo menos 8 caracteres para acessar o servidor. |
  | -p 1401:1433 | Expõe a porta 1433 do container para a porta 1401 do host. |
  | --name sqlserver1 | Define um nome para o container. |
  | -d | Rodando em modo daemon. |
  | microsoft/mssql-server-linux:2017-latest | Nome da imagem do Sql Server. |

>  Pode também ser usado o parâmetro `-h` para definir o nome interno do host.  


### Fontes:

* (Sql Server Linux Overview)[https://docs.microsoft.com/pt-br/sql/linux/sql-server-linux-overview];
* (Quick Start)[https://docs.microsoft.com/pt-br/sql/linux/quickstart-install-connect-docker];
* (Imagem Docker)[https://hub.docker.com/r/microsoft/mssql-server-linux/];
