# Consulta transação

<span class="get">GET</span>

API para consulta das transações e recebimento dos dados de retorno da mesma.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»

> **Exemplo de envio em JSON**

```curl
curl
  --request GET https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/10000000000000/1234
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  {   "numeroTransacao": 1234,
      "codigoEstabelecimento": "1000000000000",
      "codigoFormaPagamento": 170, 
      "valor": 2000, 
      "valorDesconto": 0, 
      "parcelas": 1,
      "statusTransacao": 13,
      "autorizacao": "123456",
      "codigoTransacaoOperadora": "0", 
      "dataAprovacaoOperadora": "24/05/2017",
      "numeroComprovanteVenda": "10069930690009F2122A",
      "nsu": "428706",
      "mensagemVenda": "Operation Success",
      "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoCielo.do?cod=14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
      "cartoesUtilizados": ["000000*******0001"]
  }
```



