# Validação de cartão

**REQUISIÇÃO**

Campo | Descrição | Tipo | Tamanho | Obrigatório 
:----- | :---------: | :----: | :-------: | :-----------------:
codigoEstabelecimento |	Código estabelecimento Yapay |	Numérico|	13 dígitos|	Sim 
codigoFormaPagamento |	[Código da forma de pagamento](tabela-forma-pagamento.md) |	Numérico	|Até 3 dígitos	|Sim
dadosCartao|	Nó reservado para dados de cartão|	-|	-|	-


> dadosCartao

Campo | Descrição | Tipo | Tamanho | Obrigatório
:----- | :---------: | :----: | :-------: | :-----------------:
nomePortador|	Nome do titular do cartão de crédito|	Alfa Numérico|	Até 16 dígitos|	Sim
numeroCartao|	Numero do cartão de crédito, sem espaços ou traços|	Numérico|	Até 22 caracteres|	Sim
codigoSeguranca|	Código de segurança do cartão (campo não é armazenado pelo Yapay)|	Numérico|	Até 4 caracteres|	Sim
dataValidade|	Data de validade do cartão. Formato mm/yyyy|	Alfa Numérico|	7 caracteres|	Sim


**RETORNO**

Campo | Descrição | Tipo | Tamanho 
:----- | :---------: | :----: | :-------: 
valid |	true = cartão válido ou false =  cartão inválido | Alfa Numérico | Até 5 caracteres
messages|	Lista com parâmetros key e value|	List|	-


