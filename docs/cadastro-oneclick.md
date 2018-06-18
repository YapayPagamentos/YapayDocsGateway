# Cadastro

API para cadastro dos dados de cartão e recebimento do token.

> **Exemplo de envio em JSON**

```curl
 --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick
  --header "Content-Type: application/json"
  --curl -u usuario:senha
  --data-binary
  {
     "codigoEstabelecimento": 1000000000000,
     "formaPagamento": 170,
     "nomeTitularCartaoCredito": "Teste OneClick",
     "numeroCartaoCredito": "0000000000000001",
     "dataValidadeCartao": "10/2020",
     "emailComprador": "yapay@yapay.com.br"
  }
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json
  { 
  "codigoEstabelecimento": 1000000000000,
  "formaPagamento": 170,
  "oneClick": 1,
  "token": "1514483826864c3149224-67db-4557-8950-6a80f708c1c5",
  "nomeTitularCartaoCredito": "Teste OneClick",
  "numeroCartaoCredito": "000000******0001",
  "dataValidadeCartao": "10/2020",
  "emailComprador": "yapay@yapay.com.br"
  }
```
