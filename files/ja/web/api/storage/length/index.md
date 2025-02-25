---
title: Storage.length
slug: Web/API/Storage/length
---
{{APIRef("Web Storage API")}}

{{domxref("Storage")}} インターフェイスの読み取り専用プロパティ `length` は、`Storage` オブジェクトに保存されているデータアイテムの数を表す整数を返します。

## 構文

```
var aLength = storage.length;
```

### 戻り値

整数

## 例

以下の関数はカレントドメインのローカルストレージに 3 個のデータアイテムを追加して、ストレージ内のアイテムの数を返します:

```js
function populateStorage() {
  localStorage.setItem('bgcolor', 'yellow');
  localStorage.setItem('font', 'Helvetica');
  localStorage.setItem('image', 'cats.png');

  localStorage.length; // 3 を返す
}
```

> **Note:** 実際の例として、[Web Storage Demo](https://github.com/mdn/web-storage-demo) をご覧ください。

## 仕様

| 仕様書                                                                           | 策定状況                         | コメント |
| -------------------------------------------------------------------------------- | -------------------------------- | -------- |
| {{SpecName('Web Storage', '#dom-storage-length', 'length')}} | {{Spec2('Web Storage')}} |          |

## ブラウザ実装状況

{{Compat("api.Storage.length")}}

## 関連情報

- [Web Storage API を使用する](/ja/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
