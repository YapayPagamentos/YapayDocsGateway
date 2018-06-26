# Introdução

O Yapay disponibiliza a integração com diversas Instituições Financeiras através de uma única integração via API em RESTful.

![API Transação Yapay](/images/transacao.png "API Yapay")

A comunicação com o Yapay Gateway ocorrerá após a finalização do pagamento no Checkout do Ecommerce, de forma transparente para o consumidor. Ao ser finalizado o pagamento dentro da loja, o Ecommerce deverá consumir os serviços WebServices do Yapay encaminhando as informações da compra de acordo com a estrutura que será apresentada nesta documentação.
Para cartões de débito será obrigatório o redirecionamento do cliente para a URL do banco retornada pelo Gateway, onde o consumidor digitará sua senha eletrônica e finalizará a compra.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

## Transação simplificada

<span class="post">POST</span>

Estrutura e exemplo de uma transação simples para cartão de débito. As funcionalidades, como Análise de Fraude, OneClick e demais formas de pagamento precisam de uma estrutura mais completa para um perfeito funcionamento. Consulte as demais estruturas e exemplos desta documentação.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-cartoes-debito.md?id=transação-simplificada)

> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --user usuario:senha 
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
