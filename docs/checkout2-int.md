# Introdução

Através desta funcionalidade, é possível finalizar pagamentos dentro do ambiente seguro do Yapay. O consumidor será redirecionado para o Checkout do Gateway e assim finalizará sua transação. Os meios de pagamentos disponíveis serão todos que estiverem configurados no estabelecimento.

![API Transação Yapay](/images/checkout.png "API Yapay")

* [clique aqui](checkout-simplificada.md) para acessar a documentação do Checkout antigo

> **Particularidades**

* Funcionalidade com redirecionamento;
* Importante a utilização do recurso de Campainha, para atualização dos pedidos no Ecommerce;
* Definição da forma de pagamento pelo consumidor;
* Link de pagamento disponível até sua expiração.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

