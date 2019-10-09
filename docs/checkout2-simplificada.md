# Simplificada

<span class="post">POST</span>

Estrutura e exemplo de uma transação simples com o Checkout Yapay. 


Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout2.md?id=transação-simplificada)

> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
    {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 997,
    "transacao" : {
        "numeroTransacao" : 1,
        "valor" : 100,
        "parcelas" : 1,
        "idioma" : 1,
        "urlCampainha": "http://sualoja.com.br_campainha/",
        "urlResultado": "http://sualoja.com.br"
    },
     "checkout": {
        "versao" : 2,
        "formasPagamento" : [170, 171, 29]
     },
    "itensDoPedido" : [
    {
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
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1570627364596ca6a0a1d-90cb-4411-998a-6299c1c5e4"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout:

![API Transação Yapay](/images/checkout2.png "API Yapay")
