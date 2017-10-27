## Oracle

O Oracle aqui é usado para treinamento. Para produção são necessários cuidados diferentes.  


### Imagem do Oracle no Docker

> Estou usando a versão `Oracle Express Edition 11g Release 2` rodando no  `Ubuntu 14.04 LTS (Trusty)`.

Esta imagem do Oracle para o docker não é uma imagem de repositório oficial.  
Ela foi retirada do repositório do (alexeiled)[https://hub.docker.com/r/alexeiled/docker-oracle-xe-11g/].


### Baixando a imagem do Oracle

`docker pull alexeiled/docker-oracle-xe-11g`

### Executando o container com a imagem do oracle-xe-11g

`docker run -d --shm-size=2g -p 1521:1521 -p 8080:8080 --name oracle1 alexeiled/docker-oracle-xe-11g`  

O significado dos parâmetros são:  


* -d - Vai rodar em modo `detach` como um serviço em background.  
* --shm-size=2g - Vai rodar com 2GB de memória compartilhada(shared memory).  
* -p 1521:1521 - Porta que o servidor Oracle usa para escutar; (Verificar se essa porta é segura);  
* -p 8080:8080 - Para acessar o Oracle no navegador no endereço: `http:/localhost:8080`.     

### Acessando o Oracle 

* Acesse o endereço `http://localhost:8080/` ou `http://localhost:8080/apex` no navegador.   
> Talvez seja necessário aguardar um pouco(alguns minutos) enquanto o servidor inicia para aparecer no navegador.  


### Conectando ao Oracle

As configurações para se conectar ao servidor Oracle são:  

* hostname: `localhost`;  
* porta: `1521`;  
* sid: `xe`;  
* username: `system`;  
* password: `oracle`;  

Senha para o usuário `sys` é `oracle`.  

### Conectando ao Oracle Application Express (APEX)

* url: `http://localhost:8080/apex`;    
* workspace: `internal`;  
* usuário: `admin`;  
* senha: `oracle`;  

> Logo em seguida mude a senha do admin.

### Fontes:

* (alexeiled)[https://hub.docker.com/r/alexeiled/docker-oracle-xe-11g/];
* (Apex)[http://www.oracle.com/technetwork/pt/articles/apex/comecando-com-oracle-apex-2776847-ptb.html]
