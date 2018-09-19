# Introdução

O Yapay disponibiliza a integração com diversas Instituições Financeiras através de uma única integração via API em RESTful.

![API Transação Yapay](/images/transacao_banco.png "API Yapay")

A comunicação com o Yapay Gateway ocorrerá após a finalização do pagamento no Checkout do Ecommerce, de forma transparente para o consumidor. Ao ser finalizado o pagamento dentro da loja, o Ecommerce deverá consumir os serviços WebServices do Yapay encaminhando as informações da compra de acordo com a estrutura que será apresentada nesta documentação.
Recebendo a requisição, o Gateway retornará uma URL para a geração do boleto.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

## Criando uma transação

<span class="post">POST</span>

Estrutura para geração de boletos com carteiras sem ou com registro.

Para detalhes da estrutura de envio e retorno, [clique aqui](tabela-boletos.md)

> **Particulariedades**

* O campo `<estado>` deve ser preenchido apenas com a sigla do Estado;
* O campo `<numeroTransacao>` deve conter até 8 dígitos;
* Caso o campo `<dataVencimentoBoleto>` não for enviado, será utilizado os dias de vencimento configurado internamente no Gateway;
* Para boletos com carteira registrada (contratação a parte), o status retornado pelo Yapay no primeiro momento será 5 (transação em andamento), enquanto para boletos sem registros é retornado 8 (aguardando pagamento);
* Importante a utilização do recurso de Campainha, para atualização dos pedidos no Ecommerce;
* A conciliação de boletos não é realizada automaticamente, funcionalidade deve ser contratada a parte com o comercial@yapay.com.br.

> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
  {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 29,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "urlResultado" : "http://seusite.com.br/retorno",
        "dataVencimentoBoleto":"13/12/2030"
    },
    "itensDoPedido" : [
    {
        "codigoProduto" : 1,
        "nomeProduto" : "Produto 1",
        "codigoCategoria" : 1,
        "nomeCategoria" : "categoria",
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 2000
    }
    ],
    "dadosCobranca" : {
        "codigoCliente" : 1,
        "tipoCliente" : 1,
        "nome" : "Teste 123",
        "email" : "teste@teste.com",
        "dataNascimento" : "10/01/1975",
        "sexo" : "M",
        "documento" : "123.123.123-12",
        "endereco" : {
          "logradouro" : "Rua",
          "numero" : "123",
          "complemento" : "",
          "cep" : "12345-678",
          "bairro" : "Bairro",
          "cidade" : "Cidade",
          "estado" : "SP",
          "pais" : "BR"
          }
    }
  }
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  {  "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 29,
    "valor": 2000, 
    "valorDesconto": 0, 
    "parcelas": 1, 
    "statusTransacao": 8,
    "autorizacao": "0",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "", 
    "numeroComprovanteVenda": "", 
    "nsu": "",
    "mensagemVenda": "",
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/Gerarboleto.do?cod=14956296486904d8312c6-d57a-499e-b53b-504047402e45"
  }
```

## Enviar instruções do boleto na requisição

A partir do envio do nó `camposExtras` é possível incluir instruções diferentes para cada boleto gerado. 
O número da instrução deve ser enviado no campo `<chave>` a partir do número 1001 até o 1005 e sua respectiva instrução no campo `<valor>`.

`OBS: A quantidade de instruções disponíveis irá variar por banco.`

Banco | Modalidade | Quantidade de instruções
:-----: | :-----------: | :------------:
Itaú | Offline | 5
Itaú | Online | 3
Bradesco | Offline | 4
Bradesco | Online | 5
Banco do Brasil | Offline | 4
Banco do Brasil | Online | 1
Santander | Offline | 5
Caixa | Offline | 5


> **Exemplo de envio em JSON - campos Extras**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
  {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 29,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "urlResultado" : "http://seusite.com.br/retorno",
        "dataVencimentoBoleto":"13/12/2030"
    },
    "camposExtras":[
    	{
    	 "chave":1001,
         "valor":"Essa é a primeira instrução"
    	},
    		{
    	 "chave":1002,
         "valor":"Essa é a segunda instrução"
    	},
    	{
    	 "chave":1003,
         "valor":"Essa é a terceira instrução"
    	},
        {
    	 "chave":1004,
         "valor":"Essa é a quarta instrução"
    	},
        {
    	 "chave":1005,
         "valor":"Essa é a quinta e ultima instrução"
    	}
    ],
    "itensDoPedido" : [
    {
        "codigoProduto" : 1,
        "nomeProduto" : "Produto 1",
        "codigoCategoria" : 1,
        "nomeCategoria" : "categoria",
        "quantidadeProduto" : 1,
        "valorUnitarioProduto" : 2000
    }
    ],
    "dadosCobranca" : {
        "codigoCliente" : 1,
        "tipoCliente" : 1,
        "nome" : "Teste 123",
        "email" : "teste@teste.com",
        "dataNascimento" : "10/01/1975",
        "sexo" : "M",
        "documento" : "123.123.123-12",
        "endereco" : {
          "logradouro" : "Rua",
          "numero" : "123",
          "complemento" : "",
          "cep" : "12345-678",
          "bairro" : "Bairro",
          "cidade" : "Cidade",
          "estado" : "SP",
          "pais" : "BR"
          }
    }
  }
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
  {  "numeroTransacao": 1234,
    "codigoEstabelecimento": "1000000000000",
    "codigoFormaPagamento": 29,
    "valor": 2000, 
    "valorDesconto": 0, 
    "parcelas": 1, 
    "statusTransacao": 8,
    "autorizacao": "0",
    "codigoTransacaoOperadora": "0",
    "dataAprovacaoOperadora": "", 
    "numeroComprovanteVenda": "", 
    "nsu": "",
    "mensagemVenda": "",
    "urlPagamento": "https://sandbox.gateway.yapay.com.br/checkout/Gerarboleto.do?cod=14956296486904d8312c6-d57a-499e-b53b-504047402e45"
  }
```

