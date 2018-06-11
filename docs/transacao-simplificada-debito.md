# Transação simplificada

Estrutura e exemplo de uma transação simples para cartão de débito. As funcionalidades, como Análise de Fraude, OneClick e demais formas de pagamento precisam de uma estrutura mais completa para um perfeito funcionamento. Consulte as demais estruturas e exemplos desta documentação.

> **Exemplo de envio em JSON**

```curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --curl -u usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
  {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 179,
    "transacao" : {
        "numeroTransacao" : 123,
        "valor" : 100,
        "parcelas" : 1,
        "idioma" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "urlResultado" : "http://seusite.com.br/retorno"
    },
    "dadosCartao" : {
        "nomePortador" : "Teste Teste",
        "numeroCartao" : "0000000000000001",
        "codigoSeguranca" : "123",
        "dataValidade" : "12/2030"
    },
    "itensDoPedido" : [
    {
        "codigoProduto" : 1,
        "nomeProduto" : "Produto 1",
        "codigoCategoria" : 1,
        "nomeCategoria" : "categoria",
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 100
    }
    ],
    "dadosCobranca" : {
        "nome" : "Teste Integração",
        "documento" : "12312312312"
    }
  }
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
   {
    "numeroTransacao": 123,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 179,
    "valor": 2000,
    "valorDesconto": 0,
    "parcelas": 1,
    "statusTransacao": 1,
    "autorizacao": "123456",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "24/05/2030",
    "numeroComprovanteVenda": "10069930690009F2122A",
    "nsu": "428706",
    "mensagemVenda": "Operation Success",
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoVisaElectron.do?cod=14132971582229c00506d-e84d-4526-b902-92190d5aa808",
    "cartoesUtilizados": ["000000*******0001"]
  }
```
