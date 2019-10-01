## Transação simplificada

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento |	Código estabelecimento Yapay |	Numérico|	13 dígitos|	Sim 
codigoFormaPagamento |	[Código da forma de pagamento](tabela-forma-pagamento.md) |	Numérico	|Até 3 dígitos	|Sim
transacao |	Nó reservado para informações da transação|	-|	-|	-
dadosCartao|	Nó reservado para dados de cartão|	-|	-|	-
itensDoPedido|	Nó reservado para informações dos produtos|	-|	-|	-
dadosCobranca|	Nó reservado para informações dos dados de cobrança|	-|	-|	-
telefone|	Nó reservado para informações de telefone|	-|	-|	-
dadosEntrega|	Nó reservado para informações de dados de entrega|	-|	-|	-

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
moeda|	Tipo da moeda. OBS: Disponível ‘USD” apenas para PayPal Internacional|	Alfa Numérico|	Até 10 caracteres|	Não
tipoParcelamento|	Use “E” para estabelecimento, use “A” para administradora. Caso não for enviado será utilizado as configurações do seu estabelecimento|	Alfa Numérico|	1 caracter|	Não
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Não
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação|	Alfa Numérico|	Até 250 caracteres|	Para pagamentos redirecionáveis é obrigatório
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Não
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Não
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2 |	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre3|	Campo Livre 3| 	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 100 caracteres|	Não

> dadosCartao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nomePortador|	Nome do titular do cartão de crédito|	Alfa Numérico|	Até 16 dígitos|	Sim
numeroCartao|	Numero do cartão de crédito, sem espaços ou traços|	Numérico|	Até 22 caracteres|	Sim
codigoSeguranca|	Código de segurança do cartão (campo não é armazenado pelo Yapay)|	Numérico|	Até 4 caracteres|	Sim
dataValidade|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim


> dadosCobranca

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	Até 100 caracteres|	Recomendamos o envio
documento|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Recomendamos o envio
documento2|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Não
email|	E-mail do comprador|	Alfa Numérico|	20 caracteres|	Não
codigoCliente|	Código do Comprador|	Alfa Numérico|	20 caracteres|	Não
dataNascimento|	Data Nascimento Comprador|	Alfa Numérico|	10 caracteres|	Não
sexo|	Sexo Comprador|	Alfa Numérico|	2 caracteres|	Não
tipoCliente|	Tipo do Cliente - 1 - Pessoa Física 2 - Pessoa Jurídica|	Numérico|	Até 8 dígitos|	Não
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

`Observação: O envio do nó dadosCobranca é obrigatório.`

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Não
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Não
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não

> endereco

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
logradouro|	Endereço do comprador|	Alfa Numérico| 40 caracteres |	Não
numero|	Número do comprador|	Alfa Numérico| 10 caracteres|	Não
bairro|	Bairro do comprador|	Alfa Numérico| 20 caracteres |	Não
complemento|	Complemento do endereço|	Alfa Numérico| 40 caracteres|	Não
cidade|	Cidade do comprador|	Alfa Numérico| 20 caracteres |	Não
estado|	Estado do comprador|	Alfa Numérico| 2 caracteres| 	Não
cep|	CEP do comprador|	Alfa Numérico| 10 caracteres|	Não
pais|	País do comprador|	Alfa Numérico| 10 caracteres|	Não

> telefone

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
tipoTelefone|	1 = Outros / 2 = Residencial / 3 = Comercial / 4 = Recados / 5 = Cobrança / 6 = Temporário|	Numérico| 1 dígito|	Não
ddi|	Código DDI do telefone|	Alfa Numérico| 10 caracteres |	Não
ddd|	Código DDD do telefone|	Alfa Numérico| 10 caracrteres |	Não
telefone|	Número do telefone|	Alfa Numérico| 20 caracteres| 	Não

