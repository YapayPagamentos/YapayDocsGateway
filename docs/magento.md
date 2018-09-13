## Módulo Magento

> **Particulariedades**

* As ações de captura e cancelamento não estão disponíveis no Módulo Magento. Estas ações deverão ser realizadas diretamente no painel administrativo Yapay.
* As funcionalidades de Recorrência, Múltiplos Cartões, Retentativa de Pagamento e Switch de Adquirência atualmente não estão disponíveis no Módulo Magento.

> **Formas de pagamento disponíveis**

**Cartões**

Código | Bandeira | Tipo | Tecnologia | Adquirente | Modelo
------ | -------- |----- | ------------|-----------|---------
52|	Checkout|Checkout|	Cielo API 3.0|	Cielo|	Redirect
170|	Visa	|Crédito | Cielo API 3.0|	Cielo|	WebService
171|	MasterCard | Crédito|Cielo API 3.0|	Cielo|	WebService
172|	American Express|Crédito|Cielo API 3.0|	Cielo|	WebService
173|	Elo|	Crédito|Cielo API 3.0|	Cielo|	WebService
174|	Diners|	Crédito|Cielo API 3.0|	Cielo|	WebService
175|	Discover|Crédito|	Cielo API 3.0|	Cielo|	WebService
176|	Aura|Crédito|	Cielo API 3.0|	Cielo|	WebService
177|	JCB|	Crédito|Cielo API 3.0|	Cielo|	WebService
178|	Maestro|Débito|	Cielo API 3.0|	Cielo|	WebService
179|	Visa Electron|Débito|	Cielo API 3.0|	Cielo|	WebService
180|    Hipercard |Crédito| Cielo API 3.0 | Cielo | WebService
189|	American Express|Crédito|	E-Rede|	Rede|	WebService
190|	Visa|Crédito|	E-Rede|	Rede|	WebService
191|	MasterCard|Crédito|	E-Rede|	Rede|	WebService
192|	Diners	|Crédito|E-Rede|	Rede|	WebService
193|	Hipercard|Crédito|	E-Rede|	Rede|	WebService
194|	Hiper	|Crédito| E-Rede|	Rede|	WebService
195|	JCB|Crédito|	E-Rede|	Rede|	WebService
196|	Credz|Crédito|	E-Rede|	Rede|	WebService
197|	Maestro|Débito|	E-Rede|	Rede|	WebService
198|	Visa Electron|Débito|	E-Rede|	Rede|	WebService
199|	Elo|Crédito	|E-Rede|	Rede|	WebService
270|	Visa|	Crédito|GetNetWS|	GetNet|	WebService
271|	MasterCard|Crédito|	GetNetWS|	GetNet|	WebService
272|	American Express |Crédito|	GetNetWS|	GetNet|	WebService
273|	Elo |Crédito|	GetNetWS|	GetNet|	WebService
274|	Maestro |Débito|	GetNetWS|	GetNet|	WebService
275|	Visa Electron|Débito|	GetNetWS|	GetNet|	WebService
350|	Visa|Crédito|	StoneWs|	Stone|	WebService
351|	MasterCard|Crédito|	StoneWs|	Stone|	WebService
352|    Hipercard | Crédito| StoneWs | Stone | WebService
353|    Elo | Crédito| StoneWs | Stone | WebService
380|	Visa|Crédito|	BinWS|	Bin-FirstData|	WebService
381|	MasterCard|Crédito|	BinWS|	Bin-FirstData|	WebService
382|	Cabal|Crédito|	BinWS|	Bin-FirstData|	WebService

**Boletos e Transferências**

Código | Banco | Modalidade | Tecnologia 
------ | -------- |----- | ------------
16|	Itaú|	Transferência|	Itaú Shopline
17|	Itaú|	Boleto Online|	Itaú Shopline
20|	Banco do Brasil|	Boleto|	BBOnline
21|	Banco do Brasil|	Transferência|	BBOnline
23|	Banrisul|	Transferência|	Banricompras
24|	Banrisul|	Parcelamento|	Banricompras.com
25|	Banrisul|	Pré Datado|	Banricompras.com
26|	Banrisul|	Boleto|	Banricompras.com
28|	Banco do Brasil|	Boleto Offline|	Banco do Brasil
29|	Itaú|	Boleto Offline|	Itaú
30|	Bradesco|	Boleto Offline|	Bradesco
34|	Caixa Econômica Federal |	Boleto Offline|	Caixa Econômica Federal
41|	Santander|	Boleto Offline|	Santander
48|	Banco do Brasil|	Boleto Offline com registro|	Banco do Brasil
104|	Bradesco|	Transferência|	Bradesco Shopfacil
105|	Bradesco|	Boleto Online|	Bradesco ShopFácil

> **Status Magento**

O Gateway enviará ao Magento automaticamente, após a finalização do pagamento, o status da transação. Portanto, os pedidos no Magento ficarão com o status do mesmo e não do Gateway.
Abaixo tabela de/para dos status Magento e Gateway Yapay:

Status Gateway | Status Magento | Descrição Status Magento
-------------- | -------------- | ----------------------
1 - Pago e Capturado | processing | O pagamento do seu pedido foi confirmado
2 - Pago e não Capturado | processing | O pagamento do seu pedido foi confirmado
3 - Não Pago | pending_payment | O pagamento do seu pedido continua em pendente. Estamos aguardando a confirmação para continuar o processo de venda
5 - Transação em Andamento | pending_payment | O pagamento do seu pedido continua em pendente. Estamos aguardando a confirmação para continuar o processo de venda
8 - Aguardando Pagamento | pending_payment | O pagamento do seu pedido continua em pendente. Estamos aguardando a confirmação para continuar o processo de venda
9 - Falha na operadora | pending_payment | Houve uma falha na operadora. Entre em contato conosco
13 - Cancelado | pending_payment | Pagamento do pedido cancelado
21 - Boleto pago a menor | payment_review | Recebemos a confirmação de pagamento do seu boleto. Porém o valor pago é divergente do emitido pelo nosso sistema. Por favor entre em contato conosco
22 - Boleto pago a maior | payment_review | Recebemos a confirmação de pagamento do seu boleto. Porém o valor pago é divergente do emitido pelo nosso sistema. Por favor entre em contato conosco


> **Instalação**

**Versões Compatíveis**

O módulo Yapay Gateway é compatível com as versões 1.5.X, 1.6.X, 1.7.X, 1.8.X, 1.9.X da plataforma ecommerce Magento.

**Procedimento**

1 - Para instalar o módulo é necessário baixar o arquivo através da página a seguir:

<a href="https://gateway.yapay.com.br/administrador/plugin_magento.7z" class="btnMagento"><i class="fa fa-arrow-circle-down" aria-hidden="true"></i>Magento</a>


2 - Descompacte o conteúdo do arquivo baixado no diretório raiz de instalação do Magento.

3 - Atualize o cache do Magento, através do item System/Cache Management do administrador do sistema.

![Cache](/images/Cache_Magento.png "Cache")

4 - O módulo está instalado! Para configurar os dados de sua conta do Yapay acesse na área administrativa do Magento o item System/Configuration/Payments Methods, para mais informações

`Observação: Para utilização do Módulo é necessário a habilitação do SoapClient no php.ini.`

> **Configuração**

Após a instalação do Módulo Magento Yapay, clicar em Métodos de pagamento na opção de configuração do Painel do Magento

![Config](/images/MenuMagento.png "Config")

Aparecerá as opção de Formas de pagamento do Yapay.

![Config](/images/ModuloMagento.png "Config")
<br>
![Config](/images/ModuloMagento2.png "Config")






