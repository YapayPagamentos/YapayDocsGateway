## Cancelar transação total

<span class="put">PUT</span>

Através desta API é possível cancelar uma autorização ou venda capturada. 
Abaixo o prazo de cancelamento para cada adquirente:

Adquirente | Prazo de cancelamento
---------- | ----------------------
Cielo|	300 dias após a geração do pedido para transações capturadas e 15 dias úteis para transações apenas autorizadas
Rede|	Pode variar conforme o ramo de atuação de cada estabelecimento
GetNet|	365 dias para transações capturadas*. 7 dias para vendas autorizadas
Stone|	180 dias após a geração do pedido
Bin|	90 dias após captura do pedido

*Caso a solicitação de cancelamento seja realizada em D+1, o Gateway retornará o status 40 (Aguardando cancelamento) até que a cancelamento seja realizado.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/cancelar
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/cancelar

> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/10000000000000/1234/cancelar
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
   {
      "numeroTransacao": 1234,
      "codigoEstabelecimento": "1000000000000",
      "codigoFormaPagamento": 170,
      "valor": 2000,
      "valorDesconto": 0,
      "parcelas": 1,
      "statusTransacao": 13,
      "autorizacao": "123456",
      "codigoTransacaoOperadora": "0",
      "dataAprovacaoOperadora": "24/05/2018",
      "numeroComprovanteVenda": "10069930690009F2122A",
      "nsu": "428706",
      "mensagemVenda": "Operation Success",
      "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoCielo.do?cod=14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
      "cartoesUtilizados": ["000000*******0001"]
      }
```

## Cancelar transação parcial

<span class="put">PUT</span>

Através desta API é possível cancelar uma venda parcialmente. 
Consulte abaixo as adquirentes que fornecem o cancelamento parcial e o prazo de cancelamento:

Adquirente | Tecnologia | Prazo de cancelamento | Observação
---------- | -----------| ----------- | ----------
Cielo|	API 3.0| 300 dias após a geração do pedido para transações capturadas e 15 dias úteis para transações apenas autorizadas | -
Rede|	E Rede|	Pode variar conforme o ramo de atuação de cada estabelecimento | Disponível apenas após D+1 da captura
GetNet| GetNetWS | 365 dias para transações capturadas*. | Disponível apenas após D+1 da captura
BIN| BIN | Ocorre no mesmo dia da venda | -

* Gateway retornará o status 40 (Aguardando cancelamento) até que a cancelamento seja realizado.

> **Particulariedades**

* Disponível apenas no plano corporativo;
* A transação deverá estar capturada para realizar o cancelamento parcial, do contrário, o cancelamento será total.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/cancelar?valor=
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/cancelar?valor=

> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/10000000000000/1234/cancelar?valor=1000
  --header "Content-Type: application/json"
  --curl -u usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  {
    "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 170,
    "valor": 2000,
    "valorDesconto": 0,
    "parcelas": 1,
    "statusTransacao": 27,
    "autorizacao": "123456",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "2018-01-03 13:02:53",
    "numeroComprovanteVenda": "10069930690009F2122A",
    "nsu": "428706",
    "mensagemVenda": "Operation Success",
    "urlPagamento": "14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
    "cartoesUtilizados": ["000000*******0001"]
  }
```

