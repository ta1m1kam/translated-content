---
title: IDBCursor.key
slug: Web/API/IDBCursor/key
---

{{APIRef("IndexedDB")}}

**key**是只读属性，返回在游标中的位置。如果游标在范围之外，这个值会被置为 undefined。游标的 key 可以是任何数据类型。

{{AvailableInWorkers}}

## 语法

```
var key = cursor.key;
```

### 值

任意类型

## 示例

在该示例中，我们创建一个事务，检索一个存储对象，然后使用游标遍历所有存储在 object store 中的记录。遍历的过程中，我们把类似（相簿标题，这是我们的键 key），游标的 key 打印出来。

我们可以不根据游标的 key 来选取数据；我们可以抓取所有。还要注意，在循环的每个迭代中，您可以使用 cursor.value.foo 从当前记录下获取数据。完整示例，请看[IDBCursor example](https://github.com/mdn/IDBcursor-example/) ([view example live](http://mdn.github.io/IDBcursor-example/).)

```
function displayData() {
  var transaction = db.transaction(['rushAlbumList'], "readonly");
  var objectStore = transaction.objectStore('rushAlbumList');

  objectStore.openCursor().onsuccess = function(event) {
    var cursor = event.target.result;
    if(cursor) {
      var listItem = document.createElement('li');
      listItem.innerHTML = cursor.value.albumTitle + ', ' + cursor.value.year;
      list.appendChild(listItem);

      console.log(cursor.key);
      cursor.continue();
    } else {
      console.log('Entries all displayed.');
    }
  };
};
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 相关链接

- [Using IndexedDB](/zh-CN/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- Starting transactions: {{domxref("IDBDatabase")}}
- Using transactions: {{domxref("IDBTransaction")}}
- Setting a range of keys: {{domxref("IDBKeyRange")}}
- Retrieving and making changes to your data: {{domxref("IDBObjectStore")}}
- Using cursors: {{domxref("IDBCursor")}}
- Reference example: [To-do Notifications](https://github.com/mdn/to-do-notifications/tree/gh-pages) ([view example live](http://mdn.github.io/to-do-notifications/).)