> dadosEntrega

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	20 caracteres|	Não
email| E-mail do comprador|	Alfa Numérico|	20 caracteres|	Não
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos
codigoEstabelecimento|	Código que identifica o estabelecimento dentro do Yapay|	Numérico|	13 dígitos
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md)  |	Numérico|	Até 3 dígitos
valor|	Valor da transação|	Numérico|	Até 10 dígitos
valorDesconto|	Valor desconto|	Numérico|	Até 10 dígitos
taxaEmbarque|	Valor taxa embarque|	Numérico|	Até 10 dígitos
parcelas|	Quantidade de parcelas da transação|	Numérico|	Até 2 dígitos
urlPagamento|	Para o modelo redirect. Essa será a URL de redirecionamento da operação|	Alfa Numérico|	Até 500 caracteres
statusTransacao|	[Status atual da transação](tabela-status.md)|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da adquirente|	Numérico|	Até 20 dígitos
codigoTransacaoOperadora|	Código da transação na adquirente|	Alfa Numérico|	Até 20 dígitos
dataAprovacaoOperadora|	Data de aprovação na adquirente|	Alfa Numérico|	Até 10 dígitos
numeroComprovanteVenda|	Número do comprovante de venda|	Alfa Numérico|	Até 20 dígitos
nsu|	Número do NSU da adquirente|	Alfa Numérico|	Até 20 caracteres
mensagemVenda|	Mensagem de retorno da adquirente|	Alfa Numérico|	Até 50 dígitos
cartoesUtilizados|	Cartões mascarados utilizados na transação|	Alfa Numérico|	Até 20 caracteres


## Transação com análise de fraude

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento |	Código estabelecimento Yapay |	Numérico|	13 dígitos|	Sim 
codigoFormaPagamento |	[Código da forma de pagamento](tabela-forma-pagamento.md)  |	Numérico	|Até 3 dígitos	|Sim
transacao |	Nó reservado para informações da transação|	-|	-|	-
dadosCartao|	Nó reservado para dados de cartão|	-|	-|	-
itensDoPedido|	Nó reservado para informações dos produtos|	-|	-|	-
dadosCobranca|	Nó reservado para informações dos dados de cobrança|	-|	-|	-
telefone|	Nó reservado para informações de telefone|	-|	-|	-
dadosEntrega|	Nó reservado para informações de dados de entrega|	-|	-|	-

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
moeda|	Tipo da moeda. OBS: Disponível ‘USD” apenas para PayPal Internacional|	Alfa Numérico|	Até 10 caracteres|	Não
tipoParcelamento|	Use “E” para estabelecimento, use “A” para administradora. Caso não for enviado será utilizado as configurações do seu estabelecimento|	Alfa Numérico|	1 caracter|	Não
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Sugerimos o envio para o recebimento do status atualizado do pedido pós análise da antifraude
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação|	Alfa Numérico|	Até 250 caracteres|	Para pagamentos redirecionáveis é obrigatório
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Sim
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Sim
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2  (Envio do FingerPrint)|	Alfa Numérico|	Até 100 caracteres|	Sim
campoLivre3|	Campo Livre 3 (Envio do canal de venda ClearSale Total/Total Garantido e Application - solicitar ativação para Suporte Yapay)| 	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 100 caracteres|	Não

> dadosCartao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nomePortador|	Nome do titular do cartão de crédito|	Alfa Numérico|	Até 16 dígitos|	Sim
numeroCartao|	Numero do cartão de crédito, sem espaços ou traços|	Numérico|	Até 22 caracteres|	Sim
codigoSeguranca|	Código de segurança do cartão (campo não é armazenado pelo Yapay)|	Numérico|	Até 4 caracteres|	Sim
dataValidade|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim


> dadosCobranca

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	Até 100 caracteres|	Sim
documento|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Sim
documento2|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Não
email|	E-mail do comprador|	Alfa Numérico|	20 caracteres|	Sim
codigoCliente|	Código do Comprador|	Alfa Numérico|	20 caracteres|	Não
dataNascimento|	Data Nascimento Comprador|	Alfa Numérico|	10 caracteres| Não <br>*Caso utilizar FControl, campo obrigatório
sexo|	Sexo Comprador|	Alfa Numérico|	2 caracteres|	Não
tipoCliente|	Tipo do Cliente - 1 - Pessoa Física 2 - Pessoa Jurídica|	Numérico|	Até 8 dígitos|	Sim
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

`Observação: O envio do nó dadosCobranca é obrigatório.`

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Sim
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Sim
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Sim
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Sim

