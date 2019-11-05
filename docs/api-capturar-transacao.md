# Capturar transação

## Capturar transação total

<span class="put">PUT</span>

Através desta API é possível confirmar uma pré autorização na adquirente, assim o consumidor receberá a cobrança em seu cartão e gerará crédito ao lojista. Os estabelecimentos com captura manual deverão acionar a API de captura de acordo com a tabela abaixo, pois após este período a adquirente cancelará automaticamente a pré autorização.

Operadora   | 	Limite Captura
----------  | -----------------------
Cielo |	5 dias, mas pode variar de acordo com o contrato. Consulte a Cielo para maiores informações
Rede |	Pode variar conforme o ramo de atuação de cada estabelecimento. Consulte a Rede para maiores informações
GETNET|	30 dias da geração do pedido
Stone|	7 dias da geração do pedido
Bin|    5 dias da geração do pedido

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/capturar
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/capturar

> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/1000000000000/1234/capturar
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
    "statusTransacao": 1,
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

## Capturar transação parcial

<span class="put">PUT</span>

Através desta API é possível confirmar parte do valor de uma pré autorização na adquirente.

Operadora   | 	Limite Captura
----------  | -----------------------
Cielo |	5 dias, mas pode variar de acordo com o contrato. Consulte a Cielo para maiores informações
Rede |	Pode variar conforme o ramo de atuação de cada estabelecimento. Consulte a Rede para maiores informações
GETNET|	30 dias da geração do pedido

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/capturar?valor=
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/capturar?valor=

> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/1000000000000/123401/capturar?valor=1000
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  {
    "numeroTransacao": 123401,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 170,
    "valor": 2000,
    "valorDesconto": 0,
    "parcelas": 1,
    "statusTransacao": 1,
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

