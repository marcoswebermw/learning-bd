## Documentos
  
Os documentos são parecidos com as linhas, registros ou tuplas de uma tabela relacional, mas não são a mesma coisa.  

Nele é possível fazer inserções, alterações, remoções e buscas como no modelo relacional.  
  
Documentos tem tudo que precisam, são auto-suficientes(não dependem de relacionamentos).  
  
No mongodb um documento é muito parecido com arquivos JSON.  

**Exemplo de documento tirado da documentação**
  
```js
{
   "_id" : 1,
   "sku" : "abc123",
   "quantity" : 8,
   "metrics" : {
      "orders" : 3,
      "ratings" : 3.5
   }
}
```
  
> Acesse o diretório `CRUD` para verificar as principais operações feitas em um documento.  
  
### Dicas para trabalhar com documentos  
  
Evite usar os documentos como os relacionamentos do modelo relacional. Aqui estamos trabalhando com o modelo de documentos.  
  
Não faça muitos aninhamentos, mantenha o documento o mais simples possível.  
  
