Informações sobre a contratação e particulariedades do banco Banrisul tecnologia Banricompras.

Neste conteúdo também encontrará exemplos de envio e retorno utilizando esta modalidade.

> **CONTRATAÇÃO**

Contratando a solução BANRICOMPRAS será possível oferecer na sua loja:

* Boleto;
* Pagamento pré datado;
* Pagamentos parcelados;
* Pagamentos á vista.


Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação do BANRICOMPRAS no Gateway:

* Código do estabelecimento Banrisul;
* Código da rede;
* Senha de consulta.

O Yapay não participa das negociações entre o estabelecimento e bancos/adquirentes. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

Informações sobre a contratação, entre em contato com *banrisul_cartoes_atendimento_adquirencia@banrisul.com.br*

> **PARTICULARIEDADES**

* Modalidades com redirecionamento;
* Para utilização das modalidades Banricompras, todos os campos referente aos dados do cliente devem ser preenchidos;
* Se não for informado uma data de vencimento do boleto, será informado os dias de vencimento configurado internamente no Gateway;
* Processo de homologação junto ao Banrisul obrigatório para liberação em produção.

> **CONFIGURAÇÃO AMBIENTE BANRISUL**

Para o Gateway de Pagamento funcionar corretamente, é necessário configurar algumas urls no ambiente do Banricompras.

**CAMPAINHA**

**Homologação**

Link Painel Banrisul: https://ww4.banrisul.com.br/banricompras/

URL Campainha: https://sandbox.gateway.yapay.com.br/checkout/Banrisul/NotificacaoBanrisul.do

**Produção**

Link Painel Banrisul: https://ww7.banrisul.com.br/banricompras/

URL Campainha: https://gateway.yapay.com.br/checkout/Banrisul/NotificacaoBanrisul.do

**NOTIFICAÇÃO**

**Homologação**

URL Sucesso: https://gateway.sandbox.yapay.com.br/checkout/Banrisul/RedirecionamentoBanrisulOk.do

URL Não Pago: https://gateway.yapay.com.br/yapay/Banrisul/RedirecionamentoBanrisulNoOk.do

**Produção**

URL Sucesso: https://gateway.yapay.com.br/checkout/Banrisul/RedirecionamentoBanrisulOk.do

URL Não Pago: https://gateway.yapay.com.br/checkout/Banrisul/RedirecionamentoBanrisulNoOk.do

> **PROCESSO DE HOMOLOGAÇÃO**

Após realizar a integração com o Yapay em ambiente de testes e configurações no painel Banrisul, enviar para tecnologia_homologacoes@banrisul.com.br o link de acesso a página de testes, bem como o código de usuário e senha para login. Assim que o processo for finalizado pela equipe Banrisul, os mesmos enviarão os dados de produção para o estabelecimento.

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
        "codigoFormaPagamento": 26,
        "transacao": {
            "numeroTransacao": 1,
            "valor": 2000,
            "valorDesconto": 0,
            "parcelas" : 1,
            "urlCampainha" : http://seusite.com.br/campainha,
            "urlResultado" : http://seusite.com.br/retorno,
            "ip" : "192.168.12.110",
            "idioma" : 1
        },
        "itensDoPedido: [
        {
            "codigoProduto": 1,
            "nomeProduto": Blusa,
            "codigoCategoria": 1,
            "nomeCategoria" : Roupa,
            "quantidadeProduto" : 1,
            "valorUnitarioProduto" : 2000
        }
        ],
        "dadosCobranca" : {
            "codigoCliente" : 1,
            "tipoCliente" : 1,
            "nome" : Teste Yapay,
            "email" : teste@teste.com,
            "dataNascimento" : "",
            "sexo" : "M",
            "documento" : "12312321312",
            "endereco" : {
            "logradouro" : Rua Teste,
            "numero" : 123,
            "complemento" : "",
            "cep" : 12345-678,
            "bairro" : Bairro Teste,
            "cidade" : Cidade Teste,
            "estado" : SP,
            "pais" : BR
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
        "codigoFormaPagamento": 26,
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
        "urlPagamento": "https://gateway.yapay.com.br/checkout/Boleto/PagamentoBanrisul.do?cod=141348960683a720e602-5631-4725-8f79-268c06795a3c"
        }
```