> endereco

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
logradouro|	Endereço do comprador|	Alfa Numérico| 40 caracteres |	Sim
numero|	Número do comprador|	Alfa Numérico| 10 caracteres|	Sim
bairro|	Bairro do comprador|	Alfa Numérico| 20 caracteres |	Sim
complemento|	Complemento do endereço|	Alfa Numérico| 40 caracteres|	Não
cidade|	Cidade do comprador|	Alfa Numérico| 20 caracteres |	Sim
estado|	Estado do comprador|	Alfa Numérico| 2 caracteres| 	Sim
cep|	CEP do comprador|	Alfa Numérico| 10 caracteres|	Sim
pais|	País do comprador|	Alfa Numérico| 10 caracteres|	Não

> telefone

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
tipoTelefone|	1 = Outros / 2 = Residencial / 3 = Comercial / 4 = Recados / 5 = Cobrança / 6 = Temporário|	Numérico| 1 dígito|	Sim
ddi|	Código DDI do telefone|	Alfa Numérico| 10 caracteres |	Não
ddd|	Código DDD do telefone|	Alfa Numérico| 10 caracrteres |	Sim
telefone|	Número do telefone|	Alfa Numérico| 20 caracteres| 	Sim

> dadosEntrega

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome recebedor|	Alfa Numérico|	20 caracteres|	Não *Obrigatório caso utilizar ClearSale
email| E-mail do recebedor|	Alfa Numérico|	20 caracteres|	Não *Obrigatório caso utilizar ClearSale
documento|	Documento principal do recebedor|	Alfa Numérico|	30 caracteres|	Não *Obrigatório caso utilizar ClearSale
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos
codigoEstabelecimento|	Código que identifica o estabelecimento dentro do Yapay|	Numérico|	13 dígitos
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md)  |	Numérico|	Até 3 dígitos
valor|	Valor da transação|	Numérico|	Até 10 dígitos
valorDesconto|	Valor desconto|	Numérico|	Até 10 dígitos
taxaEmbarque|	Valor taxa embarque|	Numérico|	Até 10 dígitos
parcelas|	Quantidade de parcelas da transação|	Numérico|	Até 2 dígitos
urlPagamento|	Para o modelo redirect. Essa será a URL de redirecionamento da operação|	Alfa Numérico|	Até 500 caracteres
statusTransacao|	[Status atual da transação](tabela-status.md)|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da adquirente|	Numérico|	Até 20 dígitos
codigoTransacaoOperadora|	Código da transação na adquirente|	Alfa Numérico|	Até 20 dígitos
dataAprovacaoOperadora|	Data de aprovação na adquirente|	Alfa Numérico|	Até 10 dígitos
numeroComprovanteVenda|	Número do comprovante de venda|	Alfa Numérico|	Até 20 dígitos
nsu|	Número do NSU da adquirente|	Alfa Numérico|	Até 20 caracteres
mensagemVenda|	Mensagem de retorno da adquirente|	Alfa Numérico|	Até 50 dígitos
cartoesUtilizados|	Cartões mascarados utilizados na transação|	Alfa Numérico|	Até 20 caracteres

## Transação com múltiplos cartões

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento |	Código estabelecimento Yapay |	Numérico|	13 dígitos|	Sim 
codigoFormaPagamento |	[Código da forma de pagamento](tabela-forma-pagamento.md)  |	Numérico	|Até 3 dígitos	|Sim
transacao |	Nó reservado para informações da transação|	-|	-|	-
dadosMultiplosCartoes | Nó reservado para dados de cartão| -| -|-
itensDoPedido|	Nó reservado para informações dos produtos|	-|	-|	-
dadosCobranca|	Nó reservado para informações dos dados de cobrança|	-|	-|	-
telefone|	Nó reservado para informações de telefone|	-|	-|	-
dadosEntrega|	Nó reservado para informações de dados de entrega|	-|	-|	-

