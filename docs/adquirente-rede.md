Informações sobre a contratação e particulariedades da Adquirente Rede.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta adquirente.

> **CONTRATAÇÃO**

Contratando a solução da E REDE para e-commerce será possível oferecer na sua loja:

* Cartão de crédito aunteticado (Bandeiras Visa e Mastercard);
* Cartão de crédito Visa;
* Cartão de crédito MasterCard;
* Cartão de crédito Amex;
* Cartão de crédito Hiper;
* Cartão de crédito HierpCard;
* Cartão de crédito Elo;
* Cartão de crédito JCB;
* Cartão de crédito Credz;
* Cartão de crédito Credsystem;
* Cartão de crédito Banescard;
* Cartão de crédito Sorocred;
* Cartão de crédito Cabal;
* Cartão de débito Visa Electron;
* Cartão de débito Maestro;


Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da E REDE no Gateway:

* Filiação (PV);
* Token;

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://www.userede.com.br/nossos-produtos/e-rede).

> **PARTICULARIEDADES**

* Para esta modalidade é necessário certificado SSL de segurança 2048 bits;
* Esta operadora de cartão permite cadastrar uma informação para aparecer na fatura dos clientes quando realizarem compras sua loja, funcionalidade chamada de SoftDescriptor. Esta deverá possuir até 13 caracteres. Caso queira utilizar, envie ao Suporte SuperPay o nome desejado para configuração em seu estabelecimento.
Também é possível o envio do SoftDescriptor por pedido, para isto solicite ao Suporte a ativação e envie a informação no campoLivre4 de cada transação;
* Para transações com cartão de débito ou autenticada, o eCommerce deverá enviar o “userAgente” (Identificador do browser utilizado pelo comprador no momento da compra) no campo `<campoLivre1>` e redirecionar o consumidor para o campo `<urlPagamento>` recebida no retorno, onde o mesmo deverá incluir sua senha ou token no ambiente do banco emissor. Apenas após esta etapa, a transação será concluída.
* Para bandeiras de débito (Visa Electron e Maestro) e/ou cartões autenticados (Visa e MasterCard), é preciso a liberação do serviço de 3DS. Portanto, para utilização destas bandeiras solitem a liberação diretamente com a Adquirente Rede;
* O cancelamento com esta adquirente geralmente não é retornado no mesmo momento de sua solicitação, portanto, o Gateway só atualizará o status do pedido para 13 (Cancelado) quando receber da Rede a informação que o cancelamento foi realizado.

> **CONFIGURAÇÃO GATEWAY**

[Acesse aqui](https://atendimento.yapay.com.br/hc/pt-br/articles/360005085993-Cart%C3%A3o-de-Cr%C3%A9dito-e-D%C3%A9bito-e-Rede) para informações sobre como configurar o E Rede no Gateway Yapay.

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
    "codigoFormaPagamento" : 191,
    "transacao" : {
        "numeroTransacao" : 123,
        "valor" : 500000,
        "parcelas" : 1,
        "idioma" : 1
    },
    "dadosCartao" : {
        "nomePortador" : "Teste Teste",
        "numeroCartao" : "5899160000000005",
        "codigoSeguranca" : "123",
        "dataValidade" : "01/2019"
    },
    "itensDoPedido" : [
    {
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 500000
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
    "codigoFormaPagamento": 191,
    "valor": 500000,
    "valorDesconto": 0,
    "parcelas": 1,
    <!--Status que deverá ser tratado pelo eCommerce-->
    "statusTransacao": 1,
    <!--Código de autorização-->
    "autorizacao": "123456",
    <!--Código retorno Cielo-->
    "codigoTransacaoOperadora": "0",
    <!--Data retorno adquirente-->
    "dataAprovacaoOperadora": "24/05/2030",
    <!--TID-->
    "numeroComprovanteVenda": "10117092708342800232",
    "nsu": "428706",
    <!--Mensagem adquirente-->
    "mensagemVenda": "00 - Success",
    "urlPagamento": "14956291484887110cf2a-9aeb-4b34-a869-1a61f0611b66",
    "cartoesUtilizados": ["589916******0005"]
    }
```
