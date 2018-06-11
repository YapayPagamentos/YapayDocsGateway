# Introdução

O Yapay disponibiliza a integração com diversas Instituições Financeiras através de uma única integração via API em RESTful.

![API Transação Yapay](/images/transacao.png "API Yapay")

A comunicação com o Yapay Gateway ocorrerá após a finalização do pagamento no Checkout do Ecommerce, de forma transparente para o consumidor. Ao ser finalizado o pagamento dentro da loja, o Ecommerce deverá consumir os serviços WebServices do Yapay encaminhando as informações da compra de acordo com a estrutura que será apresentada nesta documentação.
Para cartões de débito será obrigatório o redirecionamento do cliente para a URL do banco retornada pelo Gateway, onde o consumidor digitará sua senha eletrônica e finalizará a compra.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  | https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao
Produção | https://gateway.yapay.com.br/checkout/api/v3/transacao

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].



