# 3DS 2.0

Este é um novo padrão de autenticação dos meios de pagamento no mundo de eCommerce, que tem como objetivo minimizar o índice de fraude sem prejudicar a taxa de conversão.
O novo padrão é capaz de analisar dezenas de variáveis que são utilizadas como critérios para determinar se um comprador é de fato o portador cartão, permitindo em alguns casos, a autenticação silenciosa, ou seja, não há redirecionamentos para página do banco emissor.

* No momento está disponível no Gateway apenas o 3DS 2.0 da adquirente Cielo.

## CIELO ECOMMERCE 3.0

Primeiramente, seguir os passos abaixo para realizar a autenticação e com o retorno realizar a autorização da transação.

Conforme documentação [Cielo](https://developercielo.github.io/manual/emv3ds#autentica%C3%A7%C3%A3o-3ds-2.0) para utilização do 3DS 2.0 é necessário da inclusão de um script na página de checkout da loja virtual.
Esse script enviará para o serviço de autenticação os inputs do formulário marcados com as classes "bpmpi_*" e, dependendo dos campos enviados, abrirá um modal para fornecimento da senha do portador do cartão (com desafio) ou devolverá para página o resultado da autenticação (sem desafio).

Para habilitar esta função junto ao Gateway será necessário os seguintes dados abaixo: 

* Merchant ID
* Merchant Key
* Código do estabelecimento do Cielo 3.0
* Nome do estabelecimento na Cielo
* Código da categoria
* Usuário/Senha para Basic Authentication

Após estas configurações no Gateway, o estabelecimento receberá o Acess Token para seguir com o processamento da autenticação.


> **Recuperando o Token Acess**

**REQUEST**

<span class="put">PUT</span>

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/3ds/«codigoEstabelecimento»/«código forma de pagamento»/token
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/«codigoEstabelecimento»/«código forma de pagamento»/token

**RESPONSE**

{
    <!--tempo de expiração do token acess-->
    "expiration": "14/06/2019 09 16 08",<br>
    <!--Token Acess-->
    "token": "eyJ0eXAiOiJKV...hn_35nsc"
}

> **Repassando dados ao Gateway**

Antes que haja o submit, preferencialmente no carregamento da página, a função "bpmpi_config" do JS Cielo deve ser definida com as ações a serem tomadas após a resposta da autenticação e informar se o ambiente é produção "PRD" ou sandbox "SDB".
No submit do formulário de pagamento as funções "bpmpi_load" e "bpmpi_authenticate" de BP.Mpi.3ds20.min.js devem ser executadas na sequência e o script se encarregará da autenticação.

A resposta de sucesso do script terá o retorno com as campos:

{
   Cavv: "",<br>
   Xid: "",<br>
   Eci: "",<br>
   Version: "",<br>
   ReferenceId: ""<br>
}

Esta resposta deve ser enviada ao Gateway Yapay através do nó <camposExtras>, com <chave> e <valor>

Chave | Valor
-------- | ------
35784110 | 'true' (indicador de autenticação externa, valor fixo)
35784118 | 'SUCCESS' (indicador de autenticação bem sucedida, valor fixo)
35784111 | Cavv retornado pelo Script
35784112 | Xid retornado pelo Script
35784113 | Eci retornado pelo Script
35784114 | Version retornado pelo Script
35784115 | ReferenceId retornado pelo Script

> **Exemplo de envio em JSON**

```curl
curl
        --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
        --header "Content-Type: application/json"
        --user usuario:senha
        --data-binary
        {
        "codigoEstabelecimento" : 1000000000000,
        "codigoFormaPagamento" : 171,
        "transacao" : {
            "numeroTransacao" : 123,
            "valor" : 100,
            "parcelas" : 1,
            "idioma" : 1
        },
        "dadosCartao" : {
            "nomePortador" : "Teste Teste",
            "numeroCartao" : "0000000000000001",
            "codigoSeguranca" : "123",
            "dataValidade" : "12/2030"
        },
        "itensDoPedido" : [
        {
            "quantidadeProduto" : 1,
            "valorUnitarioProduto" : 100
        }
        ],
        "dadosCobranca" : {
            "nome" : "Teste Integração",
            "documento" : "12312312312"
        },
        "camposExtras":[
        {
            "chave":35784110,
            "valor":"true"
        },
        {
            "chave":35784118,
            "valor":"SUCCESS"
        },
        {
            "chave":35784111,
            "valor":"AAABAWFlmQAAAABjRWWZEEFgFz+="
        },
        {
            "chave":35784112,
            "valor":"SG1vdTZrbzNhS1M5Z0VYMWYxbDA="
        },
        {
            "chave":35784113,
            "valor":05
        },
        {
            "chave":35784114,
            "valor":1
        },
        {
            "chave":35784115,
            "valor":"1abbabe0-ac89-45c7-90f6-2e7e9fa5a936"
        }
       ]
      }
```

> **Exemplo de retorno em JSON**

```curl
        --header "Content-Type: application/json"
        {
        "numeroTransacao": 123,
        "codigoEstabelecimento": "1000000000000",
        "codigoFormaPagamento": 171,
        "valor": 2000,
        "valorDesconto": 0,
        "parcelas": 1,
        <!--Status que deverá ser tratado pelo eCommerce-->
        "statusTransacao": 1,
        <!--Código de autorização-->
        "autorizacao": "123456",
        <!--Código erro em caso de negação-->
        "codigoTransacaoOperadora": "0",
        <!--Data retorno adquirente-->
        "dataAprovacaoOperadora": "24/05/2030",
        <!--TID-->
        "numeroComprovanteVenda": "10069930690009F2122A",
        <!--NSU-->
        "nsu": "428706",
        <!--Mensagem adquirente-->
        "mensagemVenda": "Operation Success",
        "urlPagamento": "14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
        "cartoesUtilizados": ["000000*******0001"]
        }
```


