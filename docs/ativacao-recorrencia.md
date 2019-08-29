# Ativação recorrência

<span class="put">PUT</span>

API para ativação da recorrência. Esta funcionalidade ativará a recorrência já cadastrada e que se encontra cancelada para o agendamento das futuras recorrências.


> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia
Produção |https://gateway.yapay.com.br/checkout/api/v3/recorrencia


> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://gateway.yapay.com.br/checkout/api/v3/recorrencia/agg/«codigoEstabelecimento»/«numeroRecorrencia»/ativar
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
 {
    "tipo": "REST",
    "periodicidade": "MENSAL",
    "codigoEstabelecimento": "1000000000001",
    "numero": 22348,
    "ativo": true,
    "dataCriacao": "2019-04-05 12:53:57",
    "formaPagamento": 170,
    "formaPagamentoDescricao": "Visa Cielo API",
    "valor": 13000,
    "quantidadeCobranca": 0,
    "numeroCobrancaRestantes": -1,
    "diaCobranca": 20,
    "mesCobranca": 0,
    "primeiraCobranca": 0,
    "ultimaCobranca": null,
    "detalhes": null,
    "logs": null,
    "periodicidadeCodigo": 3
}
```
