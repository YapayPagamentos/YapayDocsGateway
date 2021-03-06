# Introdução

Através desta funcionalidade, é possível armazenar os dados de cartão do consumidor de forma segura (sempre será solicitado o código de segurança) nos serviços do Gateway e assim, nas cobranças futuras não será necessário a digitação de todos dados de cartão.

A API de OneClick da Yapay permite o compartilhamento de tokens, basta solicitar ao Suporte a liberação dos estabelecimentos que podem compartilhar.

**Cadastro**

![API Transação Yapay](/images/oneclick_cadastro.png "API Yapay")

**Pagamento**

Fluxo de pagamento para futuras compras:

![API Transação Yapay](/images/oneclick_pagto.png "API Yapay")

> **Particularidades**

* Disponível para cartões de crédito e débito.
* Caso não envie o CVV nos pagamentos, utilizando a funcionalidade de recorrência das adquirentes, estará disponível apenas vendas sem autenticação para pagamentos OneClick.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick
Produção | https://gateway.yapay.com.br/checkout/api/v3/oneclick

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].
