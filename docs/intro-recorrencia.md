# Pagamento recorrente

Neste modelo, o Yapay controla os pagamentos que foram cadastrados pelo estabelecimento, de acordo com sua periodicidade, valor e dia de cobrança.

O gateway possui um processo que verifica todos os dias se existem recorrências a serem processadas. Se sim, elas são agendadas para processamento na madrugada e assim que finalizadas, o Yapay notifica o estabelecimento através do acionamento da campainha, enviada no cadastro da recorrência.

![API Transação Yapay](/images/recorrencia.png "API Yapay")

> **Particularidades**

* Disponível para cartão de crédito no modelo WebService e boleto bancário;
* Renova Fácil com a operadora Cielo;
* Importante a utilização do recurso de Campainha, para atualização dos pedidos no Ecommerce;
* Habilitar junto a Adquirente para utilização de transações recorrentes: Cielo, Stone e GetNet. Para as demais não é preciso ativação.

> **Autenticação**

Os dados para autenticação devem ser enviados no cabeçalho Authorization da requisição HTTP, seguindo o padrão de Basic Authentication do HTTP. A autenticação deverá conter o usuário e senha de seu estabelecimento. Caso ainda não o possua, por gentileza enviar solicitação para nossa equipe de Suporte através do email [servicedesk@yapay.com.br].

