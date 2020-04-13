# Alterar status

<span class="put">PUT</span>

Através desta API é possível alterar o status de uma transação.
<br>**Lembrando que a alteração de status não realiza nenhuma ação sobre a venda, exemplo, uma transação que foi alterada para status Cancelado, não será cancelada na Adquirente, para isto é necessário acionar a API de cancelamento.**

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/status/«idNovoStatus»
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«numeroPedido»/status/«idNovoStatus»

*[Consulte os ids dos status](tabela-status.md)*

> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/1000000000000/1234/status/13
  --header "Content-Type: application/x-www-form-urlencoded"
  --user usuario:senha
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/x-www-form-urlencoded"
  {
    "mensagem": "OK"
}
```
