# Checkout 2.0

Disponibilizamos uma nova versão de nosso Checkout com algumas melhorias: novo layout, validação de BIN, escolha das formas de pagamento e aumento da segurança com recaptcha v3.

A alteração na estrutura foi mínima, para utilizar a nova versão do Checkout Yapay basta enviar a tag `<versao>` igual a 2 no nó `checkout`.

Maiores informações sobre a estrutura

> **Particularidades**

* Funcionalidade com redirecionamento;
* Importante a utilização do recurso de Campainha, para atualização dos pedidos no Ecommerce;
* Fechamento automático para Não Pago de pedidos expirados;
* Nesta versão ainda não está disponivél o pagamento com multiplos cartões.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

> **Exemplos**

**REQUISIÇÃO**

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
        "formasPagamento" : [170,171,29],
        "oneclick" : 1
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

**RETORNO**

```curl
  --header "Content-Type: application/json"
      {
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/checkout/redirecionaPagamento?codigoPagamento=150609150796704e7-5b25-4a41-a753-a09bfb66db8d&tipoPagamento=0&oneClick=false"
      }
```

