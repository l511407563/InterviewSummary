#### js数据类型
```
    基础数据类型:
        undefined(未定义)
        null(空值)
        Boolean(布尔值)
        Number(数字)
        String(字符串)
        Symbol(es6新增，独一无二的值)
        BigInt(es10新增)

    引用数据类型:
        Obeject(对象):
        对象包含的数据类型有：
            Function(函数)
            Array(数组)
            Date(日期)
            ...等等
    
```

#### js数据类型转换
```
    1. 转换Boolea值，调用Boolean()方法

    2. 转换为数字，调用Number()、parseInt()和parseFloat()方法

    3. 转换为字符串，调用.toString()或者String()方法

    null和undefined没有.toString()方法
```

#### js数据类型判断
```
    1. typeof
        可用于number、boolean、string、function、undefined的判断
        Object、Array、Null都会返回object，所以无法用于判断这些类型

    2. instanceof
        通过判断对象的原型链中是否能找到类型的prototype，所以可以精准判断引用数据类型
        Number、Boolean、String、Array、Function、Object、Undefined、Null

    3. constructor
        通过判断构造函数来判断类型

    4. Object.prototype.toString.call()
        原理和instanceof类似

```

#### js有哪些内置对象
``` 
    常用的：
    NaN、undefined、null
    eval()、parseInt()、parseFloat()
    Object、Function、Boolean、Symbol
    Number、Math、Date
    String、RegExp
    Map、Set
    JSON、
    Promise、Generator、Proxy
    arguments
    
```

#### null和undefined的相同点和区别
```
    1. 二者都是基本数据类型
    2. null表示空对象(但其实它并不是一个对象，000开头的代表对象，null只是一个全零，所以将它错误的判断为 object,这只是一个古老的bug)、
        undefined表示未定义
```

#### 作用域和作用域链
```
    作用域：
        作用域是定义变量的区域，它有一套访问变量的规则，这套规则用来管理浏览器引擎如何在当前作用域以及嵌套的作用域中根据变量(标识符)进行变量查找。

    作用域链：
        作用域链的本质是一个指向变量对象的指针列表，变量对象是一个包含了执行环境中所有变量和函数的对象。
        作用域链的作用是保证对执行环境有权访问的所有变量和函数的有序访问，通过作用域链，我们可以访问到外层环境的变量和函数。
```

#### javascript继承的几种方式
```
    1. 原型继承(对象继承)
        原型继承，不能传参，私有属性和公有属性都继承。
    
    2. 构造函数继承(函数继承)
        构造函数继承, 可以传参, 只继承了私有属性。	

    3. 组合继承
        组合继承, 可以传参, 私有属性和公有属性都继承了，但是私有属性继承了两次，消耗多余资源。

    4. 寄生组合继承
        寄生组合继承, 可以传参, 私有属性和公有属性都继承了，而且都只继承了一次，可以实现多继承。
```

#### this、call、apply、bind
```
    1. 在浏览器中、在全局范围内this指向window对象
    2. 在函数中、this永远指向最后调用它的那个函数
    3. 构造函数中、this指向new出来的那个新对象
    4. call、apply、bind中的this被强绑定在指定的那个对象上
    5. 箭头函数的this指向父作用域
```

#### 原型、原型链 有什么特点
```
    原型是一个对象prototype，里面放着同一个类实例化出来的对象的公共属性和方法
```

#### js获取原型的方法
```
    p.proto
    p.constructor.prototype
    Object.getPrototypeOf(P)
```

#### 闭包
```
    1.  为了在函数外部访问函数内部的变量，上下文信息
    2.  为了防止函数中的上下文不被js垃圾回收机制回收。
```

#### 什么是DOM, 什么是BOM
```
    DOM指的是文档对象模型
        document、里面的元素内容等

    BOM指的是浏览器对象模型
        window、里面location、navigator等
```

#### 三种事件模型是什么？
```
    1. DOM 0级模型
        无事件流的概念，直接定义监听函数，比如click之类的
    
    2. IE事件模型
        一次事件两个过程，事件处理阶段->事件冒泡阶段，通过attachEvent来添加监听函数

    3. DOM2级事件模型
        一次事件共三个过程：事件捕获阶段 -> 事件处理阶段 -> 事件冒泡阶段
        例：使用 addEventListener 给元素dom绑定一个click事件，
            用户点击之后，浏览器会从winodw对象一直找到dom元素(事件捕获阶段)，
            然后会给dom元素绑定click事件(事件处理阶段)，
            接着又从dom元素返回window对象(事件冒泡阶段)
```

