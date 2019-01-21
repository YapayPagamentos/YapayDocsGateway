Informações sobre a contratação e particulariedades da Adquirente Bin-First Data.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta adquirente.

> **CONTRATAÇÃO**

Contratando a solução da BIN para e-commerce será possível oferecer na sua loja:

* Cartão de crédito Visa;
* Cartão de crédito MasterCard;
* Cartão de crédito Cabal;
* Cartão de crédito Hipercard;
* Cartão de crédito Elo;
* Cartão de cŕedito Sorocred;
* Cartão de crédito Hiper.

Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da BIN no Gateway:

* Store Id;
* User Id;
* Password;
* Arquivo do certificado BIN;
* Senha do certificado;
* Terminal ID.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://www.bin.com.br/content/bin/pt_br/home/peca-ja/solicite-seu-credenciamento.html).

> **PARTICULARIEDADES**

* Para esta modalidade é necessário certificado SSL de segurança 2048 bits;
* Integração apenas na modalidade WebService.

> **CONFIGURAÇÃO GATEWAY**

[Acesse aqui](https://atendimento.yapay.com.br/hc/pt-br/articles/360005036074-Cart%C3%A3o-de-Cr%C3%A9dito-BIN) para informações sobre como configurar a BIN no Gateway Yapay.

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
        "codigoFormaPagamento" : 381,
        "transacao" : {
            "numeroTransacao" : 123,
            "valor" : 500000,
            "parcelas" : 1,
            "idioma" : 1
        },
        "dadosCartao" : {
            "nomePortador" : "Teste Teste",
            "numeroCartao" : "5547220000000102",
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
        "codigoFormaPagamento": 381,
        "valor": 100,
        "valorDesconto": 0,
        "parcelas": 1,
        <!--Status que deverá ser tratado pelo eCommerce-->
        "statusTransacao": 1,
        <!--Código de autorização-->
        "autorizacao": "657409",
        <!--Código retorno Bin-->
        "codigoTransacaoOperadora": "0",
        <!--Data retorno adquirente-->
        "dataAprovacaoOperadora": "20/10/2030 16:36:43",
        <!--TID-->
        "numeroComprovanteVenda": "Y:657409:4514266711:PPX :632615",
        "nsu": "",
        <!--Mensagem adquirente-->
        "mensagemVenda": "APPROVAL 000009113",
        "urlPagamento": "14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
        "cartoesUtilizados": ["554722******0102"]
       }
```
