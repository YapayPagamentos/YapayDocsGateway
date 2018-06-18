# Alteração

API para alteração do cadastro de OneClick.

> **Exemplo de envio em JSON**

```curl
  curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick/1514483826864c3149224-67db-4557-8950-6a80f708c1c5/alterar
  --header "Content-Type: application/json"
  --curl -u usuario:senha
  --data-binary
  {
  "codigoEstabelecimento": 1000000000000,
  "formaPagamento": 170,
  "nomeTitularCartaoCredito": "Teste OneClick",
  "numeroCartaoCredito": "0000000000000002",
  "dataValidadeCartao": "10/2021",
  "emailComprador": "yapay@yapay.com.br"
  }
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json
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
