## Configurando o Cassandra
  
Baixe ele no site oficial ou use o docker com `docker run cassandra`.  
  
### Instalando em Debians-like
  
Adicione o repositório do Cassandra no source.list do Debian.  
    
`echo "deb http://www.apache.org/dist/cassandra/debian 311x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list `  
   
Adicione as chaves do repositório Cassandra.  
  
`curl https://www.apache.org/dist/cassandra/KEYS | sudo apt-key add - `  
  
Atualize o repositório e instale.   
  
`sudo apt update && sudo apt install cassandra -y`  

Verifique que o Cassandra está rodando.  

`nodetool status`       

Ou.  

`sudo service cassandra status`    
  

### Iniciando o Cassandra
  
`cassandra -f`  
  
Em Debians-like:  
  
`sudo service cassandra start`  
  
Para parar

`sudo service cassandra stop`    
  

### Arquivos do Cassandra

Os arquivos de configuração do Cassandra se encontram em:    
  
* Configurações: `/etc/cassandra`;  
* Dados: `/var/lib/cassandra`;  
* Logs: `/var/log/cassandra`;  
* Opções de inicialização: `/etc/default/cassandra`;  
  

### Referências
  
* [Download Cassandra](http://cassandra.apache.org/download/);  
