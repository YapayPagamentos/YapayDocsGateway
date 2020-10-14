# Criando recorrência

<span class="post">POST</span>

API para cadastro de um pagamento recorrente.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia
Produção |https://gateway.yapay.com.br/checkout/api/v3/recorrencia

## Recorrência com cartão de crédito

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-recorrencia.md?id=criação-de-recorrencia)


> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
  {
      "estabelecimento": "1000000000000",
      "recorrencia": {
          "formaPagamento": 170,
          "numeroRecorrencia": 2,
          "valor": 13000,
          "modalidade": "1",
          "periodicidade": "3",
          "urlNotificacao": "http://teste.com.br/campainha",
          "processarImediatamente": "true",
          "quantidadeCobrancas": "0",
          "dataPrimeiraCobranca": "30/10/2019",

          "dadosCobranca": {
              "nomeComprador": "Teste Recorrencia",
              "documento": "12312312312",
              "emailComprador": "teste@teste.com.br",
              "tipoCliente": "1",
              "telefone": {
                  "tipoTelefone": "1"
              }
          },
          "dadosCartao": {
              "nomePortador": "Teste",
              "numeroCartao": "0000000000000001",
              "codigoSeguranca": "287",
              "dataValidade": "01/2030"
          }
      }
  }
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
  "recorrencia": {
      "estabelecimento": "1000000000000",
      "numeroRecorrencia": 2,
      "codigoFormaPagamento": 170,
      "valor": 13000,
      "numeroCobrancaTotal": 0,
      "numeroCobrancaRestantes": -1,
      "status": 0,
      "mensagem": "Processamento realizado com sucesso.",
      "numeroPedido": 20001,
      "statusTransacao": 1,
      "autorizacao": "123456",
      "codigoTransacaoOperadora": "00",
      "dataAprovacaoOperadora": "2020-09-23 16:57:32",
      "numeroComprovanteVenda": "1006993069000891071A",
      "mensagemVenda": "Operation Success"
  }
```

## Recorrência com boleto bancário

Nesse modelo de recorrência, a Yapay enviará a toda cobrança um email ao comprador com o link para efetuar a geração do boleto bancário.

O template do email de cobrança pode ser personalizado de acordo com a necessidade do estabelecimento, para isto basta realizar o cadastro através da nossa [API](checkout2-layout).
Caso o estabelecimento não tenha layout cadastrado, o email será enviado em formato padrão Yapay

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-recorrencia.md?id=criação-de-recorrencia-boleto)


> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
  {
      "estabelecimento": "1000000000000",
      "recorrencia": {
          "formaPagamento": 29,
          "numeroRecorrencia": 3,
          "valor": 20000,
          "modalidade": "3",
          "periodicidade": "3",
          "urlNotificacao": "http://teste.com.br/campainha",
          "processarImediatamente": "true",
          "quantidadeCobrancas": "0",
          "dataPrimeiraCobranca": "30/10/2021",

       "dadosCobranca" : {
          "tipoCliente": "1",
          "nomeComprador" : "Teste 123",
          "emailComprador" : "teste@teste.com",
          "documento" : "123.123.123-12",
          "enderecoComprador" : "Rua",
          "numeroEnderecoComprador" : "123",
          "cepComprador" : "12345-678",
          "bairroComprador" : "Bairro",
          "cidadeComprador" : "Cidade",
          "estadoComprador" : "SP",
          "telefone": {
            "tipoTelefone": "1"
            },
          }
      }
  }
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
  "recorrencia": {
      "estabelecimento": "1000000000000",
      "numeroRecorrencia": 3,
      "codigoFormaPagamento": 28,
      "valor": 20000,
      "numeroCobrancaTotal": 0,
      "numeroCobrancaRestantes": -1,
      "status": 0,
      "mensagem": "Processamento realizado com sucesso.",
      "numeroPedido": 30001,
      "statusTransacao": 5,
      "autorizacao": "",
      "codigoTransacaoOperadora": "0",
      "dataAprovacaoOperadora": "",
      "numeroComprovanteVenda": "",
      "mensagemVenda": "Checkout Yapay",
      "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1602000c2d2-a1br877687871-6767868678"
  }
```
