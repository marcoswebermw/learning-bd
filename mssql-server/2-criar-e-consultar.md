## Criar e Consultar dados

Será mostrado como criar dados e como consultá-los dentro do sgbd.  
Serão usados o `sqlcmd` para enviar comandos para o sgbd e a linguagem `Transact-SQL`
para a criação e consulta dos dados.  

### Criando um banco de dados.

> Os comandos não serão executados imediatamente. Depois de digitá-los é necessário
executar o comando `GO` para que eles realmente alterem algo no sgbd.


Crie o banco:
`CREATE DATABASE BDTest`  

Mostre todos os bancos de dados no sistema:  
`SELECT Name from sys.Databases`  

Depois execute o `GO` para executar os comandos anteriores.  
`GO`  


### Selecione o banco de dados a ser usado  

`USE BDTest`  

`GO`  

### Crie uma tabela  

`CREATE TABLE Pessoa (id INT, nome NVARCHAR(50), idade INT)`

`GO`  

### Inserindo dados  

`INSERT INTO Pessoa VALUES (1, 'Amber Heard', 31)`;  
`INSERT INTO Pessoa VALUES (2, 'Margot Robbie', 27)`;  
`INSERT INTO Pessoa VALUES (3, 'Ana de Armas', 29)`
`GO`

## Consultando dados   

`SELECT * FROM Pessoa`
`GO`  

Outra consulta:  

`SELECT * FROM Pessoa WHERE idade > 30`  
`GO`  
