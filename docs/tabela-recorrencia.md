## Criação de recorrência

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento |	Código estabelecimento Yapay |	Numérico|	13 dígitos|	Sim 
recorrencia |	Nó reservado para informações da recorrencia|	-|	-|	-

> recorrencia

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroRecorrencia|	Número da Recorrência deve ser único|	Numérico|	Até 15 dígitos|	Sim
estabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
valor|	Valor da recorrência. Não devem ser utilizados virgulas nem pontos|	Numérico|	Até 10 dígitos	|Sim
modalidade|	Modalidade do pagamento, enviar 1|	Alfa Numérico|	1 caracter|	Sim
formaPagamento|[Código da forma de pagamento](tabela-forma-pagamento.md) |	Numérico|	Até 3 dígitos|	Sim
dadosCartao|	Nó reservado para os dados de cartão|	-|	-|	-
dadosCobranca|	Nó reservado para os dados de cobrança|	-|	-|	-
dadosEntrega|	Nó reservado para os dados de entrega	|-|	-|	-
itensDoPedido|	Nó reservado para informações dos produtos|	-|	-|	-
quantidadeCobrancas|	Quantidade de cobranças, caso 0 a recorrência será feita até que ocorra um cancelamento|	Numérico|	Até 10 dígitos|	Sim
dataPrimeiraCobranca|	Data para a primeira cobrança. Formato dd/mm/aaaa|	Alfa Numérico|	10 caracteres|	Sim
periodicidade|	1 – Semanal, 2 – Quinzenal, 3 – Mensal, 4 – Bimestral, 5 – Trimestral, 6 – Semestral e 7 – Anual|	Alfa Numérico|	1 caracter|	Sim
urlNotificacao|	URL para notificação de cada cobrança da recorrência|	Alfa Numérico|	Até 200 caracteres|	Recomendamos o envio para atualização do pedido
processarImediatamente|	true – A recorrência será processada imediatamente ao cadastro <br>false - A recorrência não será processada no cadastro|	Booleano|	4 caracteres|	Sim
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre3|	Campo Livre 3|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4|	Alfa Numérico|	Até 100 caracteres|	Não
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
nomeComprador|	Nome do comprador|	Alfa Numérico|	Até 100 caracteres|	Recomendamos o envio
documento | Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Recomendamos o envio
emailComprador|	E-mail do comprador|	Alfa Numérico|	Até 100 caracteres|	Não
enderecoComprador|	Logrodouro do comprador|	Alfa Numérico|	Até 100 caracteres|	Não
bairroComprador|	Bairro do comprador|	Alfa Numérico|	Até 50 caracteres|	Não
complementoComprador|	Complemento do endereço comprador|	Alfa Numérico|	Até 50 caracteres|	Não
cidadeComprador|	Cidade do comprador|	Alfa Numérico|	Até 50 caracteres|	Não
estadoComprador|	Estado do comprador|	Alfa Numérico|	Até 2 caracteres|	Não
cepComprador|	CEP do comprador. Enviar sem traços ou espaços|	Alfa Numérico|	Até 10 caracteres|	Não
paisComprador|	Pais do comprador|	Alfa Numérico|	Até 50 caracteres|	Não
telefone|	Lista de Telefones|	-|	-|	-
tipoCliente|	Tipo do Cliente - 1 - Pessoa Física 2 - Pessoa Jurídica|	Alfa Numérico|	1 dígito|	Sim


> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Não
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Não
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não


> telefone

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
tipoTelefone|	1 = Outros / 2 = Residencial / 3 = Comercial / 4 = Recados / 5 = Cobrança / 6 = Temporário|	Numérico| 1 dígito|	Sim
ddi|	Código DDI do telefone|	Alfa Numérico| 10 caracteres |	Não
ddd|	Código DDD do telefone|	Alfa Numérico| 10 caracrteres |	Não
telefone|	Número do telefone|	Alfa Numérico| 20 caracteres| 	Não

> dadosEntrega

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nomeEntrega|	Nome de entegra|	Alfa Numérico|	Até 100 caracteres|	Não
emailEntrega|	Email de entrega|	Alfa Numérico|	Até 100 caracteres|	Não
enderecoEntrega|	Logradouro de entrega|	Alfa Numérico|	Até 100 caracteres|	Não
bairroEntrega|	Bairro de entrega|	Alfa Numérico|	Até 50 caracteres|	Não
complementoEntrega|	Complemento do endereço de entrega|	Alfa Numérico|	Até 50 caracteres|	Não
cidadeEntrega|	Cidade de entrega|	Alfa Numérico|	Até 50 caracteres|	Não
estadoEntrega|	Estado de entrega|	Alfa Numérico|	2 caracteres|	Não
cepEntrega|	CEP de entrega. Enviar sem traços ou espaços	|Alfa Numérico|	Até 10 caracteres|	Não
paisEntrega|	Pais de entrega|	Alfa Numérico|	Até 50 caracteres|	Não
telefone|	Lista de Telefones|	-|	-|	-

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
numeroRecorrencia|	Número da Recorrência|	Numérico|	Até 15 dígitos
estabelecimento|	Código do estabelecimento Yapay|	Numérico|	13 dígitos
valor|	Valor|	Numérico|	Até 10 dígitos
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md) |	Numérico|	Até 3 dígitos
numeroCobrancaTotal|	Quantidade máxima de cobranças|	Numérico|	Até 10 dígitos
numeroCobrancaRestantes|	Quantidade de cobranças restantes|	Numérico|	Até 10 dígitos
status|	Status da ação realizada, 0 para processo feito com sucesso|	Numérico|	1 dígito
mensagem|	Mensagem da recorrência|	Alfa Numérico|	Até 50 caracteres
numeroPedido|	Número da Cobrança Recorrente|	Numérico|	Até 19 dígitos
statusTransacao|	[Status atual da cobrança recorrente](tabela-status.md)|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da Adquirente|	Alfa Numérico|	Até 20 caracteres
codigoTransacaoOperadora|	Código de retorno da adquirente|	Alfa Numérico|	Até 20 caracteres
dataAprovacaoOperadora|	Data aprovação Adquirente|	Alfa Numérico|	Até 10 caracteres
numeroComprovanteVenda|	Número Comprovante Adquirente|	Alfa Numérico|	Até 20 caracteres
mensagemVenda|	Mensagem Venda Adquirente|	Alfa Numérico|	Até 50 caracteres

