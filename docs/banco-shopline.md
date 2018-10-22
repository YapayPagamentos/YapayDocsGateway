Informações sobre a contratação e particulariedades do banco Itaú tecnologia ShopLine.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta modalidade.

> **CONTRATAÇÃO**

Contratando a solução ITAU SHOPLINE será possível oferecer na sua loja:

* Boleto sem ou com registro, dependendo de seu contrato com o banco;
* Transferência eletrônica;


Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da ITAU SHOPLINE no Gateway:

* Código da empresa;
* Chave de acesso.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://www.itau.com.br/empresas/recebimentos/shopline/).

ou 

Acesse o bankline e vá na aba "Recebimentos" e selecione Itaú Shopline - Comércio Eletrônico

![Cache](/images/shopline.png "Cache")

Clique em contratar:

![Cache](/images/shopline2.png "Cache")

Preencha os dados:

![Cache](/images/shopline3.png "Cache")

> **PARTICULARIEDADES**

* Modalidades com redirecionamento;
* O tamanho do número do pedido deverá ser de no máximo 8 dígitos;
* Para utilização das modalidades ShopLine, todos os campos referente aos dados do cliente devem ser preenchidos;
* Tempo padrão de consulta no banco para atualização do status no Yapay: 120 dias;
* Se não for informado uma data de vencimento do boleto, será informado os dias de vencimento configurado internamente no Gateway;
* Para evitar fraudes, o Itaú sempre abrirá as duas opções para o cliente (boleto e transferência) independente da modalidade enviada ao Gateway.

> **CONFIGURAÇÃO AMBIENTE ITAU**

* Para o Gateway de Pagamento funcionar corretamente, é necessário configurar URL de retorno no BankLine.
* Acesse o BankLine, aba Cobrança > Itaú Shopline > Informações Cadastrais e inclua a URL abaixo no campo “URL Retorno”

<span class="url">URL RETORNO: https://gateway.yapay.com.br/checkout/</span>

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
        "codigoFormaPagamento": 16,
        "transacao": {
            "numeroTransacao": 1,
            "valor": 2000,
            "valorDesconto": 0,
            "parcelas" : 1,
            "urlCampainha" : "http://seusite.com.br/campainha",
            "urlResultado" : "http://seusite.com.br/retorno",
            "ip" : "192.168.12.110",
            "idioma" : 1
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
        "codigoFormaPagamento": 16,
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
        "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/PagamentoItauShopline/PagamentoItauShopline.do?cod=141348960683a720e602-5631-4725-8f79-268c06795a3c"
        }
```
