Informações sobre a contratação e particulariedades da Adquirente Cielo.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta adquirente.

## Modalidade WebService

> **CONTRATAÇÃO**

Contratando a solução da CIELO API 3.0 para e-commerce será possível oferecer na sua loja:

* Vendas de cŕedito autenticadas (Bandeiras Visa e MasterCard);
<br>
* Cartão de crédito Visa;
* Cartão de crédito MasterCard;
* Cartão de crédito Amex;
* Cartão de crédito Aura;
* Cartão de crédito Diners;
* Cartão de crédito Discover;
* Cartão de crédito Elo;
* Cartão de crédito JCB;
* Cartão de crédito HiperCard;
* Cartão de débito Maestro;
* Cartão de débito Visa Electron;

Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da CIELO no Gateway:

* Merchant ID;
* Merchant Key;

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://formularios2.cielo.com.br/form1b/api-cielo-convencional/passo-1).

> **PARTICULARIEDADES**

* Para esta modalidade é necessário certificado SSL de segurança 2048 bits;
* Caso o campo `<codigoSeguranca>` não for enviado ou for enviado com “000”, a transação será encaminhada a Cielo como modelo “Recorrente”, onde este campo não é obrigatório. Lembrando que para esta utilização é preciso habilitar junto a Adquirente. Salientamos que a conversão de seu estabelecimento pode diminuir;
* Esta operadora de cartão permite cadastrar uma informação para visualização na fatura dos clientes quando realizarem compras em sua loja, funcionalidade chamada de SoftDescriptor. Esta deverá possuir até 13 caracteres. Caso queira utilizar, envie ao Suporte Yapay o nome desejado para configuração em seu estabelecimento. Também é possível o envio do SoftDescriptor por pedido, para isto solicite ao Suporte a ativação e envie a informação no `<campoLivre4>` de cada transação;
* Para transações com cartão de débito ou autenticada, o eCommerce deverá redirecionar o consumidor para a `<urlPagamento>`, onde o mesmo deverá incluir sua senha ou token no ambiente do banco emissor. Apenas após esta etapa, a transação será concluída;
* Para utilizar pagamentos recorrentes é preciso ativar junto ao Cielo Ecommerce a recorrência na filiação do estabelecimento.
* Abaixo seguem bancos e bandeiras disponíveis para cartão de débito:

MASTERCARD | VISA
---------- | --------
Bradesco|	Bradesco
Banco do Brasil|	Banco do Brasil
Santander|	Santander
Itaú|	Itaú
CitiBank|	CitiBank
BRB|	N/A
Caixa|	N/A
BancooB|	N/A

> **CONFIGURAÇÃO GATEWAY**

[Acesse aqui](https://atendimento.yapay.com.br/hc/pt-br/articles/360005085973-Cart%C3%A3o-de-Cr%C3%A9dito-e-D%C3%A9bito-Cielo) para informações sobre como configurar Cielo WebService no Gateway Yapay.

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
        }
      }
