# Simplificada

<span class="url">VERSÃO ANTIGA</span>
<br>
<br>

<span class="post">POST</span>

Estrutura e exemplo de uma transação simples com o Checkout Yapay. 


Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout.md?id=transação-simplificada)

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
        "processar": 0,
        "tipoPagamento" : 0
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
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1602000c2d2-a1br877687871-6767868678"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout:

![API Transação Yapay](/images/checkout_simp.png "API Yapay")

# Múltiplos Boletos

<span class="post">POST</span>

No Checkout Yapay também está disponível o pagamento com mais de um boleto, assim é possível dividir o valor total em vários boletos.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout.md?id=múltiplos-boletos)

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
        "valor" : 10000,
        "parcelas" : 1,
        "idioma" : 1,
        "urlCampainha": "http://sualoja.com.br/campainha/",
        "urlResultado": "http://sualoja.com.br"
    },
     "checkout": {
        "processar": 0,
        "tipoPagamento" : 3,
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
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1602000c2d2-a1br877687871-6767868678"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout para uma transação com Múltiplos Boletos:

![API Transação Yapay](/images/checkout_multboleto.png "API Yapay")

# Múltiplos Cartões

<span class="post">POST</span>

No Checkout Yapay também está disponível o pagamento com mais de um cartão.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout.md?id=múltiplos-cartões)

> **Particulariedades**

* Disponível apenas no Plano Corporativo;
* Disponível para cartão de crédito;

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
        "processar": 0,
        "tipoPagamento" : 1,
        "multiploCartao" :1
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
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1602000c2d2-a1br877687871-6767868678"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout para uma transação com Múltiplos Cartões:

![API Transação Yapay](/images/checkout_multcartao.png "API Yapay")

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
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1602000c2d2-a1br877687871-6767868678"
      }
```

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout para uma transação com OneClick. Será exibido o cartão cadastrado caso o cliente já tenha efetuado uma venda na loja e tenha permitido salvar seus dados de cartão.

![API Transação Yapay](/images/checkout_oneclick.png "API Yapay")
