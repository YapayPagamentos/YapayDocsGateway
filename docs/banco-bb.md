Informações sobre a contratação e particulariedades do banco do Brasil tecnologia Online.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta modalidade.

> **CONTRATAÇÃO**

Contratando a solução BB ONLINE será possível oferecer na sua loja:

* Boleto sem ou com registro, dependendo de seu contrato com o banco;
* Transferência eletrônica;


Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação do BB ONLINE no Gateway:

* Código do convênio;
* Código cobrança.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](http://www.bb.com.br/pbb/pagina-inicial/empresas/produtos-e-servicos/pagamentos-e-recebimentos/comercio-eletronico#/).

> **PARTICULARIEDADES**

* Modalidades com redirecionamento;
* Para utilização das modalidades BBOnline, todos os campos referente aos dados do cliente devem ser preenchidos;
* Se não for informado uma data de vencimento do boleto, será informado os dias de vencimento configurado internamente no Gateway;
* Para baixa automática dos boletos deve contratar o conciliador Yapay, para informações entre em contato com *comercial@yapay.com.br*;
* Caso o boleto seja gerado com sucesso, a linha digitável será retornada via API.

> **EXEMPLOS**

**REQUISIÇÃO**

```curl
curl
        --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
        --header "Content-Type: application/json"
        --user usuario:senha
        --data-binary
       {
        "codigoEstabelecimento": 1000000000000,
        "codigoFormaPagamento": 21,
        "transacao": {
            "numeroTransacao": 1,
            "valor": 2000,
            "valorDesconto": 0,
            "parcelas" : 1,
            "urlCampainha" : "http://seusite.com.br/campainha",
            "urlResultado" : "http://seusite.com.br/retorno",
            "ip" : "192.168.12.110",
            "idioma" : 1,
            "dataVencimentoBoleto" : "10/01/2020"
        },
        "itensDoPedido": [
        {
            "codigoProduto": "1",
            "nomeProduto": "Blusa",
            "codigoCategoria": "1",
            "nomeCategoria" : "Roupa",
            "quantidadeProduto" : 1,
            "valorUnitarioProduto" : 2000
        }
        ],
        "dadosCobranca" : {
            "codigoCliente" : "1",
            "tipoCliente" : 1,
            "nome" : "Teste Yapay",
            "email" : "teste@teste.com",
            "dataNascimento" : "",
            "sexo" : "M",
            "documento" : "12312321312",
            "endereco" : {
            "logradouro" : "Rua Teste",
            "numero" : "123",
            "complemento" : "",
            "cep" : "12345-678",
            "bairro" : "Bairro Teste",
            "cidade" : "Cidade Teste",
            "estado" : "SP",
            "pais" : "BR"
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
   "codigoFormaPagamento": 21,
   "valor": 2000,
   "valorDesconto": 0,
   "parcelas": 1,
   "statusTransacao": 8,
   "autorizacao": ,
   "codigoTransacaoOperadora": "0",
   "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoBBOnline/PagamentoBBOnline.do?cod=147499950329455715d65-621f-4b80-896c-5d1a645fb9e0"
}
```
