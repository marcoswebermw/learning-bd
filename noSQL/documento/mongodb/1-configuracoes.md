  
### Baixando mongodb via Docker
  
`docker pull mongo:latest`  
  
### Subindo o servidor
  
`docker run -d -p 27017:27017 --rm --name mongodb1 mongo:latest`  
  
### Entrando no cli do mongodb
  
`docker exec -it mongodb1 mongo`