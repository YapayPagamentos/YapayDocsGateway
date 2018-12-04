# Venda recorrente

Neste fluxo de recorrência, o estabelecimento receberá a campainha informando qual recorrência houve a cobrança e, depois disto, deverá acionar a [consulta Recorrente](api-consultar-recorrencia.md) para receber o número do pedido, e assim, acionar a [consulta Transacao](api-consultar-transacao.md) para recebimento do status.

`Caso a URL de campainha estiver em HTTPS, informar ao Suporte Yapay, servicedesk@yapay.com.br`

> **Detalhamento dos campos**

Campo | Descrição | Tipo
----- | --------- | -------
numeroRecorrencia|	Código que identifica a recorrência dentro do Yapay|	Numérico
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico
campoLivre1|	Campo Livre 1|	Alfa Numérico
campoLivre2|	Campo Livre 2|	Alfa Numérico
campoLivre3|	Campo Livre 3|	Alfa Numérico
campoLivre4|	Campo Livre 4|  Alfa Numérico
campoLivre5|	Campo Livre 5|	Alfa Numérico


> **Exemplo de chamada**


```curl
curl
  --request POST https://sualoja.com.br/campainha
  --header "Content-Type: application/x-www-form-urlencoded"
  --data-binary
"numeroRecorrencia=1&codigoEstabelecimento=1000000000000&campoLivre1=A&campoLivre2=B&campoLivre3=C&campoLivre4=D&campoLivre5=E"
```
