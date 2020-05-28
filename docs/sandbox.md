# Sandbox

O Yapay disponibiliza um ambiente totalmente gratuito para sua equipe de desenvolvimento realizar testes. Basta solicitar seu ambiente para nossa equipe comercial através do email [comercial@yapay.com.br] com as seguintes informações:

* Nome da Loja;
* CNPJ;
* Email para criação do cadastro.

## Informações para testes

>**CIELO API 3.0**

Os status da transação são definidos pelo FINAL do cartão:

**Aprovação**

Bandeira | Final do cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------- | ----------------
Qualquer | 0000000000000000 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000001 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000004 | 123 | qualquer data posterior ao dia corrente

**Negação**

Bandeira | Final do cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------- | ----------------
Qualquer | 0000000000000002 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000003 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000005 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000006 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000007 | 123 | qualquer data posterior ao dia corrente
Qualquer | 0000000000000008 | 123 | qualquer data posterior ao dia corrente


> **E REDE**


Bandeira | Número de cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------- | ----------------
Visa | 4235647728025682 | 123 | jan/2023
Visa Electron* | 4761120000000148 | 123 | jan/2023
MasterCard | 5448280000000007 | 123 | jan/2023
Maestro* | 5277696455399733 | 123 | jan/2023
Hiper | 6370950847866501 | 123 | jan/2023
HiperCard | 6062825624254001 | 123 | jan/2023
Diners | 36490101441625 | 123 | jan/2023
Elo | 4389351648020055 | 123 | jan/2023
Amex | 371341553758128 | 123 | jan/2023
JCB | 3569990012290937 | 123 | jan/2023
Credz | 6367600001405019 | 123 | jan/2023
Cabal | 6042034400069940 | 123 | jan/2023
Sorocred | 6364142000000122 | 123 | jan/2023
Credsystem | 6280281038975334 | 123 | jan/2023
Banescard | 6031828795629272 | 123 | jan/2023

Caso seja enviada transação com cartão diferente dos informados, o sandbox retornará o seguinte erro:

Código de erro | Descrição
------------ | -----------
58 | Unauthorized. Contact issuer.

* Estas bandeiras são de débito e portanto possuem autenticação obrigatória. Após o envio da requisição ao Gateway será retornado a URl para autenticação, neste ambiente de sandbox a Rede criou uma página para simulação.
Para aprovação informe o código que será exibido na tela, para negação informar um código diferente:

![API REde](/images/telampi.png "Rede")


> **BIN - FIRST DATA**

* Utilizar os dados abaixo para aprovação;
* Para aprovação com a bandeira Cabal, o valor do pedido deve ser superior a R$100,00.

Bandeira | Número do cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------ | ----------------
Visa |	4488540010253330004 |	123 |	12/2026
MasterCard |	5547220000000102 |	123 |	12/2027
Cabal*	| 6042030000204200 |	123 |	09/2029

*A Adquirente BIN não disponibilizou ainda cartões de testes para as bandeiras Elo, Hipercard e Sorocred. Portanto, não há regras para os testes, deve ser enviado qualquer cartão.

> **GETNET**

Para aprovação das vendas, seguir tabelas abaixo:

Bandeira  | Número do cartão |	Código de segurança |	Data de validade
--------- | -------------------- | ----------------| -----------
Visa |	4012001038166662 |	123	| 10/2023
MasterCard |	5453010000083303 |	123	 |10/2023
Visa Electron | 4012001037141112 | 123 | 10/2023
Maestro | 54326201155166661 | 123 | 10/2023
Amex | 376442058032004 | 1589 | 07/2023
Elo | 5067230000009011 | 568 | 10/2023


Categoria  |	Número de parcelas |	Valor |	Exemplo
--------- | ------------ | --------- | ---------
A vista|	1 |	nnnnn	|10000
Parcelado|	2|	nn6nn02	|10060002
Parcelado|	3|	nn6nn03	|10060003
Parcelado|	4|	nn6nn04	|10060004

> **BOLETO OFFLINE**

Neste ambiente não configuramos dados reais para geração dos boletos por segurança. Caso queira utilizar esta forma de pagamento solicite ao Suporte Yapay e o boleto será configurado com dados fictícios.

Obs: Neste ambiente os testes ocorrem apenas com boletos sem registros.

<!-- *> **INTERMEDIADORES DE PAGAMENTO**

Para testes com este meio de pagamento é preciso possuir cadastro com a instituição financeira. -->

## Bibliotecas de exemplo

Disponibilizamos [bibliotecas de exemplos](https://github.com/YapayPagamentos/integracao_gateway) para integração com o Gateway Yapay:

- Ruby
- PHP
- Java
- .NET

## Collections Postman

> **API TRANSAÇÃO**

Exemplos de chamadas as API's de transação do Gateway, [acesse aqui](https://www.getpostman.com/collections/fab35ade5eb63509da4b)

> **3DS 2.0 CIELO**

Exemplo de chamada a API 3DS 2.0, [acesse aqui](https://www.getpostman.com/collections/139de1e111de992645db)
* Necessário a implementação do JS Cielo

> **API RECORRÊNCIA**

Exemplos de chamadas as API's de pagamento recorrente, [acesse aqui](https://www.getpostman.com/collections/0738bd472eeae610dea9)

> **API ONECLICK**

Exemplos de chamadas as API's de pagamento com único clique, [acesse aqui](https://www.getpostman.com/collections/7c690e31400dfcbfcac9)

> **API CHECKOUT YAPAY**

Exemplos de chamadas as API's do checkout Yapay, [acesse aqui](https://www.getpostman.com/collections/4c07442480fb955054f0)

