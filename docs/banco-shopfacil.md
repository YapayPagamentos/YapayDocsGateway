Informações sobre a contratação e particulariedades do banco Bradesco tecnologia Shopfácil.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta modalidade.

> **CONTRATAÇÃO**

Contratando a solução BRADESCO SHOPFACIL será possível oferecer na sua loja:

* Boleto sem ou com registro, dependendo de seu contrato com o banco;
* Transferência eletrônica;


Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação da BRADESCO SHOPFACIL no Gateway:

* Merchantid;
* Email de acesso ao gerenciador;
* Chave de Acesso; (Gerada dentro do gerenciador do Bradesco, passo a passo abaixo);
* Número da Carteira.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Para contratar, [acesse aqui](https://www.bradescocomercioeletronico.com.br/conteudo/meios-pagamento/duvidasFrequentes.aspx).


> **PARTICULARIEDADES**

* Modalidades com redirecionamento;
* Para utilização das modalidades ShopFácil, todos os campos referente aos dados do cliente devem ser preenchidos;
*  não for informado uma data de vencimento do boleto, será informado os dias de vencimento configurado internamente no Gateway;
* Sugerimos o envio dos campos de dados do comprador sem acentuação, pois os mesmos poderão ficar mal formatados na impressão do boleto.

> **CONFIGURAÇÃO AMBIENTE BRADESCO**

**Gerando chave de acesso**

Procedimento idêntico em ambos ambientes:

Ambiente|  URL
------- | ----------
HOMOLOGAÇÃO|	https://homolog.meiosdepagamentobradesco.com.br/gerenciadorapi
PRODUÇÃO|https://meiosdepagamentobradesco.com.br/gerenciadorapi

Após logar, acesse Configurações > Meios de Pagamento > Boleto Bancário, inclua uma palavra secreta para geração da chave.


**Configurando URL de notificação**

**BOLETO**

Após logar, acesse Configuração > Meios de Pagamento > Boleto Bancário, incluir no campo “URL de notificação”:

Ambiente|  URL
------- | ---------
HOMOLOGAÇÃO|	https://sandbox.gateway.yapay.com.br/checkout/bradesco/confirmaBoletoRegistro
PRODUÇÃO|	https://gateway.yapay.com.br/checkout/bradesco/confirmaBoletoRegistro

**TRANSFERÊNCIA**

Após logar, acesse Configuração > Meios de Pagamento > Transferência, incluir no campo “URL de notificação”:

Ambiente|  URL
------- | ---------
HOMOLOGAÇÃO|	https://sandbox.gateway.yapay.com.br/checkout/bradesco/confirmaTransf
PRODUÇÃO|	https://gateway.yapay.com.br/checkout/bradesco/confirmaTransf


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
        "codigoFormaPagamento": 105,
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
   "codigoFormaPagamento": 105,
   "valor": 2000,
   "valorDesconto": 0,
   "parcelas": 1,
   "statusTransacao": 8,
   "autorizacao": ,
   "codigoTransacaoOperadora": "0",
   "urlPagamento": "https://homolog.meiosdepagamentobradesco.com.br/apiboleto/Bradesco?token=RmVEaDhUV2dPblhpTEJYakhSM0FtSkpSb0FSbDBTMnpqbm9hMEtmcRTTzdOUm1RPT0."
}
```
