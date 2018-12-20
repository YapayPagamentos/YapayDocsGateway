# Criando recorrência

<span class="post">POST</span>

API para cadastro de um pagamento recorrente.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-recorrencia.md?id=criação-de-recorrencia)

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia
Produção |https://gateway.yapay.com.br/checkout/api/v3/recorrencia


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
      "dataAprovacaoOperadora": "30/06/2018",
      "numeroComprovanteVenda": "1006993069000891071A",
      "mensagemVenda": "Operation Success"
  }
```
