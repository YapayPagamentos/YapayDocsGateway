# Pagamento

<span class="post">POST</span>

API para pagamento utilizando token.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-oneclick.md?id=pagamento-oneclick)

> **Exemplo de envio em JSON cartão de cŕedito**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick/1514483826864c3149224-67db-4557-8950-6a80f708c1c5/autorizar
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
  {
      "codigoEstabelecimento" : 1000000000000,
      "transacao" : {
          "numeroTransacao" : 123,
          "valor" : 100,
          "parcelas" : 1,
          "idioma" : 1
      },
      "dadosCartao" : {
          "codigoSeguranca" : "123"
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
          "tipoCliente" : 1
      }
  }
```

> **Exemplo de retorno em JSON cartão de cŕedito**

```curl
--header "Content-Type: application/json
  {
    "numeroTransacao": 123,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 170,
    "valor": 100,
    "valorDesconto": 0,
    "parcelas": 1,
    "oneClick": 1,
    "token": "1514483826864c3149224-67db-4557-8950-6a80f708c1c5",
    "statusTransacao": 1,
    "autorizacao": "892358",
    "codigoTransacaoOperadora": "6",
    "dataAprovacaoOperadora": "2018-01-10 10:18:43",
    "numeroComprovanteVenda": "0110101834052",
    "mensagemVenda": "Operation Successful"
  }
```

> **Exemplo de envio em JSON cartão de débito**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick/1514483826864c3149224-67db-4557-8950-7a00f708c1c5/autorizar
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
  {
      "codigoEstabelecimento" : 1000000000000,
      "transacao" : {
          "numeroTransacao" : 1234,
          "valor" : 100,
          "parcelas" : 1,
          "idioma" : 1
      },
      "dadosCartao" : {
          "codigoSeguranca" : "123"
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
          "tipoCliente" : 1
      }
  }
```

> **Exemplo de retorno em JSON cartão de débito**

```curl
--header "Content-Type: application/json
  {
    "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 179,
    "valor": 100,
    "valorDesconto": 0,
    "parcelas": 1,
    "oneClick": 1,
    "token": "1514483826864c3149224-67db-4557-8950-7a00f708c1c5",
    "statusTransacao": 8,
    "autorizacao": "0",
    "codigoTransacaoOperadora": "1",
    "dataAprovacaoOperadora": "2018-01-10 10:18:43",
    "numeroComprovanteVenda": "0110101834010",
    <--Redirecionar o cliente para a URL abaixo, afim de realizar a autenticacao-->
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoVisaElectron.do?cod=15434085369452f4e4342-e6e2-4ef9-ab62-17d24a82f5dc"
  }
```

