# OneClick

<span class="post">POST</span>

No Checkout Yapay também está disponível o pagamento com token, assim nas futuras compras o consumidor digitará apenas o código de segurança do cartão.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout.md?id=oneclick)

> **Particulariedades**

* Disponível apenas no Plano Corporativo;

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
        "processar": 1,
        "tipoPagamento" : 1
     },
    "itensDoPedido" : [
    {
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 100
    }
    ],
    "dadosCobranca" : {
        "nome" : "Teste Integração",
        "documento" : "12312312312",
        "email": "teste@teste.com"
    }
  }
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
      {
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/checkout/redirecionaPagamento?codigoPagamento=15296042250074c4b0dc5-04cx-4f5d-a3d0-194d06aa5a5f&oneClick=true"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout para uma transação com OneClick. Será exibido o cartão cadastrado caso o cliente já tenha efetuado uma venda na loja e tenha permitido salvar seus dados de cartão.

![API Transação Yapay](/images/checkout_oneclick.png "API Yapay")
