Com este meio de pagamento é possível trabalhar com transferências entre vários bancos sem possuir contrato com cada um deles.

> **CONTRATAÇÃO**

Contratando a solução SAFETYPAY será possível oferecer na sua loja:

* Transferência entre bancos;

Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da SAFETYPAY no Gateway:

* API Key;
* Signature Key;
* Usuário;
* Senha.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](http://www.safetypay.com/pt/produtos-e-solucoes/safetypay-banking/).

> **PARTICULARIDADES**

* Modalidades com redirecionamento;
* Para utilização da modalidade, todos os campos referente aos dados do cliente devem ser preenchidos;
* A URL retornada no campo `<urlPagamento>`;

> **CONFIGURAÇÃO AMBIENTE SAFETYPAY**

Configurar em seu painel safetyPay a URL de notificação do Gateway + seu código de estabelecimento Yapay:

Ambiente | URL
-------- | ------
Homologação | https://sandbox.gateway.yapay.com.br/checkout/SafetyPay/Notificacao?codigoEstabelecimento={CODIGOYAPAY}
Produção | https://gateway.yapay.com.br/checkout/SafetyPay/Notificacao?codigoEstabelecimento={CODIGOYAPAY}


> **EXEMPLOS**

**REQUISIÇÃO**

```curl
curl
        --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
        --header "Content-Type: application/json"
        --user usuario:senha
        --data-binary
       {
        codigoEstabelecimento: 1000000000000,
        codigoFormaPagamento: 155,
        transacao: {
            numeroTransacao: 1,
            valor: 2000,
            valorDesconto: 0,
            parcelas : 1,
            urlCampainha : http://seusite.com.br/campainha,
            urlResultado : http://seusite.com.br/retorno,
            ip : "192.168.12.110",
            idioma : 1
        },
        itensDoPedido: [
        {
            codigoProduto: 1,
            nomeProduto: Blusa,
            codigoCategoria: 1,
            nomeCategoria : Roupa,
            quantidadeProduto : 1,
            valorUnitarioProduto : 2000
        }
        ],
        dadosCobranca : {
            codigoCliente : 1,
            tipoCliente : 1,
            nome : Teste Yapay,
            email : teste@teste.com,
            dataNascimento : "",
            sexo : "M",
            documento : "12312321312",
            endereco : {
            logradouro : Rua Teste,
            numero : 123,
            complemento : "",
            cep : 12345-678,
            bairro : Bairro Teste,
            cidade : Cidade Teste,
            estado : SP,
            pais : BR
           }
        }
     }
```

**RESPOSTA**

```curl
    --header "Content-Type: application/json"
    {
   "numeroTransacao": 1,
   "codigoEstabelecimento": "1000000000000",
   "codigoFormaPagamento": 155,
   "valor": 2000,
   "valorDesconto": 0,
   "parcelas": 1,
   "statusTransacao": 8,
   "autorizacao": ,
   "codigoTransacaoOperadora": "0",
   "dataAprovacaoOperadora": ,
   "numeroComprovanteVenda": ,
   "nsu": ,
   "mensagemVenda": ,
   "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoSafetyPay/PagamentoSafetyPay.do?cod=141348960683a720e602-5631-4725-8f79-268c06795a3c"
}
```
