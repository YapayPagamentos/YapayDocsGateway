## Status transação

Código | Nome | Descrição
------ | -----|------------
1|	Pago e Capturado|	Transação está autorizada e confirmada na instituição financeira
2|	Pago e Não Capturado|	Transação está apenas autorizada, aguardando confirmação (captura)
3|	Não Pago|	Transação negada pela instituição financeira
5|	Transação em Andamento|	Comum para pagamentos cartão redirect ou pagamentos com autenticação
8|	Aguardando Pagamento|	Comum para pagamentos com boletos e pedidos em reprocessamento
9|	Falha na Operadora|	Houve um problema no processamento com a adquirente
13|	Cancelada|	Transação cancelada na adquirente
14|	Estornada|	A venda foi estornada na adquirente
15|	Em Análise de Fraude|	A transação foi enviada para o sistema de análise de riscos. Status transitório
17|	Recusado pelo AntiFraude|	A transação foi negada pelo sistema análise de risco
18|	Falha na Antifraude|	Falha. Não foi possível enviar pedido para a análise de Risco, porém será reenviado
21|	Boleto Pago a menor|	O boleto foi pago com valor menor do emitido
22|	Boleto Pago a maior|	O boleto foi pago com valor maior do emitido
23|	Estorno Parcial|	A venda estonada na adquirente parcialmente
24|	Estorno Não Autorizado|	O Estorno não foi autorizado pela adquirente
25|	Falha no estorno|	Falha ao enviar estorno para a operadora
27|	Cancelamento parcial|	Pedido parcialmente cancelado na adquirente
31|	Transação já Paga|	Transação já existente e finalizada na adquirente
40|	Aguardando Cancelamento|	Processo de cancelamento em andamento

## Formas de Pagamento

> **CARTÕES**

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
350|	Visa|Crédito|	StoneWs|	Stone|	WebService
351|	MasterCard|Crédito|	StoneWs|	Stone|	WebService
352|    Hipercard | Crédito| StoneWs | Stone | WebService
353|    Elo | Crédito| StoneWs | Stone | WebService
380|	Visa|Crédito|	BinWS|	Bin-FirstData|	WebService
381|	MasterCard|Crédito|	BinWS|	Bin-FirstData|	WebService
382|	Cabal|Crédito|	BinWS|	Bin-FirstData|	WebService

> **BOLETOS E TRANSFERÊNCIAS**

**Modalidade Online** 

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
104|	Bradesco|	Transferência|	Bradesco Shopfacil
105|	Bradesco|	Boleto Online|	Bradesco ShopFácil

**Modalidade Offline**

Código | Banco | Modalidade | Tecnologia 
------ | -------- |----- | ------------
28|	Banco do Brasil|	Boleto Offline|	Banco do Brasil
29|	Itaú|	Boleto Offline|	Itaú
30|	Bradesco|	Boleto Offline|	Bradesco
34|	Caixa Econômica Federal |	Boleto Offline|	Caixa Econômica Federal
41|	Santander|	Boleto Offline|	Santander
48|	Banco do Brasil|	Boleto Offline com registro|	Banco do Brasil

> **INTERMEDIÁRIOS FINANCEIROS**

Código | Intermediador 
------ | -------- 
39|	PagSeguro
111|	PayPal Nacional
112|	PayPal Internacional
155|	SafetyPay




