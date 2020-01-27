# Validação de cartão

<span class="post">POST</span>

API que permite uma validação prévia do cartão do portador para saber se o mesmo é válido, ates do processamento da autorização.

Importante salientar que esta API não analisa:

1. Limite de crédito do cartão
2. Informações sobre o portador
3. Não aciona a base bancária (dispara SMS ao portador)

Lista das adquirentes e bandeiras de crédito disponíveis:

Adquirente | Bandeira
---------- | ---------
Cielo | Visa, MasterCard, Elo
Rede | Visa, MasterCard, Elo, Hiper e HiperCard
GetNet | Visa, Mastercard e HiperCard

> **EndPoints**

Ambiente | Endereço
-------- | ---------
Sandbox  |https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/zeroauth
Produção |https://gateway.yapay.com.br/checkout/api/v3/transacao/zeroauth


**Para maiores informações sobre a estrutura, [acesse aqui](tabela-api-validar.md)


## Cielo

A validação de cartão está disponível para as bandeiras de crédito da Cielo 3.0: 
**Visa, Mastercard e Elo**

<br>** No momento a Cielo não possui o zero auth disponível em sandbox


> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/zeroauth
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
{
    "codigoEstabelecimento": 1000000000000,
    "codigoFormaPagamento": 170,
    "dadosCartao": {
        "nomePortador": "Titular de Teste",
        "numeroCartao": "0000000000000001",
        "codigoSeguranca": "123",
        "dataValidade": "01/2022"
    }
}
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
{
    "valid": true,
    "messages": [
        {
            "key": "00",
            "value": "Transação autorizada"
        }
    ]
}
```

O campo `<valid>` informará se o cartão é valido ou não.
Caso o retorno for false, poderá identificar o motivo através do campo `<key>` e `<value>`

Abixo tabela de códigos e descrições da Cielo:

Key | Value
--- | --------
00 | Transação autorizada
57 | Autorização negada ou bandeira inválida
322 | Zero Dollar Auth is not enabled
324 | Affiliation not found
389 | Restrição cadastral

## Rede

A validação de cartão está disponível para as bandeiras de crédito do E Rede: 
**Visa, Mastercard, Elo, Hiper e Hipercard**

> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/zeroauth
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
{
    "codigoEstabelecimento": 1000000000000,
    "codigoFormaPagamento": 190,
    "dadosCartao": {
        "nomePortador": "Titular de Teste",
        "numeroCartao": "4235647728025682",
        "codigoSeguranca": "123",
        "dataValidade": "01/2022"
    }
}
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
{
    "valid": true,
    "messages": [
        {
            "key": "174",
            "value": "Zero dollar transaction success."
        }
    ]
}
```

O campo `<valid>` informará se o cartão é valido ou não.

Abixo tabela de códigos e descrições da Rede:

Key | Value
--- | --------
170 | Zero dollar transaction not allowed for this card
174 | Zero dollar transaction success
175 | Zero dollar transaction denied

## GetNet

A validação de cartão está disponível para as bandeiras de crédito da GetNet: 
**Visa, Mastercard e Hipercard**

> **Exemplo de envio em JSON**

```curl
curl
  --request POST https://sandbox.gateway.yapay.com.br/checkout/api/v3/transacao/zeroauth
  --header "Content-Type: application/json"
  --user usuario:senha
  --data-binary
{
    "codigoEstabelecimento": 1000000000000,
    "codigoFormaPagamento": 270,
    "dadosCartao": {
        "nomePortador": "Titular de Teste",
        "numeroCartao": "4012001038166662",
        "codigoSeguranca": "123",
        "dataValidade": "01/2022"
    }
}
```

> **Exemplo de retorno em JSON**

```curl
--header "Content-Type: application/json"
{
    "valid": true,
    "messages": [
        {
            "key": "00",
            "value": "VERIFIED"
        }
    ]
}
```

O campo `<valid>` informará se o cartão é valido ou não.

Abixo tabela de códigos e descrições da GetNet:

Key | Value
--- | --------
00 | Verified
N7 | Not Verified