## Alteração recorrência

**REQUISIÇÃO DIA COBRANÇA**

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
diaCobranca|	Novo dia da cobrança recorrente|	Numérico|	Até 2 dígitos|Sim

**REQUISIÇÃO VALOR**

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
valor|	Novo valor da recorrência|	Numérico|	Até 10 dígitos|Sim

**REQUISIÇÃO DADOS DE CARTÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
formaPagamento | Forma de pagamento já cadastrada ou nova forma de pagamento | Numérico | Até 3 dígitos | Sim
nomePortador|	Nome do titular do cartão de crédito|	Alfa Numérico|	Até 16 dígitos|	Sim
numeroCartao|	Numero do cartão de crédito, sem espaços ou traços|	Numérico|	Até 22 caracteres|	Sim
dataValidade|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
tipo|	Tipo da integração|	Alfa Numérico|	4 caracteres
periodicidade|	Periodicidade da cobrança|	Alfa Numérico|	Até 10 caracteres
codigoEstabelecimento|	Código do estabelecimento|	Numérico|	13 dígitos
numero|	Número da recorrência|	Numérico|	Até 15 dígitos
ativo|	Status da recorrência|	Boleano|	Até 4 caracteres
dataCriacao|	Data da criação da recorrência	|Alfa Numérico	|Até 20 caracteres
formaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md) |	Numérico|	Até 3 dígitos
formaPagamentoDescricao|	Descrição da forma de pagamento|	Alfa Numérico|	Até 50 caracteres
valor|	Valor da Recorrência|	Numérico|	Até 10 dígitos
quantidadeCobranca|	Quantidade de cobranças|	Numérico|	Até 10 dígitos
numeroCobrancaRestantes|	Quantidade das cobranças restantes|	Numérico|	Até 10 dígitos
diaCobranca|	Dia da cobrança	|Numérico|	Até 10 dígitos
mesCobranca|	Mês da cobrança, retorna apenas para SOAP|	Numérico|	Até 10 dígitos
primeiraCobranca|	1 – Cobrança no mês corrente 2 – Cobrança no próximo mês Retorna apenas para SOAP|	Numérico|	1 dígito
detalhes|	-|	-|	 
logs|	-|	-|	 
periodicidadeCodigo|	Código da periodicidade|	Numérico|	1 dígito

## Cancelar recorrência

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroRecorrencia|	Número da Recorrência a ser cancelada|	Numérico| Sim
estabelecimento|	Código estabelecimento Yapay|	Numérico|Sim
acao	|Ação para realizar o processamento|	“cancelar”|Sim

**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
numeroRecorrencia|	Número da Recorrência|	Numérico|	Até 15 dígitos
estabelecimento|	Código do estabelecimento Yapay|	Numérico|	13 dígitos
valor|	Valor|	Numérico|	Até 10 dígitos
codigoFormaPagamento|	[Código da forma de pagamento](tabela-forma-pagamento.md) |	Numérico|	Até 3 dígitos
numeroCobrancaTotal|	Quantidade máxima de cobranças|	Numérico|	Até 10 dígitos
numeroCobrancaRestantes|	Quantidade de cobranças restantes|	Numérico|	Até 10 dígitos
status|	Status da ação realizada, 0 para processo feito com sucesso|	Numérico|	1 dígito
mensagem|	Mensagem da recorrência|	Alfa Numérico|	Até 50 caracteres
numeroPedido|	Número da Cobrança Recorrente|	Numérico|	Até 19 dígitos
statusTransacao|	[Status atual da cobrança recorrente](tabela-status.md)|	Numérico|	Até 2 dígitos
autorizacao|	Código de autorização da Adquirente|	Alfa Numérico|	Até 20 caracteres
codigoTransacaoOperadora|	Código de retorno da adquirente|	Alfa Numérico|	Até 20 caracteres
dataAprovacaoOperadora|	Data aprovação Adquirente|	Alfa Numérico|	Até 10 caracteres
numeroComprovanteVenda|	Número Comprovante Adquirente|	Alfa Numérico|	Até 20 caracteres
mensagemVenda|	Mensagem Venda Adquirente|	Alfa Numérico|	Até 50 caracteres

