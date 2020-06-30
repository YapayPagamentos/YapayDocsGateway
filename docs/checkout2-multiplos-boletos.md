# Múltiplos Boletos

<span class="post">POST</span>

No Checkout Yapay também está disponível o pagamento com mais de um boleto, assim é possível dividir o valor total em vários boletos.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout2.md?id=múltiplos-boletos)


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
        "valor" : 10000,
        "parcelas" : 1,
        "idioma" : 1,
        "urlCampainha": "http://sualoja.com.br/campainha/",
        "urlResultado": "http://sualoja.com.br"
    },
     "checkout": {
        "versao" : 2,
        "multiploBoleto" : 1,
        "boletos": [
         {
          "valor": 5000,
          "vencimento": "13/01/2019"
         },
         {
          "valor": 5000,
          "vencimento": "13/02/2019"
         }
       ]
     },
    "itensDoPedido" : [
    {
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 100
    }
    ],
     "dadosCobranca" : {
        "codigoCliente" : 1,
        "tipoCliente" : 1,
        "nome" : "Teste 123",
        "email" : "teste@teste.com",
        "dataNascimento" : "10/01/1975",
        "sexo" : "M",
        "documento" : "123.123.123-12",
        "endereco" : {
          "logradouro" : "Rua",
          "numero" : "123",
          "complemento" : "",
          "cep" : "12345-678",
          "bairro" : "Bairro",
          "cidade" : "Cidade",
          "estado" : "SP",
          "pais" : "BR"
          }
       }
    }
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
      {
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=15705573858156e0f9acd-4f71-4220-b71c-45749e03"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout para uma transação com Múltiplos Boletos:

![API Transação Yapay](/images/check2-multboletos.png "API Yapay")
