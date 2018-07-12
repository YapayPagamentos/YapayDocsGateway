# Consulta OneClick

<span class="get">GET</span>

API para consulta de dados através do TOKEN.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick/«token»
Produção |https://gateway.yapay.com.br/checkout/api/v3/oneclick/«token»

> **Exemplo de envio em JSON**

```curl
curl
  --request GET https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick/1514483826864c3149224-67db-4557-8950-6a80f708c1c5
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  { 
  "codigoEstabelecimento": 1000000000000,
  "codigoFormaPagamento": 170,
  "oneClick": 1,
  "token": "1514483826864c3149224-67db-4557-8950-6a80f708c1c5",
  "nomeTitularCartaoCredito": "Teste OneClick",
  "numeroCartaoCredito": "000000******0002",
  "dataValidadeCartao": "10/2021",
  "emailComprador": "yapay@yapay.com.br"
  }
```



