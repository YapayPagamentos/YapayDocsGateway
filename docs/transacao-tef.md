# Introdução

O Yapay disponibiliza a integração com diversas Instituições Financeiras através de uma única integração via API em RESTful.

![API Transação Yapay](/images/transacao_tef.png "API Yapay")

A comunicação com o Yapay Gateway ocorrerá após a finalização do pagamento no Checkout do Ecommerce, de forma transparente para o consumidor. Ao ser finalizado o pagamento dentro da loja, o Ecommerce deverá consumir os serviços WebServices do Yapay encaminhando as informações da compra de acordo com a estrutura que será apresentada nesta documentação.
Recebendo a requisição, o Gateway retornará uma URL para redirecionamento a página do banco e finalização da transferência.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

## Criando uma transação

<span class="post">POST</span>

Estrutura para geração de transferências eletrônicas.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-transferencia.md)

> **Particulariedades**

* O campo `<estado>` deve ser preenchido apenas com a sigla do Estado;
* O campo `<numeroTransacao>` deve conter até 8 dígitos;
* Importante a utilização do recurso de Campainha, para atualização dos pedidos no Ecommerce;

> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
  {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 16,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "valorDesconto" : 0,
        "parcelas" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "urlResultado" : "http://seusite.com.br/retorno",
        "ip" : "192.168.12.110",
        "idioma" : 1,
        "dataVencimentoBoleto":"13/12/2030"
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
          }
    }
  }
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  {  "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 16,
    "valor": 2000, 
    "valorDesconto": 0, 
    "parcelas": 1, 
    "statusTransacao": 5,
    "autorizacao": "0",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "", 
    "numeroComprovanteVenda": "", 
    "nsu": "",
    "mensagemVenda": "",
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoIatuShopLine/PagamentoItauShopLine.do?cod=132971582229c00506d-e84d-4526-b902-92190d5aa808"
  }
```
