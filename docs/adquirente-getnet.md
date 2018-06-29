Informações sobre a contratação e particulariedades da Adquirente GetNet.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta adquirente.

> **CONTRATAÇÃO**

Contratando a solução da GetNet para e-commerce será possível oferecer na sua loja:

* Cartão de crédito VISA;
* Cartão de crédito MasterCard;


Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da GETNET no Gateway:

* Merchant Id;
* Terminal Id;
* Usuário;
* Senha.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://site.getnet.com.br/#/solucoes/e-commerce).

> **PARTICULARIEDADES**

* Para esta modalidade é necessário certificado SSL de segurança 2048 bits;
* Integração apenas na modalidade WebService.

> **EXEMPLOS**

**REQUISIÇÃO**

```curl
curl
        --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
        --header "Content-Type: application/json"
        --user usuario:senha
        --data-binary
        {
        "codigoEstabelecimento" : 1000000000000,
        "codigoFormaPagamento" : 271,
        "transacao" : {
            "numeroTransacao" : 123,
            "valor" : 500000,
            "parcelas" : 1,
            "idioma" : 1
        },
        "dadosCartao" : {
            "nomePortador" : "Teste Teste",
            "numeroCartao" : "5453010000083303",
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
        }
       }
```

**RESPOSTA**

```curl
        --header "Content-Type: application/json"
        {
        "numeroTransacao": 123,
        "codigoEstabelecimento": "1000000000000",
        "codigoFormaPagamento": 271,
        "valor": 100,
        "valorDesconto": 0,
        "parcelas": 1,
        <!--Status que deverá ser tratado pelo eCommerce-->
        "statusTransacao": 1,
        <!--Código de autorização-->
        "autorizacao": "1234",
        <!--Código retorno GetNet-->
        "codigoTransacaoOperadora": "0",
        <!--Data retorno adquirente formato mmdd-->
        "dataAprovacaoOperadora": "1017",
        <!--TID-->
        "numeroComprovanteVenda": "1662429594",
        "nsu": "",
        <!--Mensagem adquirente-->
        "mensagemVenda": "CAPTURED",
        "urlPagamento": "14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
        "cartoesUtilizados": ["545301******3303"]
        }
```
