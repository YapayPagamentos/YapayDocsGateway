# Sandbox

O Yapay disponibiliza um ambiente totalmente gratuito para sua equipe de desenvolvimento realizar testes. Basta solicitar seu ambiente para nossa equipe comercial através do email [comercial@yapay.com.br] com as seguintes informações:

* Nome da Loja;
* CNPJ;
* Email para criação do cadastro.

## Informações para testes

>**CIELO API 3.0**

**Aprovação**

Bandeira | Número de cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------- | ----------------
Qualquer | 0000000000000001 | 123 | qualquer posteiror ao dia corrente

**Negação**

Bandeira | Número de cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------- | ----------------
Qualquer | 0000000000000002 | 123 | qualquer posteiror ao dia corrente


> **E REDE**


Bandeira | Número de cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------- | ----------------
Visa | 4235647728025682 | 123 | jan/2020
MasterCard | 5448280000000007 | 123 | jan/2020
HiperCard | 6062825624254001 | 123 | jan/2020
Diners | 36490101441625 | 123 | jan/2020
Elo | 4389351648020055 | 123 | jan/2020
Amex | 371341553758128 | 123 | jan/2020
JCB | 3569990012290937 | 123 | jan/2020

Caso seja enviada transação com cartão diferente dos informados, o sandbox retornará o seguinte erro:

Código de erro | Descrição
------------ | -----------
58 | Unauthorized. Contact issuer.


> **BIN - FIRST DATA**

* Utilizar os dados abaixo para aprovação;
* Para aprovação com a bandeira Cabal, o valor do pedido deve ser superior a R$100,00.

Bandeira | Número do cartão | Código de segurança | Data de validade
-------- | ---------------- | ------------------ | ----------------
Visa |	4488540010253330004 |	123 |	12/2026
MasterCard |	5547220000000102 |	123 |	12/2017
Cabal*	| 6042030000204200 |	123 |	09/2029

> **GETNET**

Para aprovação das vendas, seguir tabelas abaixo:

Bandeira  | Número do cartão |	Código de segurança |	Data de validade
--------- | -------------------- | ----------------| -----------
Visa |	4012001038166662 |	456	| 10/2019
MasterCard |	5453010000083303 |	321	 |10/2019


Categoria  |	Número de parcelas |	Valor |	Exemplo
--------- | ------------ | --------- | ---------
A vista|	1 |	nnnnn	|10000
Parcelado|	2|	nn6nn02	|10060002
Parcelado|	3|	nn6nn03	|10060003
Parcelado|	4|	nn6nn04	|10060004

> **BOLETO OFFLINE**

Neste ambiente não configuramos dados reais para geração dos boletos por segurança. Caso queira utilizar esta forma de pagamento solicite ao Suporte Yapay e o boleto será configurado com dados fictícios.

Obs: Neste ambiente os testes ocorrem apenas com boletos sem registros.

> **INTERMEDIADORES DE PAGAMENTO**

Para testes com este meio de pagamento é preciso possuir cadastro com a instituição financeira.

