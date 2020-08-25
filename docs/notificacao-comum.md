# Venda comum

O sistema de campainha existe para notificar o estabelecimento sobre uma atualização de status na transação. Toda vez que ocorre qualquer alteração de status em uma transação, é feita uma chamada via <span class="post">POST</span> ao campo “urlCampainha” (enviada como parâmetro junto da transação), essa chamada enviará alguns dados que identificarão a transação, e assim o estabelecimento saberá em qual transação houve uma mudança de status.

Importante lembrar que a chamada de campainha não informa qual o status atual da transação e apenas que houve uma alteração, sendo assim, o estabelecimento deve realizar uma [consulta](api-consultar-transacao.md) para verificar com mais detalhes a situação atual da transação.

Estabelecimentos que utilizam captura automática, não receberão a notificação dos primeiros status ( Pago e capturado ou Não Pago), já que os mesmos serão retornados no primeiro momento, logo após o envio da transação ao Gateway.
Portanto, nestes casos, a campainha será acionada para eventos efetuados após esta etapa, um cancelamento do pedido por exemplo.

`Caso a URL de campainha estiver em HTTPS, informar ao Suporte Yapay, servicedesk@yapay.com.br`

**Importante que a URL de notificação da loja retorne ao Gateway algum código do grupo 200**



> **Detalhamento dos campos**

Campo | Descrição | Tipo
----- | --------- | -------
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico
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
"numeroTransacao=123&codigoEstabelecimento=1000000000000&campoLivre1=A&campoLivre2=B&campoLivre3"
```
