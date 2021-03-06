# Funcionalidades

> Captura posterior

Com o Yapay é possível realizar em primeiro momento apenas uma pré autorização, onde o valor da transação será apenas sensibilizado no limite do cartão, e após acionar o método de captura para a confirmação da venda e cobrança no cartão.

Operadora   | 	Limite Captura
----------  | -----------------------
Cielo |	5 dias, mas pode variar de acordo com o contrato. Consulte a Cielo para maiores informações
Rede |	Pode variar conforme o ramo de atuação de cada estabelecimento. Consulte a Rede para maiores informações
GETNET|	7 dias da geração do pedido
Stone|	7 dias da geração do pedido
Bin|    5 dias da geração do pedido

> Cancelamento

Cancelamento de transações rapidamente acionando o método de cancelamento.

Adquirente | Prazo de cancelamento
---------- | ----------------------
Cielo|	300 dias após a geração do pedido para transações capturadas e 15 dias úteis para transações apenas autorizadas
Rede|	Pode variar conforme o ramo de atuação de cada estabelecimento
GetNet|	365 dias para transações capturadas*. 7 dias para vendas autorizadas
Stone|	180 dias após a geração do pedido
Bin|	90 dias após captura do pedido

> Cancelamento Parcial

Com esta funcionalidade é possível realizar cancelamentos parciais e totais, dependendo da adquirente utilizada.

Adquirente | Tecnologia | Prazo de cancelamento | Observação
---------- | -----------| ----------- | ----------
Cielo|	API 3.0| 300 dias após a geração do pedido para transações capturadas e 15 dias úteis para transações apenas autorizadas | -
Rede|	E Rede|	Pode variar conforme o ramo de atuação de cada estabelecimento | Disponível apenas após D+1 da captura
GetNet| GetNetWS | 365 dias para transações capturadas. | Disponível apenas após D+1 da captura
BIN| BIN | Ocorre no mesmo dia da venda | -


> Múltiplos cartões

Através desta estrutura é possível o envio de mais de um cartão para aprovação em uma mesma transação, dividindo o valor total do pedido entre os mesmos.


> Cobrança recorrente

Funcionalidade perfeita para estabelecimentos que precisam cobrar regularmente seus clientes. Faça os cadastros de suas mensalidades e o Yapay cobrará para você de acordo com o período cadastrado.

> Boletos registrados

Com o registro dos boletos, os bancos possuem conhecimento do mesmo desde sua geração. Atualmente o Yapay possui em produção os boletos com registro do Itaú Offline, Itaú ShopLine, Santander, Bradesco Offline, Bradesco ShopFácil, Banco do Brasil e Caixa Econômica Federal.

O Yapay continua trabalhando com carteiras sem registros, basta o banco permitir isto em seu cadastro. Para utilização do boleto registrado, entre em contato com *servicedesk@yapay.com.br*.

> Renova fácil Cielo

Funcionalidade da adquirente Cielo

Essa funcionalidade facilita a identificação de um cartão que tenha sido substituído por outro no banco emissor. Dessa forma, quando uma transação recorrente é submetida ao Web Service e a Cielo identifica que o cartão utilizado está desatualizado, a operadora retorna ao Gateway os novos dados, que por sua vez, os atualiza na base recorrente e envia novamente a cobrança a operadora, com os dados atualizados.

Bancos Emissores Participantes:

* Bradesco
* Banco do Brasil
* Santander
* Panamericano
* Citi

Para utilizar esta funcionalidade, solicite a Cielo a ativação em seu estabelecimento e ,após isto, ao Suporte Yapay.

> Pagamento com único clique

Funcionalidade que permite o cadastramento de cartão para utilização nas futuras compras, assim o consumidor precisará incluir apenas o código de segurança para finalizar a compra.


> Análise de risco

O Yapay possui integração com as empresas especializadas em análises de riscos: ClearSale, FControl e Konduto.

> Multi lojas

Permite a criação de diversas “lojas” para um mesmo contrato, podendo estas, serem configuradas com as mesma filiações das instituições financeiras ou diferentes. Além disto, cada “loja” poderá acessar nosso Painel Administrativo para consultar apenas suas vendas.

`Para ativação solicitar para servicedesk@yapay.com.br`

> Retentativa de pagamento

Esta funcionalidade já gerou mais de 10% de recuperação de vendas com clientes.

As vendas não autorizadas (código 3 Não Pago) ou com falha de comunicação (código 9 Falha na Operadora) com códigos de retorno que permitem retentativa seguindo normativas da ABECS, serão armazenados para retentativa durante 2 dias. Não há alteração na estrutura de envio para utilizar esta funcionalidade. O Ecommerce deverá se atentar no retorno deste processo, onde o status para estes casos será 8 (aguardando pagamento) enquanto a venda não for aprovado ou até que sejam fechados (alterados para Não Pago) no terceiro dia.

A regra utiliza o código de forma de pagamento da Yapay para análise, que por sua vez não realiza a validação de BIN, então torna-se obrigatória essa validação por parte da plataforma.


Além de solicitar a ativação ao Suporte Yapay, é preciso uma alteração no campo origemTransacao enviando 5 para os pedidos que desejar a retentativa

* Retentativa não disponível para GETNET

> Switch de adquirência

Em caso de falha na aprovação da transação, o Gateway redirecionará o pagamento para outra adquirente configurada em seu estabelecimento.

O estabelecimento pode criar regras, juntamente com a equipe de Suporte do Yapay, podendo assim ordenar o envio para as operadoras por bandeiras. Lembrando que o roteamento é possível apenas em bandeiras que existem em outras operadoras. Abaixo segue lista de bandeiras que podem ser roteadas:

* Visa
* MasterCard
* Amex
* Elo
* Diners
* Discover
* HiperCard

Não há alteração na estrutura de envio para utilização desta funcionalidade. O Ecommerce deverá se atentar no retorno deste processo, onde o código da forma ded pagamento será diferente do enviado.



