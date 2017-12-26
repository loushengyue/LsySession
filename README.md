# LsySession

```
plugin LsySession
author loushengyue
website http://www.loushengyue.com
version 1.0.2
methods
        .getItem(key[string])
        .getItemsByKeys(keys[array])
        .getArr(prex[string])
        .setItem(key[string],value[string,object])
        .setArr(prex[string],values[array])
        .setList(keys[array],values[array])
        .removeItem(key[string])
        .clearAll()
```



## sessionStorage是什么？
#### sessionStorage是HTML5提供的没有时间限制的数据存储方法。相比cookie，它的存储容量更大，读取更方便。sessionStorage 方法针对一个 session 进行数据存储。当用户关闭浏览器窗口后，数据会被删除。。

由于使用sessionStorage所提供的`setItem()`、`getItem()` 、`removeItem()` 等方法具有局限性（对数组，对象存取不方便），在此，封装了一个插件[LsySession.js](https://github.com/loushengyue/LsySession)，完善了对数组，对象的读取方法。

#### LsySession.js下载：[点击下载](https://github.com/loushengyue/LsySession/archive/master.zip)
#### bower下载命令：
```
$ bower install https://github.com/loushengyue/LsySession.git
```

------
## 使用方法

### `.getItemsByKeys(keys[array])[新增API]`

例如：

```
    var arr = ['apple', 'banana', 'orange', 'grape'];
    var keys = ['fruits_0', 'fruits_3'];
    LsySession.setArr('fruits', arr);
    var list = LsySession.getItemsByKeys(keys);
    console.log(list);//['apple','grape']
```

### `.setItem(key[string],value[string,object])`

例如：

```
var key = 'zhangsan';
var value = 'He is 20 years old boy.';
var objKey = 'lisi';
var objVal = {
    age: 18,
    sex:'man'
};
LsySession.setItem(key, value); //存储字符串
LsySession.setItem(objKey, objVal); //存储对象
```


### `.setArr(prex[string],values[array])`

例如：

```
var prex = 'fruit';
var fruits = ['apple', 'banana', 'orange'];
LsySession.setArr(prex, fruits); // 以变量prex为前缀存储数组fruits
```

### `.setList(keys[array],values[array])`

例如：

```
var keys = ['aa', 'bb', 'cc'];
var values = ['the value of aa', 'the value of bb', 'the value of cc'];
LsySession.setList(keys, values); //以keys为键，以vualue为值进行map映射法存储，注意两个数组的长度必须一致
```

### `.getItem(key[string])`

例如：

```
var key = 'zhangsan';
var student = LsySession.getItem(key);  //通过键key获取sessionStorage所对应的value值
console.log(student); // He is 20 years old boy.
```

### `.getArr(prex[string])`

例如：

```
var prex = 'fruit';
var fruits = LsySession.getArr(prex); //通过键前缀prex获取sessionStorage所对应的系列value值
console.log(fruits); //['apple', 'banana', 'orange']
```

### `.removeItem(key[string])`

例如：

```
var key = 'lisi';
LsySession.removeItem(key); //通过键key删除sessionStorage所对应的value值；
var lisi = LsySession.getItem(key);
console.log(lisi); //undefined
```

### `.clearAll()`

例如：

```
LsySession.clearAll(); // 删除所有的sessionStorage信息
```
