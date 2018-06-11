# Criando uma transação

Estrutura para geração de boletos com carteiras sem ou com registro.

> **Particulariedades**

* O campo `<estado>` deve ser preenchido apenas com a sigla do Estado;
* O campo `<numeroTransacao>` deve conter até 8 dígitos;
* Caso o campo `<dataVencimentoBoleto>` não for enviado, será utilizado os dias de vencimento configurado internamente no Gateway;
* Para boletos com carteira registrada (contratação a parte), o status retornado pelo Yapay no primeiro momento será 5 (transação em andamento), enquanto para boletos sem registros é retornado 8 (aguardando pagamento);
* Importante a utilização do recurso de Campainha, para atualização dos pedidos no Ecommerce;
* A conciliação de boletos não é realizada automaticamente, funcionalidade deve ser contratada a parte com o comercial@yapay.com.br.

> **Exemplo de envio em JSON**

```curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
  --curl -u usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
  {
    "codigoEstabelecimento" : 1000000000000,
    "codigoFormaPagamento" : 29,
    "transacao" : {
        "numeroTransacao" : 1234,
        "valor" : 2000,
        "valorDesconto" : 0,
        "parcelas" : 1,
        "urlCampainha" : "http://seusite.com.br/campainha",
        "urlResultado" : "http://seusite.com.br/retorno",
        "ip" : "192.168.12.110",
        "idioma" : 1,
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
