### Usando documentos aninhados(Embebidos)
  
Os documentos aninhados são aqueles documentos que ficam dentro de outros. 
São subdocumentos.  
Em bancos orientados a documentos ás vezes é preferível deixar informações no próprio documento(duplicá-las) do que buscá-los 
em outros por questões performaticas.  
No exemplo abaixo `endereco` é um subdocumento.

```js

db.novaColecao.insert( 
                      { nome: "Fulano", 
                        idade: 30,
                        endereco: { rua: "15 de Novembro", 
                                    numero: 10
                                  }
                      } 
                    );


db.novaColecao.updateOne( 
                         { nome: "Fulano" }, 
                         { $set: { 
                                   "endereco.cidade" : "São Paulo" 
                                  } 
                          } 
                         );

```  