```

**RESPOSTA**

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

## Cielo Checkout

> **CONTRATAÇÃO**

Contratando a solução da CIELO CHECKOUT para e-commerce será possível oferecer os seguintes meios de pagamento na sua loja:

* Cartão de crédito Visa;
* Cartão de crédito MasterCard;
* Cartão de crédito Amex;
* Cartão de crédito Aura;
* Cartão de crédito Diners;
* Cartão de crédito Discover;
* Cartão de crédito Elo;
* Cartão de crédito JCB;
* Cartão de crédito HiperCard;
* Cartão de débito Maestro;
* Cartão de débito Visa Electron;

Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da CIELO no Gateway:

* Código de filiação;
* Merchant ID;
* URL de redirecionamento;

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://formularios2.cielo.com.br/form1b/checkout-cielo-convencional/passo-1).

> **PARTICULARIEDADES**

* O eCommerce deverá redirecionar o consumidor para a URL retornada no campo `<urlPagamento>`;
* Importante a utilização da campainha para atualização de status no eCommerce após finalização do pagamento;
* O eCommerce enviará um único código ao Gateway relacionado ao meio de pagamento Checkout (52) e após a abertura da URL o consumidor escolherá a bandeira de cartão;
* Necessário algumas configurações no painel Cielo. Passo a passo no próximo tópico deste documento;
* Abaixo seguem bancos e bandeiras disponíveis para cartão de débito:

MASTERCARD | VISA
---------- | --------
Bradesco|	Bradesco
Banco do Brasil|	Banco do Brasil
Santander|	Santander
Itaú|	Itaú
CitiBank|	CitiBank
BRB|	N/A
Caixa|	N/A
BancooB|	N/A

> **CONFIGURAÇÃO PAINEL CIELO**

Etapas para configuração

<br>Gerenciador Cielo:
![Gerenciador](/images/tmbackoffice.png "Gerenciador Cielo")

<br>Configuração do tempo de expiração da página de Checkout:
![Gerenciador](/images/exp_cielo.png "Gerenciador Cielo")

**EM SANDBOX** 

1- Acesse o gerenciador Cielo
<br>2- Clique na aba “Configurações”
<br>3- Primeiramente habilite em “Modo de Teste”
<br>4- Inclua as URLs abaixo:

<br>Substituir o valor 10000000000 pelo código de estabelecimento Yapay

Nome do campo|	URL
------------ | ---------
URL Retorno|	https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/RetornoCheckout?codE=10000000000&acao=retorno
URL Notificação|	https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/NotificacaoCheckout?codE=10000000000&acao=notificacao
URL de Mudança de Status|	https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/NotificacaoCheckout?codE=10000000000&acao=mudancaStatus

**EM PRODUÇÃO**

1- Acesse o gerenciador Cielo
<br>2- Clique na aba “Configurações” –> “Configurações da loja”
<br>3- Primeiramente desabilite em “Modo de Teste”
<br>4- Inclua as URLs abaixo:

<br>Substituir o valor 10000000000 pelo código de estabelecimento Yapay

Nome do campo|	URL
------------ | ---------
URL Retorno|	https://gateway.yapay.com.br/checkout/PagamentoCielo/RetornoCheckout?codE=10000000000&acao=retorno
URL Notificação|	https://gateway.yapay.com.br/checkout/PagamentoCielo/NotificacaoCheckout?codE=10000000000&acao=notificacao
URL de Mudança de Status|	https://gateway.yapay.com.br/checkout/PagamentoCielo/NotificacaoCheckout?codE=10000000000&acao=mudancaStatus

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
        "codigoFormaPagamento" : 52,
        "transacao" : {
            "numeroTransacao" : 123,
            "valor" : 100,
            "parcelas" : 1,
            "idioma" : 1
        },
        "itensDoPedido" : [
        {
            "nomeProduto": "Produto de Teste", 
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

**RETORNO**

```curl
  --header "Content-Type: application/json"
    {
    "numeroTransacao": 123,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 52,
    "valor": 2000,
    "valorDesconto": 0,
    "parcelas": 1,
    <!--Status que deverá ser tratado pelo eCommerce-->
    "statusTransacao": 5,
    <!--Código de autorização-->
    "autorizacao": "0",
    <!--Código erro em caso de negação-->
    "codigoTransacaoOperadora": "0",
    <!--URL para redirecionar o consumidor-->
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoCielo/checkout?cod=14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66"
    }
```

Estrutura de retorno após a finalização do pagamento. (Consulta do Ecommerce após acionamento de campainha):

```curl
  --header "Content-Type: application/json"
    {
    "numeroTransacao":123,"
    codigoEstabelecimento":"1000000000000",
    "codigoFormaPagamento":52,
    "valor":2000,"
    valorDesconto":0,"
    parcelas":2, 
    <!--Status da Transacao-->
    "statusTransacao":1,"
    <!--Data de retorno da operadora-->
    dataAprovacaoOperadora":"04/01/2018 10:39:42",
    <!--Comprovante de venda-->
    "numeroComprovanteVenda":"040120181039401403",
    <!--NSU-->
    "nsu":"d8aa2b2933ca4a63b425a2cf1012c0f0",
    <!--Bandeira escolhida no ambiente Cielo-->
    "bandeira":"Cartão de Crédito - Elo",
    "urlPagamento":"15150694525329e353c97-2477-4df5-943c-6e3600ef3f38"
    }
```

> **EXEMPLO PÁGINA CHECKOUT CIELO**

Ao enviar a requisição ao Gateway, será retornado a URL da página do Checkout Cielo para redirecionar o cliente do site. Abaixo segue exemplo da página:

![Checkout](/images/checkout_cielo.png "Checkout")
