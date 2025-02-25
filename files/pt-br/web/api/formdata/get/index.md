---
title: FormData.get()
slug: Web/API/FormData/get
translation_of: Web/API/FormData/get
---
{{APIRef("XMLHttpRequest")}}

O método get() da interface {{domxref("FormData")}} retorna o primeiro valor associado com a chave fornecida de um objeto do tipo FormData.

> **Nota:** Este método está disponível em [Web Workers](/pt-BR/docs/Web/API/Web_Workers_API).

## Sintaxe

```js
formData.get(nome);
```

### Parâmetros

- `nome`
  - : Um {{domxref("USVString")}} representando o nome da chave que queira retornar.

### Retorno

Um {{domxref("FormDataEntryValue")}} contendo o valor.

## Exemplo

A linha abaixo cria um objeto vazio do tipo FormData.

```js
var formData = new FormData();
```

Se adicionarmos dois valores usuario_nome usando {{domxref("FormData.append")}}:

```js
formData.append('usuario_nome', 'Sabrina');
formData.append('usuario_nome', 'Antônio');
```

A função get() abaixo apenas irá retornar o primeiro valor usuario_nome incluido:

```js
formData.get('usuario_nome'); // Retorna "Sabrina"
```

## Especificações

| Especificação                                                                | Status                               | Comentário |
| ---------------------------------------------------------------------------- | ------------------------------------ | ---------- |
| {{SpecName('XMLHttpRequest','#dom-formdata-get','get()')}} | {{Spec2('XMLHttpRequest')}} |            |

## Compatibilidade com navegadores

{{Compat("api.FormData.get")}}

## Veja também

- {{domxref("XMLHTTPRequest")}}
- [Using XMLHttpRequest](/pt-BR/docs/DOM/XMLHttpRequest/Using_XMLHttpRequest "Using XMLHttpRequest")
- [Using FormData objects](/pt-BR/docs/DOM/XMLHttpRequest/FormData/Using_FormData_Objects "DOM/XMLHttpRequest/FormData/Using_FormData_objects")
- {{HTMLElement("Form")}}
