## Riak

É um banco de dados do tipo chave-valor.  

Banco de dados chave-valor costumam ser muito simples e rápidos.  

O Riak tem alta disponibilidade de escrita, é open source, escrito em Erlang. O console dele é manipulado em Erlang o que pode ser uma barreira.   

Em bancos chave-valor geralmente não existe diferença entre o `insert` e o `update`, o que vale é o ultimo valor inserido.  

No Riak além do console é oferecida uma interface via protocolo http para fazermos operações de `crud` por exemplo.  

O Riak pode receber por padrão 3 tipos de informações:  

* `Bucket` que funciona como um namespace ou uma tabela no modelo relacional.  
* `Chave` que é o nome da nossa chave de acesso ao dado armazenado.  
* `Valor` que é o valor armazenado em determinada chave.  
  
