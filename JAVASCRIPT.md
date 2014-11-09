# JavaScript 风格参考 #


## 目的 ##


- 一致性
- 语义化
- 可读性
- 模块化


## 变量 ##

- 变量应在作用域的开头声明。
- 禁止重复声明同一变量。
- 使用 `var` 声明变量。
- 使用驼峰式命名变量和函数，如：`functionNamesLikeThis`, `variableNamesLikeThis`, `namespaceNamesLikeThis`, `ClassNamesLikeThis`。
- 私有成员变量、属性和方法命名以下划线开头，如：`var _this`。


## 变量初始化 ##

- 仅在需要时才初始化变量，即：没有必要总是在声明时初始化变量。


## 函数名 ##

- 同样采用驼峰式命名。
- 类名（构造函数名称）以大写字母开头，即大驼峰式。


## 常量 ##

- 常量定义单词全部大写，以下划线（`_`）连接，如：`SOME_CONSTANTS`。
- 使用 `var` 声明常量，不要用 `const` 来声明。


## 分号 ##

- 每一语句的结尾都要添加分号。
- 函数表达式的结尾需要添加分号，函数声明不需要添加分号。

    ```
    var foo = function() {
      return true;
    };  // 需要分号

    function foo() {
      return true;
    }  // 不需要分号
    ```


## 括号 ##

- 对于一元操作符（如 `delete`, `typeof` 和 `void`）或是某些关键字（如 `return`, `throw`, `case`, `new`）后面永远不要使用括号。

## 空行 ##

- 用空行划分一组逻辑相关的代码。


## 等与恒等 ##

- 使用 `===`。


## 单行字符数 ##

- 应尽量控制在 80 个字符以内。


## 作用域 ##

- 明确作用域，函数与变量的定义应控制在最小作用域内。


## 函数 ##

- 函数参数应控制在 3 个以内；3 个以上的参数，应考虑转成对象格式。
- 禁止在代码块中声明函数。

    ```
    // 禁止这样做
    if (x) {
      function foo() {}
    }

    // 也不要这样做，虽然谷歌的风格指南建议
    if (x) {
      var foo = function() {};
    }

    // 应该这样做
    var foo;

    if (x) {
      foo = function() {};
    }

    ```

    > 参见 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/var)，变量提升部分。


## 闭包（Closures） ##

- 可以用，但是要小心内存泄漏。

    ```
    // 内存泄漏：
    function foo(element, a, b) {
      element.onclick = function() { /* uses a and b */ };
    }

    // 应修改为：
    function bar(a, b) {
      return function() { /* uses a and b */ };
    }

    function foo(element, a, b) {
      element.onclick = bar(a, b);
    }
    ```

## 字符串 ##

- 使用单引号。
- 使用 `+` 号连接多行字符串。

    > 使用 `UglifyJS` 压缩脚本，会自动合并多行字符串。


## 基本类型（Primitive Types） ##


- 避免使用 `new` 来实例化基本类型。

    ```
    // 不要这么用
    var b = new Boolean(false);
    var s = new String('string');
    var n = new Number(10);

    // 应该这么用
    var b = false;
    var s = 'string';
    var n = 10;
    ```

- 避免修改内置对象的原型，如（`Object.prototype`、`Array.prototype`）。


## 对象字面量 ##

- 尽量采用对象字面量。

    ```
    // 不要这么用
    var a = new Array('a', 'b');
    var o = new Object();
    var r = new RegExp('[a-z]', 'i');

    // 应该这么用
    var a = ['a', 'b'];
    var o = {};
    var r = /[a-z]/i;
    ```


## 数组 ##

- 不要使用非数字索引的数组。


## 内置对象原型 ##

- 避免修改（增删改）内置对象的原型，如 `Object.prototype`、`Array.prototype`。


## 条件注释 ##

- 禁止使用 IE 的条件注释。

    ```
    var f = function () {
      /*@cc_on if (@_jscript) { return 2* @*/  3; /*@ } @*/
    };
    ```


## eval() ##

- 禁止使用。除非你确切知道输入值。


## with() {} ##

- 禁止使用。


## this ##

- 仅在构造函数、方法、闭包中使用。


## for-in 循环 ##

- 只在 object/map/hash 要遍历键值的时候使用。
- 不要对数组或类数组对象（`arguments`、`HTMLCollection`、`NodeList`）使用。


## delete ##

- 不要使用 `delete ns.foo`，建议使用 `ns.foo = null`，后者效率更高。


## 安全 ##

- 禁止引用具有潜在威胁的站外资源。
- 审查用户输入，防止 XSS 与 CSRF 跨站攻击。


## 异常 ##

- 尽量在可能但不确定出现异常的地方使用 `try-catch(e)` 来抛出异常。


## 标准 ##

- 尽量使用标准方法，比如采用 DOM 原生方法访问节点元素，而不是采用 jQuery 等库或框架封装好的方法。


## 注释 ##

- 添加必要的注释以提高可读性，采用 JSDoc 的格式。
- 对于可能引发歧义的地方，必须添加注释。


## 面向对象 ##

- 尽量用面向对象的思路来写代码，特别是对于逻辑较复杂的功能。


## 工具 ##

- **格式化**

    Node.js：https://github.com/beautify-web/js-beautify

    Sublime Text：https://github.com/victorporof/Sublime-HTMLPrettify


- **代码校验**

    JSHint：http://jshint.com/
