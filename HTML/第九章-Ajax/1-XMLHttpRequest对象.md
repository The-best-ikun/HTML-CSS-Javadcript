`XMLHttpRequest` 是 Web API 提供的一个对象，用于从服务器请求数据，而无需重新加载整个页面。下面是一些 `XMLHttpRequest` 对象的常用属性、事件和方法：

### 常用属性

| 属性名 | 描述 |
| --- | --- |
| `readyState` | 返回请求的状态。它是一个数字，范围从 0 到 4，代表不同的请求状态。0表示未初始化状态，1表示准备发送状态，3表示已发送状态等待响应，4表示完成响应状态 |
| `status` | （只有`readyState`为3或者4时）返回服务器的 HTTP 状态码（例如 200 表示成功，404 表示未找到）。 |
| `responseText` | 只有`readyState`为4时完成响应，将响应作为字符串返回。 |
| `responseXML` | 如果服务器返回的内容是 XML，那么可以使用这个属性将其解析为 XML DOM 对象。 |

### 常用事件

| 事件名 | 描述 |
| --- | --- |
| `onreadystatechange` | 当 `readyState` 属性改变时触发。这是最常用的一个事件，通常用于检查请求是否完成，以及响应是否可用。 |
| `onload` | 当请求成功完成时触发。这个事件在 `readyState` 为 4 且 `status` 为 200 时触发。 |
| `onerror` | 当请求发生错误时触发。 |
| `ontimeout` | 当请求因超时而中断时触发。 |

### 常用方法

| 方法名 | 描述 |
| --- | --- |
| `open(method, url, async, user, password)` | 初始化请求。`method` 是请求类型（如 "GET" 或 "POST"），`url` 是请求的 URL，`async` 表示请求是否异步（通常为 `true`），`user` 和 `password` 是可选的身份验证信息。 |
| `send(data)` | 发送请求。如果请求是 POST 类型，那么 `data` 参数可以包含要发送的数据。对于 GET 请求，通常不需要这个参数。 |
| `setRequestHeader(header, value)` | 在发送请求之前，设置请求头的字段和值。这通常用于设置自定义的 HTTP 头，或者覆盖默认的请求头。当`readyState`为1时，必须调用open方法后再调用，否则会出现异常 |
| `getResponseHeader()` | 检索响应头时，当`readyState`为3时，必须调用open方法后再调用，否则会出现异常 |
| `abort()` | 中断当前请求。并将对象设置为初始化状态 |

下面是一个简单的示例，使用 `XMLHttpRequest` 发送 GET 请求并处理响应：


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XMLHttpRequest 示例</title>
</head>
<body>
    <button onclick="sendRequest()">发送请求</button>
    <div id="response"></div>

    <script>
        function sendRequest() {
            var xhr = new XMLHttpRequest();
            xhr.onreadystatechange = function() {
                if (xhr.readyState === 4 && xhr.status === 200) {
                    document.getElementById('response').textContent = xhr.responseText;
                }
            };
            xhr.open('GET', 'https://api.example.com/data', true);
            xhr.send();
        }
    </script>
</body>
</html>
```
在这个示例中，当用户点击按钮时，会触发 `sendRequest` 函数。这个函数创建一个新的 `XMLHttpRequest` 对象，设置其 `onreadystatechange` 事件处理函数，然后使用 `open` 方法初始化一个 GET 请求，并通过 `send` 方法发送请求。当请求成功完成时，响应文本会显示在页面上的 `<div>` 元素中。