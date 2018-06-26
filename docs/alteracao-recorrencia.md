# Alterando recorrência

<span class="put">PUT</span>

API para alteração do dia de cobrança e/ou valor de uma recorrência já cadastrada no Gateway.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-recorrencia.md?id=alteracão-recorrencia)

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia/agg/«codigoEstabelecimento»/«numeroRecorrencia»/atualizar
Produção |https://gateway.yapay.com.br/checkout/api/v3/recorrencia/agg/«codigoEstabelecimento»/«numeroRecorrencia»/atualizar

> **Exemplo de envio em JSON - alteração dia**

```curl
curl
   --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia/agg/10000000000000/2/atualizar
   --header "Content-Type: application/json"
   --user usuario:senha
   --data-binary
   {
     "diaCobranca": 20
   }
```

> **Exemplo de retorno em JSON**

```curl
 {
      "tipo": "REST",
      "periodicidade": "MENSAL",
      "codigoEstabelecimento": "10000000000000",
      "numero": 2,
      "ativo": true,
      "dataCriacao": "02/05/2018 13:22:25",
      "formaPagamento": 170,
      "formaPagamentoDescricao": "Visa Cielo API",
      "valor": 13000,
      "quantidadeCobranca": 0,
      "diaCobranca": 20,
      "mesCobranca": 0,
      "primeiraCobranca": 0,
      "detalhes": null,
      "logs": null,
      "periodicidadeCodigo": 3
 }
```

> **Exemplo de envio em JSON - alteração de valor**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/recorrencia/agg/10000000000000/2/atualizar
  --header "Content-Type: application/json"
  --user usuario:senha .........
  --data-binary
    {
      "valor": 20000
    }
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
    {
      "tipo": "REST",
      "periodicidade": "MENSAL",
      "codigoEstabelecimento": "10000000000000",
      "numero": 2,
      "ativo": true,
      "dataCriacao": "02/05/2018 13:22:25",
      "formaPagamento": 170,
      "formaPagamentoDescricao": "Visa Cielo API",
      "valor": 20000,
      "quantidadeCobranca": 0,
      "diaCobranca": 20,
      "mesCobranca": 0,
      "primeiraCobranca": 0,
      "detalhes": null,
      "logs": null,
      "periodicidadeCodigo": 3
    }
```
