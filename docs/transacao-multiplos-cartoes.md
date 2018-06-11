# Transação com múltiplos cartões

Através desta estrutura é possível o envio de mais de um cartão de crédito para aprovação em uma mesma transação, dividindo o valor total do pedido entre os cartões.

> **Particulariedades**

* Disponível apenas no plano Corporativo;
* Disponível apenas para cartões de cŕedito na modalidade WS.

> **Exemplo de envio de JSON**

```curl
-request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
--header "Content-Type: application/json"
--curl -u usuario:senha
--data-binary
{
"codigoEstabelecimento" : 1000000000000,
"codigoFormaPagamento" : 999,
"dadosMultiplosCartoes": [
    {
        "nomePortador": "CARTAO 1",
        "numeroCartao": "0000000000000001",
        "codigoSeguranca": "321",
        "dataValidade": "12/2024",
        "codigoFormaPagamento": 170,
        "parcelas": 1,
        "valor": 500
    },
    {
        "nomePortador": "CARTAO 2",
        "numeroCartao": "0000000000000001",
        "codigoSeguranca": "123",
        "dataValidade": "12/2022",
        "codigoFormaPagamento": 171,
        "parcelas": 1,
        "valor": 800
    }
],
"transacao" : {
    "numeroTransacao" : 1234,
    "idioma" : 1
},
"itensDoPedido" : [
{
    "codigoProduto" : 1,
    "codigoCategoria" : 1,
    "quantidadeProduto" : 1,
    "valorUnitarioProduto" : 2000
}
],
"dadosCobranca" : {
    "tipoCliente" : 1,
    "nome" : "Teste 123",
    "documento" : "123.123.123-12"

}
}
```

> **Exemplo de retorno JSON**

```curl
--header "Content-Type: application/json"
{
"numeroTransacao": 1234,
"codigoEstabelecimento": "1000000000000",
"multiploCartao": 1,
"statusTransacao": 1,
"detalhesMultiploCartao":    [
        {
        "codigoFormaPagamento": 170,
        "valor": 500,
        "valorDesconto": 0,
        "parcelas": 1,
        "autorizacao": "513663",
        "codigoTransacaoOperadora": "6",
        "dataAprovacaoOperadora": "2018-02-21 11:50:21",
        "numeroComprovanteVenda": "0221115021704",
        "mensagemVenda": "Operation Successful"
        },
        {
        "codigoFormaPagamento": 171,
        "valor": 800,
        "valorDesconto": 0,
        "parcelas": 1,
        "autorizacao": "20307",
        "codigoTransacaoOperadora": "6",
        "dataAprovacaoOperadora": "2018-02-21 11:50:22",
        "numeroComprovanteVenda": "0221115022682",
        "mensagemVenda": "Operation Successful"
        }
]
}
```
