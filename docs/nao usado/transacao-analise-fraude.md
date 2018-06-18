# Transação com análise de fraude

A utilização desta estrutura é indicada para envio de pedidos com a forma de pagamento cartão de crédito, onde o estabelecimento possui contratação de umas das empresas de análise de risco integradas pelo Yapay, sendo elas ClearSale (modalidades: Total/Total Garantido, Application, ID e Start) e FControl (modalidade Fila).

`Contratação a parte com as empresas ClearSale e FControl`
<br>

> **Exemplo de envio em JSON**

```curl
 --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
    --header "Content-Type: application/json"
    --curl -u usuario:senha
    --data-binary
    {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 190,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "valorDesconto" : 0,
        "parcelas" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "ip" : "192.168.12.110",
        "idioma" : 1
    },
    "dadosCartao" : {
        "nomePortador" : "Teste Teste",
        "numeroCartao" : "4002479199570736",
        "codigoSeguranca" : "132",
        "dataValidade" : "12/2020"
    },
    "itensDoPedido" : [
    {
        "codigoProduto" : 1,
        "nomeProduto" : "Produto 1",
        "codigoCategoria" : 1,
        "nomeCategoria" : "categoria",
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 2000
    }
    ],
    "dadosCobranca" : {
        "codigoCliente" : 1,
        "tipoCliente" : 1,
        "nome" : "Teste 123",
        "email" : "teste@teste.com",
        "dataNascimento" : "10/01/1975",
        "sexo" : "M",
        "documento" : "123.123.123-12",
        "endereco" : {
            "logradouro" : "Rua",
            "numero" : "123",
            "complemento" : "",
            "cep" : "12345-678",
            "bairro" : "Bairro",
            "cidade" : "Cidade",
            "estado" : "SP",
            "pais" : "BR"
            },
        "telefone" : [
            {
            "tipoTelefone" : "1",
            "ddi" : "55",
            "ddd" : "12",
            "telefone" : "1234-5678"
            }
        ]
    },
    "dadosEntrega" : { 
        "nome" : "Teste 123",
        "endereco" : {
            "logradouro" : "Rua",
            "numero" : "123",
            "complemento" : "",
            "cep" : "12345-678",
            "bairro" : "Bairro",
            "cidade" : "Cidade",
            "estado" : "SP",
            "pais" : "BR"
            },
        "telefone" : [
            {
            "tipoTelefone" : "1",
            "ddi" : "55",
            "ddd" : "12",
            "telefone" : "1234-5678"
            }
        ]
    }
    }
```

> **Exemplo de retorno JSON**

```curl
--header "Content-Type: application/json"
    {  "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 190,
    "valor": 2000, 
    "valorDesconto": 0, 
    "parcelas": 1, 
    "statusTransacao": 1,
    "autorizacao": "12260",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "24/05/2030", 
    "numeroComprovanteVenda": "10117092009151900057", 
    "nsu": "428706",
    "mensagemVenda": "00 - Success",
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/PagamentoCielo.do?cod=14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66", 
    "cartoesUtilizados": ["400247******0736"]
    }
```

