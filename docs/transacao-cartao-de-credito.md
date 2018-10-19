# Introdução

O Yapay disponibiliza a integração com diversas Instituições Financeiras através de uma única integração via API em RESTful.

![API Transação Yapay](/images/transacao.png "API Yapay")

A comunicação com o Yapay Gateway ocorrerá após a finalização do pagamento no Checkout do Ecommerce, de forma transparente para o consumidor. Ao ser finalizado o pagamento dentro da loja, o Ecommerce deverá consumir os serviços WebServices do Yapay encaminhando as informações da compra de acordo com a estrutura que será apresentada nesta documentação.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

## Transação simplificada

<span class="post">POST</span>

Estrutura e exemplo de uma transação simples para cartão de crédito. As funcionalidades, como Análise de Fraude, Recorrência, OneClick e demais formas de pagamento precisam de uma estrutura mais completa para um perfeito funcionamento. Consulte as demais estruturas e exemplos desta documentação.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-cartoes-credito.md?id=transação-simplificada)

> **Exemplo de envio em JSON**

```curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --curl -u usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
  {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 170,
    "transacao" : {
        "numeroTransacao" : 123,
        "valor" : 100,
        "parcelas" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha"
    },
    "dadosCartao" : {
        "nomePortador" : "Teste Teste",
        "numeroCartao" : "0000000000000001",
        "codigoSeguranca" : "123",
        "dataValidade" : "12/2030"
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
    "numeroTransacao": 123,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 170,
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
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoCielo.do?cod=14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
    "cartoesUtilizados": ["000000*******0001"]
  }
```
## Transação com análise de fraude

<span class="post">POST</span>

A utilização desta estrutura é indicada para envio de pedidos com a forma de pagamento cartão de crédito, onde o estabelecimento possui contratação de umas das empresas de análise de risco integradas pelo Yapay, sendo elas ClearSale (modalidades: Total/Total Garantido, Application, ID e Start) e FControl (modalidade Fila).

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-cartoes-credito.md?id=transação-com-análise-de-fraude)

`Contratação a parte com as empresas ClearSale e FControl`
<br>

> **Exemplo de envio em JSON**

```curl
 --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
    --header "Content-Type: application/json"
    --curl -u usuario:senha
    --data-binary
    {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 190,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "valorDesconto" : 0,
        "parcelas" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "ip" : "192.168.12.110",
        "idioma" : 1
    },
    "dadosCartao" : {
        "nomePortador" : "Teste Teste",
        "numeroCartao" : "4002479199570736",
        "codigoSeguranca" : "132",
        "dataValidade" : "12/2020"
    },
    "itensDoPedido" : [
    {
        "codigoProduto" : 1,
        "nomeProduto" : "Produto 1",
        "codigoCategoria" : 1,
        "nomeCategoria" : "categoria",
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 2000
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
            },
        "telefone" : [
            {
            "tipoTelefone" : "1",
            "ddi" : "55",
            "ddd" : "12",
            "telefone" : "1234-5678"
            }
        ]
    },
    "dadosEntrega" : { 
        "nome" : "Teste 123",
        "endereco" : {
            "logradouro" : "Rua",
            "numero" : "123",
            "complemento" : "",
            "cep" : "12345-678",
            "bairro" : "Bairro",
            "cidade" : "Cidade",
            "estado" : "SP",
            "pais" : "BR"
            },
        "telefone" : [
            {
            "tipoTelefone" : "1",
            "ddi" : "55",
            "ddd" : "12",
            "telefone" : "1234-5678"
            }
        ]
    }
    }
```

> **Exemplo de retorno JSON**

```curl
--header "Content-Type: application/json"
    {  "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 190,
    "valor": 2000, 
    "valorDesconto": 0, 
    "parcelas": 1, 
    "statusTransacao": 1,
    "autorizacao": "12260",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "24/05/2030", 
    "numeroComprovanteVenda": "10117092009151900057", 
    "nsu": "428706",
    "mensagemVenda": "00 - Success",
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoCielo.do?cod=14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66", 
    "cartoesUtilizados": ["400247******0736"]
    }
```

## Transação com múltiplos cartões

<span class="post">POST</span>

Através desta estrutura é possível o envio de mais de um cartão de crédito para aprovação em uma mesma transação, dividindo o valor total do pedido entre os cartões.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-cartoes-credito.md?id=transação-com-múltiplos-cartões)

> **Particulariedades**

* Disponível apenas no plano Corporativo;
* Disponível apenas para cartões de cŕedito na modalidade WS.

> **Exemplo de envio de JSON**

```curl
curl
   --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
   --header "Content-Type: application/json"
   --user usuario:senha
   --data-binary
   {
   "codigoEstabelecimento" : 1000000000000,
   "codigoFormaPagamento" : 999,
   "dadosMultiplosCartoes": [
      {
        "nomePortador": "CARTAO 1",
        "numeroCartao": "0000000000000001",
        "codigoSeguranca": "321",
        "dataValidade": "12/2024",
        "codigoFormaPagamento": 170,
        "parcelas": 1,
        "valor": 500
      },
      {
        "nomePortador": "CARTAO 2",
        "numeroCartao": "0000000000000001",
        "codigoSeguranca": "123",
        "dataValidade": "12/2022",
        "codigoFormaPagamento": 171,
        "parcelas": 1,
        "valor": 800
      }
    ],
    "transacao" : {
        "numeroTransacao" : 1234,
        "idioma" : 1
    },
    "itensDoPedido" : [
        {
        "codigoProduto" : 1,
        "codigoCategoria" : 1,
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 2000
        }
      ],
    "dadosCobranca" : {
        "tipoCliente" : 1,
        "nome" : "Teste 123",
        "documento" : "123.123.123-12"
       }
   }
```

> **Exemplo de retorno JSON**

```curl
--header "Content-Type: application/json"
{
"numeroTransacao": 1234,
"codigoEstabelecimento": "1000000000000",
"multiploCartao": 1,
"statusTransacao": 1,
"detalhesMultiploCartao":    [
        {
        "codigoFormaPagamento": 170,
        "valor": 500,
        "valorDesconto": 0,
        "parcelas": 1,
        "autorizacao": "513663",
        "codigoTransacaoOperadora": "6",
        "dataAprovacaoOperadora": "2018-02-21 11:50:21",
        "numeroComprovanteVenda": "0221115021704",
        "mensagemVenda": "Operation Successful"
        },
        {
        "codigoFormaPagamento": 171,
        "valor": 800,
        "valorDesconto": 0,
        "parcelas": 1,
        "autorizacao": "20307",
        "codigoTransacaoOperadora": "6",
        "dataAprovacaoOperadora": "2018-02-21 11:50:22",
        "numeroComprovanteVenda": "0221115022682",
        "mensagemVenda": "Operation Successful"
        }
]
}
```
