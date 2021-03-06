## Cadastro OneClick

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
formaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md)|	Numérico|	Até 3 dígitos|	Sim
nomeTitularCartaoCredito|	Nome titular do cartão de crédito/débito|	Alfa Numérico|	Até 30 caracteres|	Sim
numeroCartaoCredito|	Numero do cartão de crédito/débito, sem espaços ou traços|	Numérico|	Até 22 dígitos|	Sim
dataValidadeCartao|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim
emailComprador|	Email do comprador|	Alfa Numérico|	20 caracteres|	Não

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos
formaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md)|	Numérico|	Até 3 dígitos
oneClick|	Retornará 1 para cadastro criado|	Numérico|	1 dígito
token|	Token criado|	Alfa Numérico|	Até 60 caracteres
nomeTitularCartaoCredito|	Nome titular do cartão de crédito/débito|	Alfa Numérico|	Até 16 caracteres
numeroCartaoCredito|	Numero do cartão de crédito/débito, sem espaços ou traços|	Numérico|	Até 22 dígitos
dataValidadeCartao|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres
emailComprador|	Email do comprador|	Alfa Numérico|	20 caracteres

## Alterar OneClick

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho  | Obrigatório
:----- | :---------: | :----: | :-------: | :-------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md)|	Numérico|	Até 3 dígitos|	Sim
nomeTitularCartao|	Nome titular do cartão de crédito/débito|	Alfa Numérico	|Até 30 caracteres|	Sim
numeroCartaoCredito|	Numero do cartão de crédito/débito, sem espaços ou traços|	Numérico|	Até 22 dígitos|	Sim
dataValidadeCartao|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim
emailComprador	|Email do comprador|	Alfa Numérico|	20 caracteres|	Não

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos
codigoFormaPagamento|	Código da forma de pagamento|	Numérico|	Até 3 dígitos
oneClick|	Retornará 1 para cadastro criado|	Numérico|	1 dígito
token|	Token	Alfa Numérico	Até 60 caracteres|
nomeTitularCartao|	Nome titular do cartão de crédito/débito|	Alfa Numérico|	Até 16 caracteres
numeroCartaoCredito|	Numero do cartão de crédito/débito, sem espaços ou traços|	Numérico|	Até 22 dígitos
dataValidadeCartao|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres
emailComprador|	Email do comprador|	Alfa Numérico|	20 caracteres

## Pagamento OneClick

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento |	Código estabelecimento Yapay |	Numérico|	13 dígitos|	Sim 
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md). Se for enviado, forma de pagamento será atualizada no token|	Numérico|	Até 3 dígitos|	Não
transacao |	Nó reservado para informações da transação|	-|	-|	-
dadosCartao|	Nó reservado para dados de cartão|	-|	-|	-
itensDoPedido|	Nó reservado para informações dos produtos|	-|	-|	-
dadosCobranca|	Nó reservado para informações dos dados de cobrança|	-|	-|	-
telefone|	Nó reservado para informações de telefone|	-|	-|	-
dadosEntrega|	Nó reservado para informações de dados de entrega|	-|	-|	-

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos *Até 16 dígitos caso utilizar E Rede|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
moeda|	Tipo da moeda. OBS: Disponível ‘USD” apenas para PayPal Internacional|	Alfa Numérico|	Até 10 caracteres|	Não
tipoParcelamento|	Use “E” para estabelecimento, use “A” para administradora. Caso não for enviado será utilizado as configurações do seu estabelecimento|	Alfa Numérico|	1 caractere|	Não
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Recomendamos o envio para atualização do pedido
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação|	Alfa Numérico|	Até 250 caracteres| Sim
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
codigoSeguranca|	Código de segurança do cartão (campo não é armazenado pelo Yapay)|	Numérico|	Até 4 caracteres|	Sim

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

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Não
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Não
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não


**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos *Até 16 dígitos caso utilizar E Rede
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md)|	Numérico|	Até 3 dígitos
valor|	Valor da transação.|	Numérico|	Até 10 dígitos
valorDesconto|	Valor desconto|	Numérico|	Até 10 dígitos
parcelas|	Quantidade de parcelas da transação|	Numérico|	Até 2 dígitos
oneClick|	1 para OneClick|	Numérico	1 dígito|
token|	Token utilizado para o pagamento|	Alfa Numérico|	Até 60 caracter
statusTransacao|	Status atual da transação|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da adquirente|	Alfa Numérico|	Até 20 caracter
codigoTransacaoOperadora|	Código da transação na adquirente| Alfa	Numérico|	Até 20 caracter
dataAprovacaoOperadora|	Data de retorno na adquirente|	Alfa Numérico|	Até 10 caracter
numeroComprovanteVenda|	Número do comprovante de venda|	Alfa Numérico|	Até 20 caracter
mensagemVenda|	Mensagem de retorno da adquirente|	Alfa Numérico|	Até 256 caracter

