## Instalando o Neo4j
  
Existem algumas formas para instalar o Neo4j.  
  


### Baixando
  
O instalador pode ser baixado em [Download](https://neo4j.com/download/).  
  
### Usando o Docker
  
Acredito que a melhor maneira(principalmente para treinamento) seja usando uma das imagens feitas para uso no Docker.  
  
Alguns links com informações a respeito:

* [Imagens oficiais no Docker Hub](https://hub.docker.com/_/neo4j/)    
* [Imagens oficiais na Docker Store](https://store.docker.com/images/neo4j)    
* [Repositório das imagens no Github](https://github.com/neo4j/docker-neo4j)    
* [Documentação oficial](https://neo4j.com/developer/docker/)    
  
### Baixando imagem Docker de forma simples
  
```sh
docker pull neo4j
```
  
### Forma mais completa de baixar imagem Docker
  
```sh
docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    --volume=$HOME/neo4j/logs:/logs \
    neo4j:3.0
```
  
#### O Docker expõe por padrão 3 portas para acesso remoto:
  
* 7474 - http  
* 7473 - https  
* 7687 - bolt  
  
#### O Docker também expõe dois volumes:
  
* /data - para o banco persistir fora do container.  
* /logs - para acessar os logs do banco.   
  
### Acessando o Neo4j
  
Para acessar o cliente, acesse o seguinte endereço no navegador:
  
`http://localhost:7474`  
   
### Autenticando
  
Para autenticar use o login e senha `neo4j/neo4j`.  
  
> Em produção não esquecer de trocar a senha.  
  
### Referências
  
[Neo4j Docker](https://neo4j.com/developer/docker/)  