> dadosMultiplosCartoes

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nomePortador|	Nome do titular do cartão de crédito|	Alfa Numérico|	Até 16 dígitos|	Sim
numeroCartao|	Numero do cartão de crédito, sem espaços ou traços|	Numérico|	Até 22 caracteres|	Sim
codigoSeguranca|	Código de segurança do cartão (campo não é armazenado pelo Yapay)|	Numérico|	Até 4 caracteres|	Sim
dataValidade|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim
codigoFormaPagamento |	[Código da forma de pagamento](tabela-forma-pagamento.md)  |	Numérico	|Até 3 dígitos	|Sim
parcelas| Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento| Numérico|	Até 2 dígitos|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos|	Sim
moeda|	Tipo da moeda. OBS: Disponível ‘USD” apenas para PayPal Internacional|	Alfa Numérico|	Até 10 caracteres|	Não
tipoParcelamento|	Use “E” para estabelecimento, use “A” para administradora. Caso não for enviado será utilizado as configurações do seu estabelecimento|	Alfa Numérico|	1 caracter|	Não
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Não
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação|	Alfa Numérico|	Até 250 caracteres|	Não
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Não
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Sim
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2 |	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre3|	Campo Livre 3 | Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4 | Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5 |	Alfa Numérico|	Até 100 caracteres|	Não

> dadosCobranca

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	Até 100 caracteres|	Sim
documento|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Sim
documento2|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Não
email|	E-mail do comprador|	Alfa Numérico|	20 caracteres|	Não
codigoCliente|	Código do Comprador|	Alfa Numérico|	20 caracteres|	Não
dataNascimento|	Data Nascimento Comprador|	Alfa Numérico|	10 caracteres|	Não
sexo|	Sexo Comprador|	Alfa Numérico|	2 caracteres|	Não
tipoCliente|	Tipo do Cliente - 1 - Pessoa Física 2 - Pessoa Jurídica|	Numérico|	Até 8 dígitos|	Sim
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

`Observação: O envio do nó dadosCobranca é obrigatório.`

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Sim
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Sim
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não

> endereco

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
logradouro|	Endereço do comprador|	Alfa Numérico| 40 caracteres |	Não
numero|	Número do comprador|	Alfa Numérico| 10 caracteres|	Não
bairro|	Bairro do comprador|	Alfa Numérico| 20 caracteres |	Não
complemento|	Complemento do endereço|	Alfa Numérico| 40 caracteres|	Não
cidade|	Cidade do comprador|	Alfa Numérico| 20 caracteres |	Não
estado|	Estado do comprador|	Alfa Numérico| 2 caracteres| 	Não
cep|	CEP do comprador|	Alfa Numérico| 10 caracteres|	Não
pais|	País do comprador|	Alfa Numérico| 10 caracteres|	Não

> telefone

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
tipoTelefone|	1 = Outros / 2 = Residencial / 3 = Comercial / 4 = Recados / 5 = Cobrança / 6 = Temporário| Numérico| 1 dígito| Não
ddi|	Código DDI do telefone|	Alfa Numérico| 10 caracteres |	Não
ddd|	Código DDD do telefone|	Alfa Numérico| 10 caracrteres |	Não
telefone|	Número do telefone|	Alfa Numérico| 20 caracteres| 	Não

> dadosEntrega

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	20 caracteres|	Não
email| E-mail do comprador|	Alfa Numérico|	20 caracteres|	Não
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos
codigoEstabelecimento|	Código que identifica o estabelecimento dentro do Yapay|	Numérico|	13 dígitos
multiploCartao | Retornará 1 | Numérico | 1 dígito
statusTransacao|	[Status atual da transação](tabela-status.md)|	Numérico|	Até 2 dígitos
detalhesMultiploCartao | Nó reservado para retornos de cartão | - | -

> detalhesMultiploCartao

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------:
codigoFormaPagamento |	[Código da forma de pagamento](tabela-forma-pagamento.md)  |	Numérico	|Até 3 dígitos	
valor|	Valor da transação|	Numérico|	Até 10 dígitos
valorDesconto|	Valor desconto|	Numérico|	Até 10 dígitos
parcelas|	Quantidade de parcelas da transação|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da adquirente|	Numérico|	Até 20 dígitos
codigoTransacaoOperadora|	Código da transação na adquirente|	Alfa Numérico|	Até 20 dígitos
dataAprovacaoOperadora|	Data de aprovação na adquirente|	Alfa Numérico|	Até 10 dígitos
numeroComprovanteVenda|	Número do comprovante de venda|	Alfa Numérico|	Até 20 dígitos
nsu|	Número do NSU da adquirente|	Alfa Numérico|	Até 20 caracteres
mensagemVenda|	Mensagem de retorno da adquirente|	Alfa Numérico|	Até 50 dígitos
