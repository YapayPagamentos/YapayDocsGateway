# Cancelando recorrência

<span class="put">PUT</span>

API para cancelamento da recorrência.
Esta funcionalidade cancelará apenas o agendamento das futuras recorrências, não cancelará as cobranças já realizadas.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-recorrencia.md?id=cancelar-recorrencia)

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia
Produção |https://gateway.yapay.com.br/checkout/api/v3/recorrencia


> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia/10000000000000/2/cancelar
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
    "recorrencia": {
    "estabelecimento": "1000000000000",
    "numeroRecorrencia": 2,
    "codigoFormaPagamento": 170,
    "valor": 13000,
    "numeroCobrancaTotal": 3,
    "numeroCobrancaRestantes": 3,
    "status": 0,
    "mensagem": "Recorrência cancelada com sucesso.",
    "numeroPedido": null,
    "statusTransacao": null,
    "autorizacao": null,
    "codigoTransacaoOperadora": null,
    "dataAprovacaoOperadora": null,
    "numeroComprovanteVenda": null,
    "mensagemVenda": null
    }
```
