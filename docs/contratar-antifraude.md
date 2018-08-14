O gateway fornece a possibilidade de incluir um analisador de fraude para garantir a segurança das transações.

Quando um analisador de fraude/risco é habilitado, ele se encaixará depois que a transação for autorizada e antes que a mesma seja capturada. O processo como um todo segue o seguinte fluxo:

* Transação é enviada para a operadora /instituição financeira para ser autorizada.
* Uma vez autorizada, o Gateway enviará a transação para análise de fraude.
* Caso seja aprovada na análise, a transação entrará em modo de espera para ser enviada para a captura (de forma automática ou manual, de acordo com as configurações do estabelecimento). Caso seja negada na análise, a transação será automaticamente cancelada na operadora.

## ClearSale

O Gateway de Pagamento Yapay possui integração com o sistema de prevenção de risco e fraude ClearSale, nas seguintes modalidades Total, Total Garantido, Application, RealTime e Start. Caso for utilizado a funcionalidade de Fingerprint da ClearSale, o campo SessionID deverá ser enviado no campoLivre2 da Yapay. 
<br>Para ter mais informações e receber um contato, sem compromisso, [acesse aqui](https://lp.br.clear.sale/yapay)

Para consultar valores dos planos da ClearSale com condições especiais da parceria, entre em contato através do email: *parcerias@clear.sale*

> **INFORMAÇÕES PARA CONFIGURAÇÃO**

<span class="clearsale">TOTAL/TOTAL GARANTIDO e APPLICATION</span>

* Entity Code

<span class="clearsale">START</span>

* Entity Code

<span class="clearsale">ID</span>

* Entity Code

## FControl

O Gateway de Pagamento Yapay possui integração com o sistema de prevenção de risco e fraude da FControl na modalidade *Fila*
Para maiores informações [acesse aqui](https://www.fcontrol.com.br/Integracao/Filas)

> **INFORMAÇÕES PARA CONFIGURAÇÃO**

<span class="clearsale">MODALIDADE FILA</span>

* Usuário
* Senha

## E Rede

Antifraude disponibilizado para clientes que possuem contratação com a adquirente Rede, na tecnologia E Rede.
O modelo de análise é síncrono e realizado junto a etapa de autorização da transação, sendo assim, se o retorno da antifraude for de aprovação o pedido seguirá com seu fluxo normalmente. Se não, será atualizado para Recusado pela antifraude (status 17)

Para utilização solicite a ativação do produto junto a Rede e suporte do Gateway Yapay
