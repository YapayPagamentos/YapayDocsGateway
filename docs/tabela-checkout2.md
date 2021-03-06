## Transação Simplificada

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
codigoFormaPagamento|	Enviar 997 para Checkout Yapay|	Numérico|	Até 3 dígitos|	Sim

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos *Até 16 dígitos caso utilizar E Rede|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Recomendamos o envio para atualização do pedido
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja aprovada|	Alfa Numérico|	Até 250 caracteres|	Sim
urlRedirecionamentoNaoPago | Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja negada|	Alfa Numérico|	Até 250 caracteres|	Sim
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Não
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Não
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2 |	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre3|	Campo Livre 3| 	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 100 caracteres|	Não

> checkout

Campo | Descrição | Tipo |  Obrigatório
:----- | :---------: | :----: | :-----------------:
versao |	Enviar 2 |	Numérico|	Sim
formasPagamento|	Código das formas de pagamento para disponibilizar no Checkout |	Numérico|	Não
expiracao | Tempo de expiração do link, enviar informação em minutos *Padrão 45 minutos para expiração | Numérico | Não

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Não
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Não
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não

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


**RETORNO**

Campo | Descrição 
:----- | :---------: 
urlPagamento|	URL para redirecionar o consumidor para o Checkout

## Transação com análise de fraude

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
codigoFormaPagamento|	Enviar 997 para Checkout Yapay|	Numérico|	Até 3 dígitos|	Sim

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos *Até 16 dígitos caso utilizar E Rede|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Sugerimos o envio para o recebimento do status atualizado do pedido pós análise da antifraude
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja aprovada|	Alfa Numérico|	Até 250 caracteres|	Para pagamentos redirecionáveis é obrigatório
urlRedirecionamentoNaoPago | Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja negada|	Alfa Numérico|	Até 250 caracteres|	Para pagamentos redirecionáveis é obrigatório
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Sim
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Sim
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2  (Envio do FingerPrint)|	Alfa Numérico|	Até 100 caracteres|	Sim
campoLivre3|	Campo Livre 3 (Envio do canal de venda ClearSale Total/Total Garantido e Application - solicitar ativação para Suporte Yapay)| 	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 100 caracteres|	Não

> checkout

Campo | Descrição | Tipo | Obrigatório
:----- | :---------: | :----: | :-----------------:
versao |	Enviar 2 |	Numérico|	Sim
expiracao | Tempo de expiração do link, enviar informação em minutos *Padrão 45 minutos para expiração | Numérico | Não
formasPagamento|	Código das formas de pagamento para disponibilizar no Checkout |	Numérico|	Não

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
codigoCategoria|	Código que identifica categoria do produto. Caso utilize antifraude Konduto deverá seguir esta [listagem](konduto-categoria.md) para a categoria, qualquer código diferente da listagem será enviado como padrão 9999|	Alfa Numérico|	20 caracteres|	Sim
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

Campo | Descrição 
:----- | :---------: 
urlPagamento|	URL para redirecionar o consumidor para o Checkout

## Múltiplos Boletos

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
codigoFormaPagamento|	Enviar 997 para Checkout Yapay|	Numérico|	Até 3 dígitos|	Sim

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos *Até 16 dígitos caso utilizar E Rede|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Recomendamos o envio para atualização do pedido
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja aprovada|	Alfa Numérico|	Até 250 caracteres|	Sim
urlRedirecionamentoNaoPago | Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja negada|	Alfa Numérico|	Até 250 caracteres|	Sim
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Não
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Não
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2 |	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre3|	Campo Livre 3| 	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 100 caracteres|	Não

> checkout

Campo | Descrição | Tipo | Obrigatório
:----- | :---------: | :----: | :-----------------:
versao |	Enviar 2 |	Numérico|	Sim
expiracao | Tempo de expiração do link, enviar informação em minutos *Padrão 45 minutos para expiração | Numérico | Não
multiploBoleto|	Enviar 1|	Numérico|	Sim
boletos| Nó para informações dos boletos| -| Sim

> boletos

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
valor|	Valor do boleto|	Numérico|	Sim
vencimento|	Vencimento do boleto. Formato dd/mm/aaaa|	Alfa Numérico|	Sim

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Não
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Não
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não

