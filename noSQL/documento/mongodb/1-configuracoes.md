  
### Baixando mongodb via Docker
  
`docker pull mongo:latest`  
  
#### Subindo o servidor
  
`docker run -d -p 27017:27017 --rm --name mongodb1 mongo:latest`  

> O nome do serviço do mongodb no sistema operacional é `mongod`.    

#### Entrando no cli do mongodb
  
`docker exec -it mongodb1 mongo`  
  
### Instalação manual
  
O mongo pode ser baixado no site oficial do (MongoDB)[https://www.mongodb.com].  
Depois de baixado o arquivo tem que ser extraído em algum diretório.  
Dentro do diretório existe outro chamado `bin`. Dentro deste diretório se encontram os seguintes programas para gerenciamento do Mongo: 

* mongod - O programa que inicializa o servidor de fato.
* mongo - Inicializa o cliente para acesso ao mongo.
* mongodump - Faz o dump do banco em binário.
* mongorestore - Faz a restauração do dump binário.
* mongoexport - Faz o export de documentos em formato JSON ou CSV.
* mongoimport - Faz o import de documentos em formato JSON ou CSV.
  
Para iniciar o servidor do mongo na porta padrão `27017` e salvar os arquivos do banco de dados no diretório `/tmp`, por exemplo, faça o seguinte:  
  
`mongod --dbpath /tmp`  
  
> Aqui o mongo está sendo iniciado sem preocupação com a segurança e alta disponíbilidade.
  
Em outro terminal se conecte ao mongo da seguinte maneira:  
  
`mongo`  
  
