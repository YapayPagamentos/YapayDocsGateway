# Checkout com logo personalizado

Funcionalidade disponível no Checkout Yapay, onde permite ao estabelecimento cadastrar um logo na base Yapay.
Desta forma, o logo da loja será disponibilizado em nosso Checkout, trazendo uma maior segurança ao consumidor no momento da finalização do pagamento.

![Checkout Yapay com Logo](/images/checkout_logo.png "checkout")

## Cadastrar logo

<span class="post">PUT</span>

API que possibilita o cadastro de um logo em base64 para o estabelecimento.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/«codigoEstabelecimento»/inclui
Produção |https://gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/«codigoEstabelecimento»/inclui


> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/100000000000/inclui
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
    {
    "imagem": "data:image/png;base64..."
  }
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
      {
       "mensagem": "Imagem cadastrada"
      }
```

## Consultar

<span class="post">GET</span>

API para consultar um logo já cadastrado

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/«codigoEstabelecimento»/
Produção |https://gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/«codigoEstabelecimento»/


> **Exemplo de envio em JSON**

```curl
curl
  --request GET https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/100000000000/
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
      {
       "imagem": "data:image/png;base64..."
      }
```

## Remover logo

<span class="post">PUT</span>

API para remover logo cadastrado

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/«codigoEstabelecimento»/remove
Produção |https://gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/«codigoEstabelecimento»/remove


> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/100000000000/remove
  --user usuario:senha 
  --header "Content-Type: application/x-www-form-urlencoded"
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/x-www-form-urlencoded"
      {
       "mensagem": "imagem removida"
      }
```