> dadosCobranca

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	Até 100 caracteres|	Sim
documento|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Sim
documento2|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Não
email|	E-mail do comprador|	Alfa Numérico|	20 caracteres|	Sim
codigoCliente|	Código do Comprador|	Alfa Numérico|	20 caracteres|	Não
dataNascimento|	Data Nascimento Comprador|	Alfa Numérico|	10 caracteres|	Não
sexo|	Sexo Comprador|	Alfa Numérico|	2 caracteres|	Não
tipoCliente|	Tipo do Cliente - 1 - Pessoa Física 2 - Pessoa Jurídica|	Numérico|	Até 8 dígitos|	Sim
endereco|	Nó reservado para dados de endereço do comprador|	-|	-|	-
telefone|	Nó reservado para dados de telefone do comprador|	-|	-|	-

`Observação: O envio do nó dadosCobranca é obrigatório.`

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

Campo | Descrição 
:----- | :---------: 
urlPagamento|	URL para redirecionar o consumidor para o Checkout

## OneClick

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento|	Código estabelecimento Yapay|	Numérico|	13 dígitos|	Sim
codigoFormaPagamento|	Enviar 997 para Checkout Yapay|	Numérico|	Até 3 dígitos|	Sim

> transacao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
numeroTransacao|	Código que identifica a transação dentro do Yapay|	Numérico|	Até 19 dígitos *Até 16 dígitos caso utilizar E Rede|	Sim
valor|	Valor da transação. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
valorDesconto|	Valor do desconto da transação. Campo apenas informativo. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Não
parcelas|	Quantidade de parcelas da transação. Verificar se forma de pagamento suporta parcelamento|	Numérico|	Até 2 dígitos|	Sim
urlCampainha|	URL será sempre acionada quando o status do pedido mudar. Deve estar preparada para receber dados de campainha|	Alfa Numérico|	Até 250 caracteres|	Recomendamos o envio para atualização do pedido
urlResultado|	Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja aprovada|	Alfa Numérico|	Até 250 caracteres|	Sim
urlRedirecionamentoNaoPago | Para o modelo de pagamento redirect, O Yapay redirecionará para essa URL no final da transação caso a mesma seja negada|	Alfa Numérico|	Até 250 caracteres|	Sim
ip|	Número do IP do usuário final/cliente. Formato xxx.xxx.xxx.xxx|	Alfa Numérico|	Até 15 caracteres|	Não
idioma|	1 - Português 2 - Inglês 3 - Espanhol|	Numérico|	1 dígito|	Não
campoLivre1|	Campo Livre 1|	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre2|	Campo Livre 2 |	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre3|	Campo Livre 3| 	Alfa Numérico|	Até 100 caracteres|	Não
campoLivre4|	Campo Livre 4	|Alfa Numérico|	Até 100 caracteres|	Não
campoLivre5|	Campo Livre 5|	Alfa Numérico|	Até 100 caracteres|	Não

> checkout

Campo | Descrição | Tipo | Obrigatório
:----- | :---------: | :----: |  :-----------------:
versao |	Enviar 2 |	Numérico|	Sim
formasPagamento|	Código das formas de pagamento para disponibilizar no Checkout |	Numérico|	Não
expiracao | Tempo de expiração do link, enviar informação em minutos *Padrão 45 minutos para expiração | Numérico | Não
oneclick | Enviar 1 para habilitar o oneclick | Numérico | Sim

> itensDoPedido

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
codigoProduto|	Código único que identifica cada produto|	Alfa Numérico|	20 caracteres|	Não
codigoCategoria|	Código que identifica categoria do produto|	Alfa Numérico|	20 caracteres|	Não
nomeProduto|	Nome do Produto |	Alfa Numérico|	100 caracteres|	Não
quantidadeProduto|	Quantidade comprada do produto|	Numérico|	Até 8 dígitos|	Sim
valorUnitarioProduto|	Valor unitário do produto. Deve ser enviado sem pontos ou vírgulas|	Numérico|	Até 10 dígitos|	Sim
nomeCategoria|	Nome da categoria do produto|	Alfa Numérico|	100 caracteres|	Não

> dadosCobranca

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nome|	Nome do comprador|	Alfa Numérico|	Até 100 caracteres|	Recomendamos o envio
documento|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Recomendamos o envio
documento2|	Documento principal do comprador|	Alfa Numérico|	30 caracteres|	Não
email|	E-mail do comprador|	Alfa Numérico|	20 caracteres|	Sim
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


**RETORNO**

Campo | Descrição 
:----- | :---------: 
urlPagamento|	URL para redirecionar o consumidor para o Checkout

