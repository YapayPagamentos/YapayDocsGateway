# Link de pagamento por email

Com esta funcionalidade habilitada ao estabelecimento, além do link de pagamento ser retornado via API, também será enviado via email ao comprador, com um template padrão do Yapay, caso não exista nenhum cadastrado.

*Será enviado apenas um email com o link, é importante o estabelecimento utilizar o recurso de [campainha](notificacao-comum.md) para informar o status do pagamento ao comprador.


## Cadastrar template

<span class="post">PUT</span>

API que possibilita o cadastro do template de email.
Disponibilizamos [palavras especiais](palavras-email.md) para compor o texto do email.

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/«codigoEstabelecimento»/inclui
Produção |https://gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/«codigoEstabelecimento»/inclui


> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/100000000000/inclui
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
    {
    "layout": {
    "assunto": "PEDIDO #_pedido_numero_#" REALIZADO COM SUCESSO,
    "conteudo": "<html><body><p>Obrigado por sua compra: <strong>#_pedido_numero_#</strong></p><br /><p>Clique na URL <strong>#_pedido_url_#</strong> para efetuar o pagamento do seu pedido</p><br><p><strong>Dados do Pedido</strong><br /><strong>Data: </strong>#_pedido_data_#<br /><strong>Total:</strong>#_pedido_valor_#</p><strong>Produtos:</strong><ul>#_item_[<li>#_descricao_#: #_valor_#</li>]_#</ul></body></html>"
  }
}
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
      {
       "mensagem": "Layout cadastrado"
      }
```

## Consultar

<span class="post">GET</span>

API para consultar um template já cadastrado

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/«codigoEstabelecimento»/
Produção |https://gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/«codigoEstabelecimento»/


> **Exemplo de envio em JSON**

```curl
curl
  --request GET https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/100000000000/
  --user usuario:senha 
  --header "Content-Type: application/json"
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/json"
      {
    "assunto": "PEDIDO #_pedido_numero_# REALIZADO COM SUCESSO",
    "conteudo": "<html><body><p>Obrigado por sua compra: <strong>#_pedido_numero_#</strong></p><br /><p>Clique na URL <strong>#_pedido_url_#</strong> para efetuar o pagamento do seu pedido</p><br><p><strong>Dados do Pedido</strong><br /><strong>Data: </strong>#_pedido_data_#<br /><strong>Total:</strong>#_pedido_valor_#</p><strong>Produtos:</strong><ul>#_item_[<li>#_descricao_#: #_valor_#</li>]_#</ul></body></html>"
}
```

## Remover template

<span class="post">PUT</span>

API para remover template cadastrado

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/«codigoEstabelecimento»/remove
Produção |https://gateway.yapay.com.br/checkout/api/v3/estabelecimento/layout/«codigoEstabelecimento»/remove


> **Exemplo de envio em JSON**

```curl
curl
  --request PUT https://sandbox.gateway.yapay.com.br/checkout/api/v3/estabelecimento/imagem/100000000000/remove
  --user usuario:senha 
  --header "Content-Type: application/x-www-form-urlencoded"
  --data-binary
```

> **Exemplo de retorno em JSON**

```curl
  --header "Content-Type: application/x-www-form-urlencoded"
      {
       "mensagem": "Layout removido"
      }
```