#### 事件委托(事件代理)
```
    利用事件冒泡的机制(事件在冒泡过程中会上传到父节点)，将子节点的监听函数定义在父节点上，
    这样可以不必要为每一个字元素都绑定一个监听事件，减少内存上的消耗，
    并且可以实现事件的动态绑定，比如新增了一个子节点，我们不需要单独的为它添加一个监听事件，它所发生的事件会统一交给父元素处理。
```

#### 什么是事件传播
```
    当事件发生在DOM元素上时，该事件并不完全发生在那个元素上。
    事件传播三个阶段：
        1. 捕获阶段：事件从window开始，然后向下到每个元素，直到达到目标元素事件或event.target
            window.addEventListener('事件名', 事件触发回调函数, useCaptrue)
            useCaptrue === true时, 事件在捕获阶段发生

        2. 目标阶段：事件已达到目标元素

        3. 冒泡阶段：事件从目标元素冒泡，然后上升到每个元素，直到到达window
            window.addEventListener('事件名', 事件触发回调函数, useCaptrue)
            useCaptrue === true时, 事件在冒泡阶段发生
```

#### DOM操作(增、删、移动、复制、创建、查找)
```
    1. 创建新节点
    createDocumentFrament() // 创建一个DOM片段
    createElement()         // 创建一个元素节点
    createTextNode()        // 创建一个文本节点

    2. 添加、移除、替换、插入
    appendChild(node)
    removeChild(node)
    replaceChild(new, old)
    insertBefore(new, old)

    3. 查找
    getElementById()
    getElementsByName()
    getElementsByTagName()
    getElementsByClassName()
    querySelector()
    querySelectorAll()

    4. 属性操作
    getAttribute(key)
    setAttribute(key, value)
    hasAttribute(key)
    removeAttribute(key)

```

#### js数组和字符串原生方法
```
    1. 数组
    push()      向数组末尾添加一个或多个元素，并返回新数组的长度
    shift()     删除数组的第一个元素,并返回第一个元素的值        
    unshift()   向数组开头添加一个或多个元素，并返回新数组的长度
    pop()       删除数组的最后一个元素，并返回最后一个元素的值
    splice()    用于插入、删除、或者替换数组的元素
    concat()    用于连接两个或者多个数组
    join()      用于将数组通过指定字符连接成一个字符串
    toStirng()  数组转换字符串  
    reverse()   数组倒序
    slice()     从数组中返回选定的元素
    sort()      将数组从小到大排序(按首字符大小排序，如果需要按照数字大小排序 sort((a, b) => a-b))
    indexOf()   返回元素在数组中的索引，不存在返回-1
    lastIndexOf()   返回元素在数组中最后一次的索引，不存在返回-1
    forEach()   遍历数组，返回值为undefined
    map()       遍历数组，返回一个新的数组
    filter()    过滤数组，返回一个新的数组
    some()      判断数组元素，只要有一个符合条件，返回true，否则返回false
    every()     判断数组元素，全部都符合条件，返回true，否则返回false
    reduce()    数组累加器，从左到右依次返回数组的元素


    2. 字符串
    charAt()    返回指定位置的字符
    charCodeAt()返回指定位置字符的Unicode编码
    concat()    链接字符串
    indexOf()   检索字符串
    match()     找到一个或者多个正则表单式的匹配
    replace()   替换与正则表达式匹配的值
    search()    检索与正则表达式匹配的值
    slice()     提取字符串中的片段
    split()     把字符串分割为字符数组
    toLocaleLowerCase() 把字符串转换为小写
    toLocaleUpperCase() 把字符串转化为大写
    toLowerCase()   把字符串转换为小写
    toUpperCase()   把字符串转换为大写
    substr()    截取子字符串
    substring() 截取子字符串

```

#### ajax是什么
```
    ajax异步通信的方法，通过直接由js脚本向服务器发起http通信，然后根据服务器返回的数据，更新网页的相应部分，而不用刷新整个页面的一种方法。

    创建步骤：
        创建xhr对象 -> 配置ajax请求地址 -> 发送请求 -> 监听请求，接受响应

    var xhr = window.XMLHttpRequest ? new XMLHttpRequest() : new ActiveXObject('Microsoft.XMLHTTP');
    xhr.open('get', 'index.html', true);
    xhr.send(null);
    xhr.onreadystatechange = function (res) {
        if (res.readyState == 4 && res.status == 200 || res.status == 304) {
            console.log(res)
        }
    }
```

