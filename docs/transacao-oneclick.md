# Introdução

Através desta funcionalidade, é possível armazenar os dados de cartão do consumidor de forma segura (sempre será solicitado o código de segurança) nos serviços do Gateway e assim, nas cobranças futuras não será necessário a digitação de todos dados de cartão.

> **Particulariedades**

* Disponível apenas no plano Corporativo;
* Disponível para cartões de crédito e débito.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/oneclick
Produção | https://gateway.yapay.com.br/checkout/api/v3/oneclick

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].
