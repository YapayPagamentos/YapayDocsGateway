# Transação com análise de fraude

<span class="post">POST</span>

A utilização desta estrutura é indicada para envio de pedidos com a forma de pagamento Checkout Yapay, onde o estabelecimento possui contratação de umas das empresas de análise de risco integradas pelo Yapay, sendo elas ClearSale (modalidades: Total/Total Garantido, Application, ID e Start), FControl (modalidade Fila), Konduto e antifraude da Adquirente Rede.


Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-checkout2.md?id=transação-com-análise-de-fraude)

`Contratação a parte com as empresas de analise de fraude`
<br>

> **Exemplo de envio em JSON**

```curl
 --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
    --header "Content-Type: application/json"
    --curl -u usuario:senha
    --data-binary
    {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 997,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "valorDesconto" : 0,
        "parcelas" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "ip" : "192.168.12.110",
        "idioma" : 1
    },
    "checkout": {
        "versao" : 2,
        "formasPagamento" : [170, 171, 29]
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
        "documento" : "12323434545",
        "email" : "yapay@yapay.com.br",
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
  {
       "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/yp/?tx=1570627364596ca6a0a1d-90cb-4411-998a-6299c1c5e4"
  }
```

**Assim que a transação for finalizada, Yapay irá notificar a loja através da campainha.

> **Exemplo página de Checkout**

Ao enviar a requisição ao Gateway, será retornado a URL da página de Checkout para redirecionar o cliente do site. Abaixo segue exemplo de nossa página de Checkout:

![API Transação Yapay](/images/checkout2.png "API Yapay")
