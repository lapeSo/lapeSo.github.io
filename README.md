// FingerJs 注解


`ES6 使用`
```javascript
    const fpPromise = import('https://lapeso.github.io/v3.js')
        .then(FingerprintJS => FingerprintJS.load())
    fpPromise
        .then(fp => fp.get())
        .then(result => {
            console.log('result', result);
            console.table(result)
        })
```

`非 ES6 使用`
```javascript
// 创建一个用于请求脚本的 <script> 元素
    var script = document.createElement('script');
    script.src = 'https://lapeso.github.io/v3_2.js';

    script.onload = function () {
        // 脚本加载完成后，在全局范围内可以访问命名导出
        const FingerLoad = window['FingerFuns']().FingerLoad;
        console.log('load', FingerLoad);
        const fpPromise = FingerLoad;
           fpPromise()
            .then(fp => fp.get())
            .then(result => {
                console.log('result', result);
                console.table(result)
                console.log('============输出指纹结果：', windo['sentData']);
            })
    };

    script.onerror = function () {
        console.error('脚本加载失败.');
    };

    // 将 <script> 元素添加到文档头部
    document.head.appendChild(script);
```