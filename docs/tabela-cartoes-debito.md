# Transação simplificada

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
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Recomendamos o envio para atualização do pedido
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação|	Alfa Numérico|	Até 250 caracteres| Sim
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Não
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Não
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 16 caracteres|	Não
campoLivre2|	Campo Livre 2 |	Alfa Numérico|	Até 16 caracteres|	Não
campoLivre3|	Campo Livre 3| 	Alfa Numérico|	Até 16 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 16 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 16 caracteres|	Não

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
urlPagamento|	URL de redirecionamento para autenticação bancária |	Alfa Numérico|	Até 500 caracteres
statusTransacao|	[Status atual da transação](tabela-status.md)|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da adquirente|	Numérico|	Até 20 dígitos
codigoTransacaoOperadora|	Código da transação na adquirente|	Numérico|	Até 20 dígitos
dataAprovacaoOperadora|	Data de aprovação na adquirente|	Alfa Numérico|	Até 10 dígitos
numeroComprovanteVenda|	Número do comprovante de venda|	Alfa Numérico|	Até 20 dígitos
nsu|	Número do NSU da adquirente|	Alfa Numérico|	Até 20 caracteres
mensagemVenda|	Mensagem de retorno da adquirente|	Alfa Numérico|	Até 50 dígitos
cartoesUtilizados|	Cartões mascarados utilizados na transação|	Alfa Numérico|	Até 20 caracteres



