## Boletos registrados

Com esta modalidade, os bancos possuem conehcimento do boleto desde sua geração, permitindo o lojista realizar protestos ao cliente caso o pagamento não for realizado.

Para utilização de qualquer boleto com carteira registrada é preciso realizar a abertura de relacionamento entre o banco e VAN homologada com o Yapay.

> **PARTICULARIEDADES**

* Para a geração de Boleto offlines, todos os campos referente aos dados do cliente devem ser preenchidos;
* Arquivo de registro e conciliação com layout de 400 posições para todos os bancos;
* Campo `<estadoComprador>` deve ser preenchido pela sigla;
* O tamanho do número do pedido, deverá possuir no máximo 7 dígitos;
* Se não for informado uma data de vencimento do boleto na requisição, será informado os dias de vencimento configurados internamente no Gateway;
* A URL retornada no campo `<urlPagamento>`;
* A requisição e retorno do Yapay para boletos registrados possuem a mesma estrutura dos sem registro, porém o status a ser retornado será 5 (transação em andamento) ao invés de 8 (aguardando pagamento);
* Para ativação do boleto registrado e Módulo de Conciliação entrar em contato com comercial@yapay.com.br;
* O Yapay não participa das negociações entre o estabelecimento e bancos/administradoras. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

> **SANTANDER**

* agência;
* conta;
* código do cedente;
* número da carteira;
* espécie de documento; (Exemplos: DM, RM, ME, NP)
* código de transmissão.

> **CAIXA ECONÔMICA FEDERAL**

* agência;
* conta;
* código do convênio;
* número da carteira;
* código de operação;
* espécie de documento. (Exemplos: DM, RM, ME, NP)

> **ITAU**

* agência;
* conta;
* número da carteira;
* espécie de documento. (Exemplos: DM, RM, ME, NP)

> **BRADESCO**

* agência;
* conta;
* número da carteira;
* espécie de documento. (Exemplos: DM, RM, ME, NP)

> **BANCO DO BRASIL**

* agência;
* conta;
* código do convênio;
* número da carteira;
* variação da carteira;
* espécie de documento. (Exemplos: DM, RM, ME, NP);
* client ID;
* secret;

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
        "codigoFormaPagamento": 30,
        "transacao": {
            "numeroTransacao": 1,
            "valor": 2000,
            "valorDesconto": 0,
            "parcelas" : 1,
            "urlCampainha" : http://seusite.com.br/campainha,
            "urlResultado" : http://seusite.com.br/retorno,
            "ip" : "192.168.12.110",
            "idioma" : 1,
            "dataVencimentoBoleto":"01/01/2020"  

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

O status do primeiro retorno será 5 (transação em andamento) e assim que o arquivo de registro for criado e enviado, o status será alterado para 8 (aguardando pagamento) até a compensação do boleto.

```curl
        --header "Content-Type: application/json"
        {
        "numeroTransacao": 1,
        "codigoEstabelecimento": "1000000000000",
        "codigoFormaPagamento": 30,
        "valor": 2000,
        "valorDesconto": 0,
        "parcelas": 1,
        "statusTransacao": 5,
        "autorizacao": ,
        "codigoTransacaoOperadora": "0",
        "dataAprovacaoOperadora": ,
        "numeroComprovanteVenda": ,
        "nsu": ,
        "mensagemVenda": ,
        "urlPagamento": "https://sandbox.gateway.yapay.com.br/GeradorBoleto.do?cod=1413487983447baddcb56-0126-4353-9253-538f64d""
        }
```

## Boleto sem registro

O Gateway de Pagamento aceita boletos sem registro emitidos pelos seguintes bancos:

* Itaú;
* Bradesco;
* Banco do Brasil;
* Caixa;
* Santander.

Ao final do processo de contratação, deve-se estar de posse das seguintes informações para ativação dos boletos no Gateway:

* Convênio;
* Agência;
* Conta;
* Número da Carteira;
* Espécie de Documento. (Exemplos: DM, RM, ME, NP)

> **PARTICULARIEDADES**

* Para a geração de Boleto offlines, todos os campos referente aos dados do cliente devem ser preenchidos.
* Campo `<estadoComprador>` deve ser preenchido pela sigla;
* O tamanho do número do pedido, deverá possuir no máximo 8 dígitos;
* Se não for informado uma data de vencimento do boleto na requisição, será informado os dias de vencimento configurados internamente no Gateway;
* A URL retornada no campo `<urlPagamento>`;
* Conciliação de boletos não é realizada automaticamente, para tal deve ser contratado o Módulo de Conciliação do Gateway. Para informações entrar em contato com comercial@yapay.com.br;
* O Yapay não participa das negociações entre o estabelecimento e bancos/administradoras. Desta forma, taxas ou eventuais isenções são tratadas de forma direta entre os envolvidos.

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
        "codigoFormaPagamento": 29,
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
        "codigoFormaPagamento": 29,
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
        "urlPagamento": "https://sandbox.gateway.yapay.com.br/GeradorBoleto.do?cod=1413487983447baddcb56-0126-4353-9253-538f64d""
        }
```
