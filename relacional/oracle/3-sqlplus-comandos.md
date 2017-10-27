## Alguns comandos do sqlplus  

* Listar os últimos comandos digitados que se encontram no buffer:  
`list`  

* Executando o último comando do buffer:  
`run` ou `/`  

* Limpando buffer:  
`clear buff`  

* Limpar a tela:  
`cl scr`  

* Sair do sqlplus:  
`exit`  


### Usando um editor de textos no sqlplus  

> Defina um editor de texto:  
`define_editor = vi`  

> Crie e edite um arquivo .sql:  
`ed teste.sql`  

> Execute o script .sql(Carregue também scrpts do diretório onde o sqlplus foi aberto):  
`@teste.sql`  ou `start teste.sql`  

### Detalhes de um tabela  

* Mostre detalhes de uma tabela com `desc nomeDaTabela`:  

`desc v$database;`  


### Comando `host`  

Com o comando `host` podemos executar comandos no `sqlplus` como se estivessemos dentro
do prompt do sistema operacional, mas sem sair do sqlplus.  

**Exemplos**  
`host ls`  
`host pwd`  

> O comando `host` sem parâmetro leva o usuário para o prompt de comando. Quando terminar
e der um `exit` o prompt voltará para o `sqlplus`.  
`host`    


### Comando `help` para ajuda  

`help list`  
`help del`  
`help app`  

### Exibindo todos os parametros do sqlplus  

`show all` ou `show nomeDoParametro;`  

### Definir algum parâmetro do sqlplus  

`set pagesize 200`   
`set timing on`  
