# Consulta recorrência

<span class="get">GET</span>

API para consulta das recorrências.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia/«codigoEstabelecimento»/«numeroRecorrencia»
Produção |https://gateway.yapay.com.br/checkout/api/v3/recorrencia/«codigoEstabelecimento»/«numeroRecorrencia»

> **Exemplo de envio em JSON**

```curl
curl
  --request GET https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia/10000000000000/2
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
 "recorrencia": {
    "estabelecimento": "1000000000000",
    "numeroRecorrencia": 2,
    "codigoFormaPagamento": 170,
    "valor": 13000,
    "numeroCobrancaTotal": 0,
    "numeroCobrancaRestantes": -1,
    "status": 0,
    "mensagem": "Processamento realizado com sucesso.",
    "numeroPedido": 20001,
    "statusTransacao": 1,
    "autorizacao": "123456",
    "codigoTransacaoOperadora": "00",
    "dataAprovacaoOperadora": "30/05/2017",
    "numeroComprovanteVenda": "1006993069000891071A",
    "mensagemVenda": "Operation Success"
    }
```