#### js延迟加载方式
```
    作用：
    js 的加载、解析和执行会阻塞页面的渲染过程，因此我们希望 js 脚本能够尽可能的延迟加载，提高页面的渲染速度。

    1. 将 js 脚本放在文档的底部，来使 js 脚本尽可能的在最后来加载执行 (常用)
    2. 动态创建 DOM 标签的方式，我们可以对文档的加载事件进行监听，当文档加载完成后再动态的创建 script 标签来引入 js 脚本。(常用)
    3. 给 js 脚本添加 defer属性，这个属性会让脚本的加载与文档的解析同步解析(少用)
    4. 给 js 脚本添加 async属性，这个属性会使脚本异步加载，不会阻塞页面的解析过程(少用)

```

#### 模块化开发
```
    一个模块是实现一个特定功能的一组方法
    1. 由于函数具有独立作用域的特点，最原始的写法是使用函数来作为模块，几个函数作为一个模块，但是这种方式容易造成全局变量的污 染，并且模块间没有联系。
    2. 后面提出了对象写法，通过将函数作为一个对象的方法来实现，这样解决了直接使用函数作为模块的一些缺点，但是这种办法会暴露所 有的所有的模块成员，外部代码可以修改内部属性的值。
    3. 现在最常用的是立即执行函数的写法，通过利用闭包来实现模块私有作用域的建立，同时不会对全局作用域造成污染。

```

#### js 的几种模块规范
```
    1. CommonJS    运行时加载(输出的是一个值的拷贝)
    2. AMD 依赖前置(例：require.js)
    3. CMD 就近依赖(例：sea.js)
    4. ES6 的 import 和 export  编译时加载(输出的是一个值的引用)

    require.js的核心原理：
        通过动态创建 script 脚本来异步引入模块，然后对每个脚本的 load 事件进行监听，如果每个脚本都加载完成了，再调用回调函数。
    
    运行时加载：
        输入时是先加载整个模块，生成一个对象，然后再从这个对象上面读取方法

    编译时加载：
        ES6 模块不是对象，它的对外接口只是一种静态定义，在代码静态解析阶段就会生成

```

#### arguments 的对象是什么
```
    arguments对象是函数中传递的参数值的集合。它是一个类似数组的对象,但它没有数组中的内置方法，如：forEach、reduce、filter和map。
    我们可以使用Array.prototype.slice将arguments对象转换成一个数组
    注意:箭头函数中没有arguments对象。
```

#### 哪些操作会造成内存泄漏？
```
    1.意外的全局变量
        第一种情况是我们由于使用未声明的变量，而意外的创建了一个全局变量，而使这个变量一直留在内存中无法被回收。
    2.被遗忘的计时器或回调函数
        第二种情况是我们设置了setInterval定时器，而忘记取消它，如果循环函数有对外部变量的引用的话，那么这个变量会被一直留在内存中，而无法被回收。
    3.脱离 DOM 的引用
        第三种情况是我们获取一个DOM元素的引用，而后面这个元素被删除，由于我们一直保留了对这个元素的引用，所以它也无法被回收。
    4.闭包
        第四种情况是不合理的使用闭包，从而导致某些变量一直被留在内存当中。
```

#### es6常用新特性
```
    块作用域
    类
    箭头函数
    模板字符串
    加强的对象字面
    对象解构
    Promise
    模块
    Symbol
    代理（proxy）Set
    函数默认参数
    rest 和展开
```

#### var,let和const的区别是什么？
```
    1. var声明的变量会挂载在window上，而let和const声明的变量不会.
    2. var声明变量存在变量提升，let和const不存在变量提升
    3. let和const声明形成块作用域
    4. 同一作用域下let和const不能声明同名变量，而var可以
    5. const声明后不能再修改
```

#### 什么是Proxy
```
    Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，
    因此提供了一种机制，可以对外界的访问进行过滤和改写。Proxy 这个词的原意是代理，用在这里表示由它来“代理”某些操作，可以译为“代理器”。
```

#### 什么是函数式编程
```
    函数式编程是通过编写纯函数，避免共享状态、可变数据、副作用 来构建软件的过程。
    与面向对象编程形成对比，面向对象中应用程序的状态通常与对象中的方法共享和共处。
```